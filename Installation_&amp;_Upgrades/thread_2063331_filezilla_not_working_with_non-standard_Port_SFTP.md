---
title: "filezilla not working with non-standard Port SFTP"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by hiflyer on 2012-09-26
I have setup SFTP and have working from the command line thru a fios router on port 22 (the default). Server is on 12.04. laptop is on 11.04
filezilla works just fine both on the lan side and bouncing out of the lan to the DYNDNS site to access the sshd server. When I make the change on the server of Port=2222, then the command line sftp still works bouncing out to DYNDNS but filezilla (configured for the port 2222) in the site manager for the server site states 
Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server"

seems the FIOS router is setup correctly as the command line works.
Filezilla should be working as I only changed the port

Is there something missing here in the configuration of filezilla.

---

