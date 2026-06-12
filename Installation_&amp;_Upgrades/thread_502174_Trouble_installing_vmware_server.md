---
title: "Trouble installing vmware server"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by heckler40 on 2007-07-16
I am trying to install vmware server on Feisty 7.04.  I keep getting the following errors:

"If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before proceeding."

"E: /var/cache/apt/archives/vmware-server_1.0.3-1_i386.deb: subprocess pre-installation script returned error exit status 1"

I have looked for the vmware-uninstall.pl everywhere I can think of.  It is not in the usr/bin where I thought it should be.

I tried installing it with Automatix and Synaptic package manager.

I would really like to get this up and running, any help would be greatly appreciated.

---

### Post by jim_p on 2007-07-16
Have you tried ```
sudo vmware-uninstall.pl
``` from the terminal?
Also, have you tried installing it from the .deb file provided from the vmware site?

---

### Post by heckler40 on 2007-07-16
Ran "sudo vmware-uninstall.pl" from terminal and got the following error:

"sudo: vmware-uninstall.pl: command not found"

I am not seeing the .deb file you speak of.  I have downloaded the rpm and the .tar.gz files from the site.  Could you post a link to the .deb?

Thanks for the fast response!

---

### Post by heckler40 on 2007-07-17
**Bump**

Anyone?  I would really like to get this working.

---

### Post by scapalexis888 on 2007-07-20
you can try removing the vmware folder in /etc.

I had the same problem and solved it like that.

hope this helps!

---

### Post by klyick on 2007-07-24
This worked perfectly for me on ubuntu Server. Thanks!

---

