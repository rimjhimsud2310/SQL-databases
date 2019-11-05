# SQL Databases Migration Introduction
SQL Databases migration project repo

## Getting Started
Start with the following:
1. Clone repository. If you are getting error message: `SSL certificate problem: unable to get local issuer certificate` for a single repouse this: `git config http.sslVerify false` and for all: `git config --global http.sslVerify false` 
2. Create your own branch via Git
3. Commit your branch and push changes into Azure DevOps
4. Create Pull Request and add relevant colleagues

## Build and Test
TODO: Describe and show how we build our code and run the tests

## SQL Databases Migration Strategies

### Assess

* Discover and assess on-premises databases and infrastructure
* Map dependencies
* Prioritize databases for migration

### Migrate

* Move databases to the cloud
* Use free tools and optional third-party assistance to manage and execute the migration
* Automate migration tasks where appropriate

### Optimize

* Assess and enhance security
* Understand and improve performance
* Manage costs

## Migration Approach

### Rehost

* Which DB’s we can move quickly from on-prem to the cloud?
* Are there DB’s with requirements for IaaS VM?
* Any DB’s which must move with no code changes?

### Refactor

* Redirecting configuration to Azure resources?
* Which DB's can be easily repackaged to exist in Azure?
* Integrate with Azure DevOps pipelines?

### Rearchitect

* A major revision to incorporate new capabilities to work effectively on a cloud platform
* Meet scalability requirements in a cost-effective way
* Apply DevOps practises provided by Azure

### Rebuild

