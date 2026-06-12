---
title: "Distributed File System Installation?"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by firefly2442 on 2006-08-01
Hello.  I was just curious if it is possible to install Ubuntu on multiple machines and have some sort of distributed file system?  Is there an option for this in the server install possibly?  Ideally, I think it would be really nice to be able to login and have one huge mounted partition that looks like one partition but is really multiple machines across an ethernet network.  Is this possible?  Thanks in advance! :)

---

### Post by n8gray on 2006-08-03
You might want to take a look at the [OpenAFS]("http://www.openafs.org/") project, since that filesystem sounds like it matches what you want.  However, I don't think Ubuntu (or any Linux distro for that matter) is going to make it particularly easy for you to set it up.  I think you have to have Kerberos working first, which I know nothing about.

Good luck,
-n8

---

