---
title: "Previous installion of vmware dectected?? HELP please!"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by dangqt85 on 2007-05-21
I am trying to install vmware server onto ubuntu feisty and i get this Previous installation of vmware dected error on terminal, i installed VMware player before and i uninstalled it with automatix, can anyone help me solve this problem?

toai@toai-desktop:~$ cd /home/toai/vmware/vmware
toai@toai-desktop:~/vmware/vmware$ cd vmware-server-distrib
toai@toai-desktop:~/vmware/vmware/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.


Thank you, i am a linux noobie T_T

---

### Post by wthanna on 2007-05-21
Uninstall vmware player that you installed originally using Automatix through the Automatix uninstall program.  

Remove the vmware folder that is located in the /etc folder.

Install vmware server using synaptic. 
(Synaptic will also remove some files related to vmware player that were not removed by Automatix during the uninstall process, when it installs vmware server.)

**This has worked successfully on two machines that I had previously installed vmware player on, using Automatix.
 Edit: This is on Ubuntu 7.04 (Feisty Fawn)

---

### Post by bankg3 on 2007-05-21
I have had this same issue and I erased the folder in /etc and that allowed me to reinstall vmware

---

### Post by juanvicfer on 2007-05-28
I was having the same issue and after removing the /etc/vmware directory everything worked fine.

Thanks :D

---

### Post by steve909 on 2007-06-02
Hello,
I've been installing and re-installing VMWare server on 7.04. I can uninstall ok, but I've had various problems with various installs, so went back to the tar.gz install from vmwares site.
I used the any-any patch to get it to install.

Now, however, I can only run it from the command line (no icon anywhere) and I always get the following message in the terminal:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

If I try to close the terminal, vmware closes as well so I have to leave it open (no command prompt shows) in order to use vmware.

Can anyone help me with this please?

If I install from the 'canonical main' repo, I can't power on any VM's. VM is a nightmare in 7.04.
Thanks

---

