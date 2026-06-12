---
title: "How to make install CD for your current configuration"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by acidsolution on 2008-02-18
How do i make a install cd from mine current configuration .
Suppose i have installed programs and all other stuff i have cunstomized mine desktop according to mine wish. Now if i want to transfer same configuration to other computer what should i do ?
Is there any way to create install cd/DVD for the current configuration so that when i install from the made cd automatically i get that configuration in other computer

---

### Post by acidsolution on 2008-02-18
I desperately need it . any help ........................

---

### Post by superhac007 on 2008-02-18
google: remastersys

---

### Post by acidsolution on 2008-02-19
i guess remastersys is only for making live cd but i want install ?
Does remastersys works for install cd ?

---

### Post by superhac007 on 2008-02-19
> **acidsolution said:**
> i guess remastersys is only for making live cd but i want install ?
Does remastersys works for install cd ?

Yep... Right from the site.  Use the backup option.

"Some notes about the backup option

   You can log into the livecd/dvd with any valid user that was on the system on the hard drive but it is recommended to log into the first one created during the initial installation as that is the user that can sudo.  When you come to install this back to a hard drive, the user setup portion of ubiquity (the install program) is just a placeholder other than the system name.  The username and password set here will not be used but must be created in order to continue with the installation.  Part of the reason for this is that your users are already created so you don't need to create them again,  but more importantly because user setup is an integral part of the install program and cannot be removed or bypassed easily.  If you were using proprietary video drivers like the nvidia or ati ones, you will need to reinstall them.  The Ubuntu livecd scripts prevent these from running properly but reinstalling them after installation will make them work again."

---

### Post by acidsolution on 2008-02-20
i couldnot get you properly 
could you please describe it 
I also tried by taking backup of the whole system using tar comand excepting mnt media and boot and dev folder and than dump it on the fresh installed ubuntu computer.
I was able to get all the program installed and working fine 
But  I :( lost mine all GUI things its givin error 
Failed to start Xserver but i can use shell things fine 

Any concrete process as remastersys to make Install CD/DVD so that we just put cd and install and please could you describe it elaborately ..
Thanks in advance

---

### Post by acidsolution on 2008-02-25
ohk done as i explained i took the backup
but i was ubanle to get desktop this was done by reconfiguration of xorg.conf file 
now i was able to transfer completely the config of one computer to another 
thanks for all your replies

---

