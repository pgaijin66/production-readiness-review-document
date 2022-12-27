## Production Readiness Review (PRR) 



| Feature  |    `[TICKET_NUMBER]: FeatureName`  |
|---|---|
| Authors  |    `author_name` |
|  Start Date |    `YYYY-MM-DD`  |
|  End Date |    `YYYY-MM-DD`  |
|  Status |    `Not Started` / `In Progress` / `Done`  |

### Reviewers

Once review has been completed, corresponding reviewer will check the box next to their name when the review is completed.

#### Required

- [ ] SRE Team: `<reviewer name>`
- [ ] Release Engineering Team: `<reviewer name>`
- [ ] Infosec Team: `<reviewer name>`

#### Optional

- [ ] Database Team: `<reviewer name>`
- [ ] Development Team: `<reviewer name>`


### Architectrure

- [ ] Is there are high level summary of the product feature documented along with usecases? 
- [ ] Are there any architecture diagrams which shows the feature and how it interact with other services / features. Please add following: dependencies ( internal / external , ports, encryption, protocols, ACLs, security policies etc )

### Operational / Scaling risks

- [ ] What might be the potential scaling issues which m
- [ ] List all the dependencies and mention if the dependency is `soft/hard` and how service might be impacted by failure of that dependency ?
- [ ] What is the blast radius if this feature fails ?
- [ ] Are there any SPOF in this feature design and if yes, how are we going to handle that ?
- [ ] How easily can we scale the service ?
- [ ] How are we going to scale the service ( horizontal or vertical ) ?

### SLA / SLO / SLI

- [ ] Is ther a SLA defined for this feature / service ? If yes, then list out all the associated SLI to map to this SLA ?
- [ ] Is SLA degined for the feature / service published publicly ?
- [ ] List out SLOs for the given SLA ?
- [ ] List out SLI which maps to each SLO ?
- [ ] Are all the SLIs measurable ?

#### CI/CD
- [ ] Are we producing any build artifacts ?
- [ ] Are build artifacts version controlled ?
- [ ] Are build artifacts promoted for each environment `dev / stage/ prod` ?
- [ ] Where are build artifacts stored and how long are they retained ?
- [ ] Do we have any CI/CD process ?
- [ ] Does CI process consist of following
    - [ ] linting
    - [ ] unit testing
    - [ ] security testing
    - [ ] code scanning (`sonarqube`)
- [ ] How are build artifacts labelled ? How many copies of build artifact do we store ( `:latest`, `:semVer`) ?
- [ ] How often we intend to release ?
- [ ] Is release process fully automated ? If not, list how automated and non-automated steps.
- [ ] Is there a downtime involved in the release ? If yes, what is the expected downtime ?
- [ ] How long roll back process will take ?
- [ ] What deployment strategy are we using ( `blue-green, canary, A/B, Recreated, Shadow`)

### Database

- [ ] Does this service use any database ?
- [ ] Is database schema verified by Database Team ?
- [ ] Are database queries vetted by Database Team ?
- [ ] What is the expected growth rate ?

### Patching

- [ ] How often is the service patched ?
- [ ] Is patching fully automated ? If not, list of the automated and non automated ones ?
- [ ] Is there a runbook for patching of service, infrastructures and application used by this feature ?
- [ ] Is there an expected downtime during patching ? If yes, how long it is expected ?


### Security and Compliance

##### Design
- [ ] Does service follow company infosec guidelines ?
- [ ] Is service using HTTPS for communication ?
- [ ] How are certificated managed ? Are certificated renewed automatically ?

##### Infrastructure
- [ ] Are there any new resources added that this service uses ?
- [ ] Is IaC(terraform) used to creat infrastructure required for this service ?
    - [ ] If yes, is IaC code checked using secure code analysis tool ?
    - [ ] Where is the state file stored  and who has access to it ?
    - [ ] Is statefile backed up from remote storage ?
    - [ ] Is statefile version controlled ?
    - [ ] Is there any secret in the statefile ?
- [ ] Are we using configuration management tool like ansible
  - [ ] How are variables and secrets passed ?
- [ ] Are there network security policy applied
    - [ ] Do firewall follow the principle of least principle
    - [ ] Is service able to handle and mitigate DDOS attack ?
    - [ ] Is service behind IDS / IPS ?
    - [ ] Is service behind WAF ?

##### Development and Operations

