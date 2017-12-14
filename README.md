# nginx-swift-proxy-openshift
Openshift nginx swift proxy

## Purpose
This project is an nginx reverse proxy implementation for OpenStack Swift containers backed by an Isilon Swift instance.

## Acknowledgements
The S2I implementation was derived from the examples in https://github.com/sclorg/nginx-container.

## Building and deploying in OpenShift
### Using container nginx-112-rhel7
```
oc new-app nginx-112-rhel7~https://github.com/spsandiford/nginx-swift-proxy-openshift.git --context-dir=nginx-112-rhel7
```

### Environment varibles for OpenShift Deployment
| Environment Variable     | Meaning                                                                             | Example                                  |
|--------------------------|-------------------------------------------------------------------------------------|------------------------------------------|
| ISILON_ROOT_URL          | The root URL for the Isilon Swift proxy implementation                              | https://swift.company.com:8083           |
| OBJECT_STORE_DIR         | The root folder for all requests that should pass through to the Isilon Swift proxy | my_objects                               |
| ISILON_OBJECT_STORE_DIR  | The Isilon swift url prefix, usually /v1/AUTH_<account>/<container>                 | /v1/AUTH_myaccount/mycontainer           |
| ISILON_SWIFT_X_AUTH_USER | Header value for X-Auth-User, usually <account>:<username>                          | myaccount:myuser                         |
| ISILON_SWIFT_X_AUTH_KEY  | Header value for X-Auth-Key                                                         | my_account_password                      |
| ISILON_AUTH_URL          | Isilon Swift proxy authentication API URL                                           | https://swift.company.com:8083/auth/v1.0 |


