# SonarQube Chart Changelog
All changes to this chart will be documented in this file.

## [2025.4.0]
* Update Chart's version to 2025.4.0
* Upgrade nginx subchart to 4.12.3
* Support Kubernetes v1.33
* Added validation to ensure that either the `applicationNodes.jwtSecret` or `applicationNodes.jwtExistingSecret` value is set

## [2025.3.0]
* Update Chart's version to 2025.3.0
* Normalizes the extension for all templates
* Remove example about non-system sonar.properties
* Fix change-admin-password hook when using special characters
* Upgrade SonarQube Server to 2025.3.0

## [2025.2.0]
* Update Chart's version to 2025.2.0
* Update ingress-nginx subchart to 4.12.1
* Upgrade SonarQube Server to 2025.2.0

## [2025.1.0]
* Update Chart's version to 2025.1.0
* Upgrade SonarQube Server to 2025.1.0
* Update ingress-nginx subchart to 4.11.3
* Support Kubernetes v1.32
* Remove the default passcode provided with `monitoringPasscode`
* Support Openshift v4.17

## [10.8.1]
* Update Chart's version to 10.8.1
* Upgrade SonarQube Server to 10.8.1

## [10.8.0]
* Update Chart's version to 10.8.0
* Upgrade SonarQube Server to 10.8.0
* Support the installation of the Oracle JDBC Driver
* Support Kubernetes v1.31
* Update the Chart's icon with the SonarQube Server logo
* Fix ENV variables not fetched when using extraConfig.configmaps
* Support Gateway on different namespace in HTTPRoute
* Change `ingress.ingressClassName` default, set it to `nginx` if `nginx.enabled` or `ingress-nginx.enabled`
* Ensure that ConfigMap resources are not created for `initFS` and `initSysctl` if not needed
* Ensure the Pod will stop at `init` stage if init_sysctl.sh failed to modify kernel parameters
* Replace the example images in initContainers, initSysctl and initFs from `busybox:1.36` to `ubuntu:24.04`, which are commented out by default
* Make the `automountServiceAccountToken` configurable with `serviceAccount.automountToken` in PodSpec
* Deprecate `ApplicationNodes` in favor of `applicationNodes`, fixing naming convention typo
* Replace helm top level '$' by '.' when not necessary
* Deprecate `elasticsearch.bootstrapchecks`, `sonarqubeFolder`, `jdbcOverwrite.jdbcPassword` and `terminationGracePeriodSeconds`
* Deprecate `account`, `curlContainerImage`, `adminJobAnnotations`
* Deprecate `logging.jsonOutput` in favor of the ENV var SONAR_LOG_JSONOUTPUT or the sonar.properties's sonar.log.jsonOutput

## [10.7.0]
* Update Chart's version to 10.7.0
* Upgrade SonarQube to 10.7.0
* Support Kubernetes v1.30
* Upgrade ingress-nginx dependency to 4.10.1
* Deprecate `jdbcOverwrite.enable` in favor of `jdbcOverwrite.enabled`
* Enable the setup of ReadOnlyRootFilesystem in the security contexts
* Support basic chart installation on Openshift
* Support Openshift Route
* Fix networkPolicy.additionalPolicys typo
* Support install-plugin and prometheusExporter proxy variables in secret
* Support GatewayAPI HttpRoute
* Support Openshift SCCv2 by default when Openshift.enabled=true
* Deprecate Openshift.createSCC
* Support the TLS communication between App and Search nodes
* Support additional CA Certificate as ConfigMap instead of Secret only
* Changed default value for caCerts.image
* Document the upgrade process when autoscaling is enabled
* Fix openshift change-admin-password-hook Job SecurityContext failure
* Support SONAR_OPENSHIFT telemetry env_var
* Update helm chart repo path in sources
* Support IS_HELM_AUTOSCALING_ENABLED telemetry env_var and rename SONAR_OPENSHIFT to IS_HELM_OPENSHIFT_ENABLED
* Remove socketTimeout from jdbcOverwrite.jdbcUrl's default value
* Refactor Route to be subparameter of OpenShift
* Make OpenShift.createSCC false by default
* Support ApplicationNodes.extraVolumes and ApplicationNodes.extraVolumeMounts
* Ensure kubernetes.io/version label is smaller than 63 chars

## [10.6.0]
* Upgrade SonarQube to 10.6.0
* Update Chart's version to 10.6.0
* Fix the env-var templating when sourcing from secrets
* Fix the postgresql chart's repository link
* Calibrate probes' initialDelaySeconds
* Define HorizontalPodAutoscaler for the app deployment
* Add support for overriding liveness/readiness probe logic in the app nodes
* Add ApplicationNodes.affinity, ApplicationNodes.tolerations, searchNodes.affinity, searchNode.tolerations, ApplicationNodes.nodeSelector, searchNodes.nodeSelector
* Define affinity, tolerations, and nodeSelector parameters for App and Search nodes