- [ ] Are there are traffic which communites via HTTP ?
- [ ] What version of TLS is used ?
- [ ] Is security scanning done as part of pipeline ?
- [ ] Are all the secrets encrypted at Rest and in Transit ?
- [ ] Is this service adding any form of authentication and authorization ?
- [ ] Does service follow principle of least previlege ?
- [ ] Are there any audit logs for data access ?
- [ ] Is service containerised ?
    - [ ] Are we scanning container for security ? `hadolint`, `kics`, `checkov`

##### Logs

- [ ] Does logs write any secrets data ?
- [ ] Are logs sanitised to hide sensitive customer information ?

##### Compliance
- [ ] Does this service prone to any legal issues ?

### Performance

- [ ] Are there any potential performance impacts to data when this service is enabled ?
- [ ] Are there any throttling applied to the service (eg `rate limiting`?
- [ ] What do customer experience if limit is reached ?
- [ ] Are there return and back-off stratefies for external and internal dependencies ?
- [ ] Will service run optimally if there is a sudden spikes in traffic ?

### Backup and Restore

- [ ] Is service stateful service ? If yes, what is the backend datastore ?
- [ ] Are there any backup process present ?
- [ ] What kind of backups is being done ( full / differential / incremental ) ?
- [ ] Where are Teir {0,1,2,3} backups stored and what are their Recovery Time Objective (RTO) and Recovery Point Objective (RPO) ?
- [ ] Are backups monitored ? If yes, please provide link to the dashboard
- [ ] What is the backup retention period ?
- [ ] Was restore from backup tested ?
- [ ] How frequently backups is being done ?
- [ ] How much data is lost if datastore was restored from last point in time backup ?

### Observability

#### Metrics
- [ ] Is service exposing metrics ?
- [ ] Is service exposing metrics which can be related to SLO ?
- [ ] Do exported metrics allow RED style analysis ?

#### Logs
- [ ] Does service expose logs ?
- [ ] Are logs sent to centralised logging system ?
- [ ] Does logs expose any secrets or PII data ?
- [ ] What logs being exposed in JSON format ?
- [ ] Are logs being sent to centralised observability platform for correlation ?

#### Traces
- [ ] What platform is used to store traces ?
- [ ] Are traces exposing sensitive information ?

#### Alerts
- [ ] Are there alerts that will be triggered when SLO is not met ?
- [ ] Is there any troubleshooting runbooks to handle the alerts ? If yes, please provide link to the document
- [ ] What platform are we using for alerting ?
- [ ] Are alerts configuration version controlled ?
- [ ] Are alerts being routed to correct place ? platform, channel,team ?
- [ ] Are there any alerts to address SLOs ?
- [ ] Are there proper threshold for issuing an official customer notification for an outage related to this service ?
- [ ] Are alerts being triggered when SLI's (SLA) are not met ?

#### Dashboard

- [ ] Are there any dashboard available to visuable service performance ? If yes, provide links
- [ ] Are dashboards version controlled ?
- [ ] Are there RED method-style dashboard for service ?

### Responsibility

- [ ] Which team will take the responsibility of realiability of service once it is in production ?
- [ ] Who is the project owner of the service ?
- [ ] Is there a RACI document created for this service ? If not, explain why not
- [ ] Who are the SME for this service ?

### On call and Incident Response

- [ ] Is someone from the team who build the service be on call ?
- [ ] What is the coverage ?
- [ ] In there follow-the-sun on-call shifts setup ?
- [ ] Is on-call rotation adequately staffed ?
- [ ] Are individuals on call given adequate training on whot o handle specific alerts ?
- [ ] How will be issue be escalated in case of an incident ? Is there any escalation channel for on-call support queries ?
- [ ] Does service has a private / public status page ? 
- [ ] Are there enough runbooks to handle each incident or alerts ?
- [ ] What communication channel are we using for this service ? ( Slack )
- [ ] Is on-call configuration version controlled ?
- [ ] Has there been any post-mortem report done on this service before ? If yes, provide the link

### Testing

- [ ] Did all test cases passed ?
- [ ] Did we do any load tests ? If yes, then what were the breaking points that were validated ?
- [ ] For the component failures theoriesd for this service, were they tested ? If so, include the result of the tests along with failure tests
- [ ] What tests are currently running as part of CI/CD pipeline ?

### Feedbacks

- [ ] Was this chechlist useful ?
- [ ] Is there anything missing on the checklist ?