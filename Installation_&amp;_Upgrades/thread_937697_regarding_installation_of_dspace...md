---
title: "regarding installation of dspace.."
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by shredder12 on 2008-10-04
I am working on a project of creating a digital library and for that i need a library management software..so i opted for dspace..but i m having trouble with its installtion..
I downloaded the dspace-1.5.1-release and read the installation documentation provided with the package...i m done with all of the prerequisites.( there could be an error in them but as far as i m concerned i have completed them..) Now i m having trouble with running the ```
mvn package
``` command.. when i executed the command in the --dspace-1.5.1-release/dspace-- directory.. it showed the following errors..
```
[INFO] Scanning for projects...
[INFO] Reactor build order: 
[INFO]   DSpace Addon Modules
[INFO]   DSpace XML-UI (Manakin) :: Web Application
[INFO]   DSpace LNI :: Web Application
[INFO]   DSpace OAI :: Web Application
[INFO]   DSpace JSP-UI :: Web Application
[INFO]   DSpace SWORD :: Web Application
[INFO]   DSpace Assembly and Configuration
[INFO] ------------------------------------------------------------------------
[INFO] Building DSpace Addon Modules
[INFO]    task-segment: [package]
[INFO] ------------------------------------------------------------------------
[INFO] artifact org.apache.maven.plugins:maven-site-plugin: checking for updates from central
[WARNING] repository metadata for: 'artifact org.apache.maven.plugins:maven-site-plugin' could not be retrieved from repository: central due to an error: Error transferring file
[INFO] Repository 'central' will be blacklisted
[INFO] ------------------------------------------------------------------------
[ERROR] BUILD ERROR
[INFO] ------------------------------------------------------------------------
[INFO] The plugin 'org.apache.maven.plugins:maven-site-plugin' does not exist or no valid version could be found
[INFO] ------------------------------------------------------------------------
[INFO] For more information, run Maven with the -e switch
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 3 minutes 9 seconds
[INFO] Finished at: Sat Oct 04 14:52:06 IST 2008
[INFO] Final Memory: 2M/4M
[INFO] ------------------------------------------------------------------------

```
what am i doing wrong..i downloaded maven using synaptic..and so it was installed automatically. do i have to configure its internet settings because we use a proxy server in my college..
Please reply..
any help in this regard will be appreciable..
thankyou..

---

### Post by shredder12 on 2008-10-05
reply please...

---

### Post by spauldingsmails on 2008-10-22
try running maven as root;

```
sudo mvn package
```

You'll also need to run ant as sudo;

```
sudo ant fresh_install
```

---