## [10.5.0]
* Upgrade SonarQube to 10.5.0
* Update Chart's version to 10.5.0
* Update nginx-ingress-controller dependency to version 4.9.1
* Fix the ingress.ingressClassName not being evaluated
* Fix searchNodes.securityContext and ApplicationNodes.securityContext not being evaluated
* Fix duplicated `ApplicationNodes.resources` parameters in the README
* Add `gcp_marketplace` value, implementing compatibility with google cloud marketplace app
* Set `automountServiceAccountToken` to false in pod's specifications
* Update default `ApplicationNodes.resources` and `searchNodes.resources` to values matching better default Xmx and Xms of the SonarQube processes.
* Make `ephemeral-storage` resource's limits and requests configurable for the SonarQube App and Search containers
* Set memory and cpu limits for the test container
* Fix `searchAuthentication` probes failure by enforcing basic auth on wget
* Remove outdated doc about persistency
* Deprecate nginx.enabled in favor of ingress-nginx.enabled, to match with subchart config block
* Deprecate `ApplicationNodes.prometheusMonitoring.podMonitor.namespace`
* Instantiate `monitoring-web` and `monitoring-ce` endpoints when the `ApplicationNodes.prometheusExporter` is enabled
* Take `sonarWebContext` into account for the `PodMonitor` path
* Fix duplicated env_var in Pods causing deployment issue (`SONAR_WEB_CONTEXT`,`SONAR_WEB_JAVAOPTS`,`SONAR_CE_JAVAOPTS`)

## [10.4.0]
* Upgrade SonarQube to 10.4.0
* Update Chart's version to 10.4.0
* Improve the description of deprecated `ApplicationNodes.jvmOpts` and `ApplicationNodes.jvmCeOpts` values
* Run the initSysctl init-container as root to prevent 'permission denied' issues
* Add revisionHistoryLimit configuration for SonarQube application Deployment ReplicaSets
* Introduce `ApplicationNodes.podDisruptionBudget` and `searchNodes.podDisruptionBudget` and deprecate `ApplicationNodes.podDistributionBudget` and `searchNodes.podDistributionBudget`.
* Update the security contexts to use root as group ID
* Fix empty ingress annotations in values

## [10.3.0]
* Upgrade SonarQube to 10.3.0
* Update Chart's version to 10.3.0
* Update default images to the latest versions
* Remove the nginx-proxy-body annotation when nginx is disabled
* Enable post-upgrade in the change-admin-password hook
* Separate annotations and labels for app and search pods
* Update default ContainerSecurityContext, InitContainerSecurityContext and postgresql.securityContext to match restricted podSecurityStandard
* Update initFs default securityContext to match baseline podSecurityStandard
* Add securityContext feature to change admin password Job
* Remove unneeded if condition for Sysctl initContainer
* Update default image of initContainers to sonarqube image, allowing for faster loading time and less external images needed
* Support Kubernetes v1.28
* Avoid duplicate SONAR_WEB_SYSTEMPASSCODE secrets
* Deprecate embedded PostgreSQL
* Update nginx-ingress-controller dependency to version 4.8.3, please carefully read the changelog of this new major version.
* Remove duplicated 'proxy-body-size' from ingress annotation.

## [10.2.0]
* Update SonarQube to 10.2.0
* Update Chart's version to 10.2.0
* Update curl image to 8.2.0
* `ApplicationNodes.readinessProbe.sonarWebContext`, `ApplicationNodes.startupProbe.sonarWebContext`, `ApplicationNodes.livenessProbe.sonarWebContext` and `account.sonarWebContext` are deprecated, please use `sonarWebContext` at the value top level.
* Set the minimum values for PodDisruptionBudget
* Updates ingress-nginx dependency to 4.7.1

## [10.1.0]
* Update SonarQube to 10.1.0
* Support Kubernetes v1.27 while dropping v1.23
* Changed default test process to wget, using sonarqube image as default
* Fix wrong condition between initFs and concat-properties
* Update Chart's version to 10.1.0
* Fix liveness probe for SonarQube Application to detect when a failure occurs.

## [10.0.0]
* Update SonarQube to 10.0.0
* Helm chart versioning will now follow the SonarQube product versioning

## [8.3.1]
* Make `jvmOpts` and `jvmCeOpts` not override env vars and sonar properties

## [8.3.0]
* Add helm-chart-sonarqube as chart sources

## [8.2.3]
* Fixed unsupported wget parameter `--proxy off` with `--no-proxy`

## [8.2.2]
* Fix install_plugins.sh not deleting previously installed plugins

## [8.2.1]
* Clarify doc for custom cacert secret

## [8.2.0]
* Add a configurable Prometheus PodMonitor resource
* Refactor Prometheus exporter's documentation and bump to version 0.17.2

## [8.1.0]
* Allow setting priorityClassName for StatefulSets

## [8.0.2]
* Fix the volume mounts for the init-fs container

## [8.0.1]
* Adds timeoutSeconds parameter to probes

## [8.0.0]
* Update SonarQube logo
* Bootstrap chart version 8.x.x dedicated to the future SonarQube 10.0

## [7.0.0]
* Update SonarQube to 9.9.0
* Bootstrap chart version 7.x.x dedicated to SonarQube 9.9 LTS

