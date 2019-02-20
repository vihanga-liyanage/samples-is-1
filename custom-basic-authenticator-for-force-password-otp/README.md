## Custom Basic Authenticator for Force Password Reset via OTP.
### Introduction / Use case.
This is a custom basic authenticator which does force password reset via OTP

### Applicable product versions.
Tested in IS 5.3.0

### How to use.
* You can build the source code and get the jar using the command ```mvn clean install```
* Copy the jar file __org.wso2.custom.authenticator.local-1.0.0.jar__ in the target directory to the __<IS_HOME>/repository/components/dropins__ directory.
* Copy the two JSP files in the [accountrecoveryendpoint](/src/main/resources/accountrecoveryendpoint) directory to the __<IS_HOME>/repository/deployment/server/webapps/accountrecoveryendpoint__ directory. You can put your own CSS and customize the pages according to your requirements. 
* Go to your __<IS_HOME>/repository/deployment/server/webapps/authenticationendpoint__ and open the login.jsp file and add the part ``` || localAuthenticatorNames.contains("CustomBasicAuthenticator")``` to the line as shown below. 
Sample login.jsp is available in the [authenticationendpoint](/src/main/resources/authenticationendpoint) folder.
  ``` 
  } else if (localAuthenticatorNames.size() > 0 && (localAuthenticatorNames.contains(BASIC_AUTHENTICATOR) || localAuthenticatorNames.contains("CustomBasicAuthenticator"))) {
  ```

 * Restart the server.
 * In your service provider configurations, instead of __Basic Authenticator__, select the __basicCustom__. You can change this authenticator friendly name according to your preference in your source code.

### Testing the project.
Follow up the documentation [1] to try out the scenario. Please note this will not prompt the second factor login page after password reset.

[1] - https://docs.wso2.com/display/IS530/Forced+Password+Reset#ForcedPasswordReset-PasswordResetviaOTP