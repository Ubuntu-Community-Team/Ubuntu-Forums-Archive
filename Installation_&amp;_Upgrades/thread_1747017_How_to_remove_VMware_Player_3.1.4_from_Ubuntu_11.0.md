---
title: "How to remove VMware Player 3.1.4 from Ubuntu 11.04?"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Uewd on 2011-05-02
I installed VMware Player 3.1.4 on my PC which I downloaded from [here]("https://www.vmware.com/tryvmware/p/activate.php?p=player&lp=1&a=DOWNLOAD_FILE&baseurl=https://download2.vmware.com/software/wkst/&filename=VMware-Player-3.1.4-385536.i386.bundle"). I installed it by this method:
[B]cd (location)
eg: cd /media/storage/downloads/[/B]

then

[B]sudo sh filename.bundle
eg: sudo sh VMware-Player-3.1.4-385536.i386.bundle[/B]
________________________________________________________________
**Now I want to remove it, but how?**
Please help.
Thanks.
Uewd.

---

### Post by lechien73 on 2011-05-02
Do you have the vmware-installer in /usr/bin? If so, then:

```
vmware-installer -u vmware-player
```

should remove it :)

---

### Post by Uewd on 2011-05-02
> **lechien73 said:**
> Do you have the vmware-installer in /usr/bin? If so, then:

```
vmware-installer -u vmware-player
```should remove it :)
[B]
HOW TO REMOVE VMWARE PLAYER 3.1.4[/B]:

1. Press **Alt+F2** on the keyboard to open the **Run Application **dialog and paste this command in the box: **gksu /usr/bin/x-terminal-emulator** 

[B]Note:
The above command opens terminal as root. If you didn't run terminal as root, you will face an error during the second step. 

[/B]2. Now run this command in terminal (Thanks for the user **"lechien73"** for providing this trick): **vmware-installer -u vmware-player**

3. Continue with the uninstallation process.

Hope this helps.
Thanks.
Uewd.

---

### Post by oiram on 2011-07-04
tested with VMware Player 3.1.3 and works as well

---

### Post by sdino on 2011-07-30
Hi,

Had tried the command but unable to uninstall vmware player - basically, it requires to shut down all VM's to continue the command. 

root@ubuntu:/home/slimer# vmware-installer -l
Product Name           Product Version     
====================== ====================
vmware-player          3.1.4.385536        
root@ubuntu:/home/slimer# vmware-installer -u vmware-player

Error:
The VMware installer could not shut down all running virtual machines.  if you have ace vm's open, please shut them down or suspend them now ans  press "RETRY" to continue.

Thanks

---

### Post by sdino on 2011-07-30
Hi,

Please ignore my last comment as problem solved. 

> Had unstalled VMware server 2.0.2 by issue this command:

sudo vmware-uninstall.pl

> Then unstall VMware player by running this command:

root@ubuntu:/home/slimer# vmware-installer -l
Product Name           Product Version     
====================== ====================
vmware-player          3.1.4.385536        
root@ubuntu:/home/slimer# vmware-installer -u vmware-player
root@ubuntu:/home/slimer# vmware-installer -l
bash: /usr/bin/vmware-installer: No such file or directory
root@ubuntu:/home/slimer# 

Thanks

---