## [6.0.2]
* Update the list of supported kubernetes versions

## [6.0.1]
* Set a new default (maximum) allowed size of the client request body on the ingress

## [6.0.0]
* Update SonarQube to 9.8.0

## [5.2.1]
* Update the postgresql chart's repository

## [5.2.0]
* Refactor Pdb and Ingress to be compatible with static compatibitly test and 1.19 minimum requirement
* Fix indent in Service.yaml annotations

## [5.1.2]
* Updated SonarQube to 9.7.1

## [5.1.1]
* Refactor templating of ConfigMap for sonar.properties
* Fix the bug where sonarSecretKey was not applied without sonar.properties set

## [5.1.0]
* Fix the installation of plugins using the standard folder `extensions/plugins` instead of `extensions/downloads` and `lib/common`
* Remove `ApplicationNodes.plugins.lib` and other small edits in the documentation

## [5.0.0]
* Updated SonarQube to 9.7.0

## [4.3.1]
* Fix the right-dash curly brace issue with the additional network policy parameter

## [4.3.0]
* Allow `tests.image` to be configured and update README accordingly.
* Allow `tests.initContainers.image` to be configured and update README accordingly.

## [4.2.1]
* Fix wrong image's tag in application nodes

## [4.2.0]
* Add support for monitoringPasscode passed as a secret and removal of livenessprobe httpheader defined in clear text

## [4.1.0]
* Add the possibility of using a secret for customizing the admin password
* Remove unreachable condition and fix the right values for sonarProperties and sonarSecretProperties
* Bump apiVersion to v2
* Add documentation for ApplicationNodes.jwtSecret
* Add documentation for ingress tls

## [4.0.6]
* Updated SonarQube to 9.6.1

## [4.0.0]
* Updated SonarQube to 9.6.0

## [3.0.1]
* Add documentation for ingress annotations

## [3.0.0]
* updated SonarQube to 9.5.0

## [2.0.4]
* Fix issue with additional network policy

## [2.0.3]
* Add automount service account token flag

## [2.0.2]
* Add documentation to setup web context via environment variable

## [2.0.1]
* Fix for issue (#215)[https://github.com/SonarSource/helm-chart-sonarqube/issues/215], adding tolerations and affinity to change password hooks

## [2.0.0]
* updated SonarQube to 9.4.0

## [1.0.7]
* Specify location of .netrc file when downloading plugins that require auth

## [1.0.6]
* Fixed properties scope for app deployment and search sts

## [1.0.5]
* Specify service account name in change admin password hook

## [1.0.4]
* secure admin password in k8s secret

## [1.0.3]
* changed description of dependency postgresql chart

## [1.0.2]
* changed links to get a better overview of sources

## [1.0.1]
* Updated all instances of the caCerts enabled check

## [1.0.0]
* updated SonarQube to 9.3.0
* officially support SonarQube DCE

## [0.6.5]
* name of elasticsearch keystore password secret is now aligned with the rest of the chart

## [0.6.4]
* properties are now correctly set

## [0.6.3]
* `livenessProbe.failureThreshold` was never rendered

## [0.6.2]
* added missing logic for `caCerts.enabled`

## [0.6.1]
* reverted liveness prove change
## [0.5.0]
* added support for additional sidecar container

## [0.4.0]
* added possibility to define the ingress pathType
* added network policies
* added possibility to define ressources for the change admin password hook
* default permissions for prometheus injector now align with pod fs permissions
* updated dependencies
* admin hook now honors web context
* added pod distribution budget

## [0.3.0]
* added support for multiple image pull secrets
  * added `searchNodes.image.pullSecrets`
  * added `ApplicationNodes.image.pullSecrets`
* deprecated support for singular image pull secret
  * deprecated `searchNodes.image.pullSecret`
  * deprecated `ApplicationNodes.image.pullSecret`
* fixed missing image pull secret in admin hook job

## [0.2.5]
* updated SonarQube to 9.2.4

## [0.2.4]
* updated SonarQube to 9.2.3

## [0.2.3]
* updated SonarQube to 9.2.2

## [0.2.2]
* replaced hardcoded port's values

## [0.2.1]
* updated SonarQube to 9.2.1

## [0.2.0]
* updated SonarQube to 9.2.0

## [0.1.7]
* added possibility to secure connection in between search nodes
* added link to community support forum

## [0.1.6]
* fixed wrong scc user reference if name was explicitly set

## [0.1.5]
* fixed serviceaccount logic

## [0.1.4]
* fixed wrong limits reference in sonarqube-application deployment

## [0.1.3]
* Homoginized Description of the Helm Chart
* fixed wrong link in README.md

## [0.1.2]
* changed external database connection logic

## [0.1.1]
* added option to use external secret as jwtSecret
* removed initSysctl from application pods

## [0.1.0]
* fixed pvc template for search nodes
* added flag to handle hazelcast on k8s
* adapted probes for search nodes
* made search nodes start up in parallel
* search nodes no longer wait for the database connection
* added new headless services for search and app

## [0.0.1]
* separated search and app configuration
* added new search service