* E.g. moving from MongoDB to Cosmos DB
* Apply [cloud-native technologies](https://docs.microsoft.com/en-gb/dotnet/architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/what-about-cloud-native-applications)

## Design for Data Availability and Resiliency

### Data Availability and Resiliency in Microsoft Azure

* Storage Redundancy  
* [Availability Sets](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/tutorial-availability-sets##targetText=An%20Availability%20Set%20is%20a,storage%20units%2C%20and%20network%20switches.)  
* [Azure Regions Availability Zones](https://docs.microsoft.com/en-us/azure/availability-zones/az-overview##targetText=Availability%20Zones%20is%20a%20high,power%2C%20cooling%2C%20and%20networking.)
* Azure Backup
* [Azure Site Recovery](https://techcommunity.microsoft.com/t5/Azure/ASR-Vs-Azure-backup/m-p/89256)

### Design for Storage Redundancy

* [Locally redundant Storage](https://docs.microsoft.com/en-us/azure/storage/common/storage-introduction##targetText=Locally%2Dredundant%20storage%20(LRS),for%20scenarios%20requiring%20high%20availability.)  
* [Zone redundant Storage](https://docs.microsoft.com/en-us/azure/storage/common/storage-introduction##targetText=Locally%2Dredundant%20storage%20(LRS),for%20scenarios%20requiring%20high%20availability.)  
* [Geo-redundant Storage](https://docs.microsoft.com/en-us/azure/storage/common/storage-introduction##targetText=Locally%2Dredundant%20storage%20(LRS),for%20scenarios%20requiring%20high%20availability.)  
* [Read access Geo-redundant Storage](https://docs.microsoft.com/en-us/azure/storage/common/storage-introduction##targetText=Locally%2Dredundant%20storage%20(LRS),for%20scenarios%20requiring%20high%20availability.)  
* [Geo-zone-redundant storage (GZRS) (preview)](https://docs.microsoft.com/en-us/azure/storage/common/storage-introduction##targetText=Locally%2Dredundant%20storage%20(LRS),for%20scenarios%20requiring%20high%20availability.)  

### Design for Availability Sets (IaaS focus)

### Design for Regions and Availability Zones (PaaS focus)

* Cost-effective region pair selection

### Design for Backup and Site Recovery

* Backup an Azure SQL Database -> `Azure SQL Databases are automatically backed up at no charge`

## Determine a Data Transfer Strategy

### Explore VPNs and **ExpressRoute**

* What kind of throughput is required?
* What type of VPN gateway is required? Are additional VM’s required?
* Site-to-site vs **ExpressRoute**?

### Explore AzCopy

* Command-line utility for copying data to/from MS Azure Blob, File, and Table Storage

### Explore Azure Database Migration Service

* Service for DB migrations to Azure
* Migrations are resilient and include self-healing features

### Explore Other Transfer Solutions

* Azure CLI, PowerShell, etc.

## SQL Migratation Design to Azure preparation checklist

* Identify business drivers  
* Identify migration goals  
* Determine migration approach  
* Select a partner where appropriate (BJSS, Microsoft)  
* Design deployment and select services  
* Determine required Azure subscriptions  
* Determine governance practices (link with RBAC project)  
* Design and configure networking (**ExpressRoute** vs VPN)  
* Design and integrate security (link with RBAC project)  
* Design and configure resilience and disaster recovery practises

## Notes, questions, issues

* New Azure Subscriptions to be build using the new Cloud Ops Model
* Balancing between IaaS vs PaaS
* Efficient RBAC control needed
* Use of Azure Policy
* On-prem VMWare focus
* What level of refactoring is needed? (touching the Web config and changing the connection strings, etc.?)
* Azure Subscription access for the team is needed.
* Which specific subscriptions we are aiming to use for the assessment tool?
* Do we need to create a new subscription for the actual SQL migration project (BJSS COM link)?
* Data team connectivity issues need to be sorted.
* Which jump-box/jump-server we are using for the project?
* How can we sort issues of accessibility to Azure-based DB’s via local DB Management tools?
* What are the exact issues Forrest and Rob faced when POC’ing this project?
* Is there a plan to user Azure Policy
* Are we aiming to user Datadog for Monitoring and Alerts implementation?
* Can we proceed with the set up of DevTest Labs?
* Who are our main stakelholders?

## Useful Links

* [Azure Policy service (link with RBAC)](https://docs.microsoft.com/en-gb/azure/governance/policy/overview)#
* [Azure Migrate POC PBI](https://vbl-core.visualstudio.com/Core%20Engineering/_workitems/edit/51853)
* [Azure Database Migration Service Overview ](https://docs.microsoft.com/en-us/azure/dms/dms-overview)
* [Azure Database Migration Service Pre-Requisites](https://docs.microsoft.com/en-us/azure/dms/pre-reqs)
* [Azure data migration Assistant](https://docs.microsoft.com/en-us/sql/dma/dma-overview?view=sql-server-ver15)
* [Microsoft Cloud Adoption Framework for Azure ](https://docs.microsoft.com/en-gb/azure/cloud-adoption-framework/migrate/index)
* [Overview of prerequisites for using the Azure Database Migration Service](https://docs.microsoft.com/en-us/azure/dms/pre-reqs)
* [Migrate SQL Server to a single database or pooled database in Azure SQL Database online using DMS](https://docs.microsoft.com/en-us/azure/dms/tutorial-sql-server-azure-sql-online)
* [Migrate SQL Server to a single database or pooled database in Azure SQL Database online using DMS](https://docs.microsoft.com/en-us/azure/dms/tutorial-sql-server-azure-sql-online)
* [Azure Migrate: Server Assessment](https://go.microsoft.com/fwlink/?linkid=2055798)
* [Azure Migrate: Server Migration](https://go.microsoft.com/fwlink/?linkid=2055935)
* [Azure Migrate: Database Assessment](https://go.microsoft.com/fwlink/?linkid=2090457)
* [Azure Migrate: Database Migration](https://go.microsoft.com/fwlink/?linkid=2090356)
* [Azure Database Migration Services](https://docs.microsoft.com/en-us/azure/dms/)
* [Data Migration Assistant](https://docs.microsoft.com/en-us/sql/dma/dma-overview?view=sql-server-ver15)
* [Azure Migrate documentation](https://docs.microsoft.com/en-us/azure/migrate/)
* [Azure Migrate hub](https://portal.azure.com/?feature.customPortal=false#blade/Microsoft_Azure_Migrate/AmhResourceMenuBlade/overview)
* [Cloud migration in the Cloud Adoption Framework](https://docs.microsoft.com/en-gb/azure/cloud-adoption-framework/migrate/index)
* [Azure Migrate support matrix](https://docs.microsoft.com/en-gb/azure/migrate/migrate-support-matrix)
* [Azure Migrate appliance](https://docs.microsoft.com/en-gb/azure/migrate/migrate-appliance)
* [Perform a SQL Server migration assessment with Data Migration Assistant](https://docs.microsoft.com/en-gb/sql/dma/dma-assesssqlonprem?view=sql-server-2017)