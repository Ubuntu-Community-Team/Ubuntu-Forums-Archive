---
title: "Ubuntu 12.4 lost"
date: 2013-12-25
forum: Installation &amp; Upgrades
---

### Post by derwalroszsagt on 2013-12-25
I recently had my hard drive failed on a windows 7 machine.  The hard drive was partitioned with 3 drives. Ubuntu was installed on drive New Volume (F).  Since that change of hard drive I am unable to boot Ubuntu.  On booting it get the windows7 boot screen showing windows and Ubuntu but when I select Ubuntu I get the error message of "cannot find \Ubuntu\winboot\wubildr.mbr".  Is there a procedure for repairing this or must I reinstall Ubuntu.  Not having used the forum for a while I was not able to find a previous post explaining how to work around the problem.  Any help is appreciated. 
derwalrosz

---

### Post by hakuna_matata on 2013-12-25
Maybe it is necessary to change drive letter at Ubuntu menu entry in Windows boot manager. For that you can use [EasyBCD]("http://neosmart.net/EasyBCD/") or [bcdedit]("http://technet.microsoft.com/en-us/library/cc709667%28v=WS.10%29.aspx")

---

### Post by deadflowr on 2013-12-25
It seems your running wubi.
In that case, you need to fix the windows drive.

[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

---

### Post by hakuna_matata on 2013-12-25
> **deadflowr said:**
> 
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)
IMHO a problem with /ubuntu/disks/root.disk file could be an additional problem, but not the reason for the error message above. It is an error message of the Windows boot manager. That boot manager needs only wubildr.mbr. wubildr.mbr needs wubildr and later root.disk will be used.

---

### Post by deadflowr on 2013-12-25
I clicked the wrong link
Here
[https://wiki.ubuntu.com/WubiGuide#Troubleshooting](https://wiki.ubuntu.com/WubiGuide#Troubleshooting)
or go up on the other link.

---

### Post by derwalroszsagt on 2013-12-27
Thank you to all that replied.  As one of you mentioned I think the reason it doesn't work is that the drive is not in the address in this case F.  I tried bcdedit but is will not allow me to change the file with the error that permission is not granted even though I am the administrator.  I tried to change the permissions but it won't allow that either.  Anyone have an idea of how to correct this.  I also tried to reinstall but I will need to reformat the drive to make it work.  Don't really want to do that.  Any ideas are really appreciated.

---

### Post by hakuna_matata on 2013-12-28
> I tried bcdedit but is will not allow me to change the file with the  error that permission is not granted even though I am the administrator.
I know this Windows problems, too. e.g. [here]("http://www.windowslinuxosx.com/q/answers-force-cmd-exe-to-run-as-admin-88491.html") is a solution.

---

### Post by derwalroszsagt on 2013-12-28
hakuna,
thanks for the reply.  After much searching I found that  by right clicking and running as administrator it works ok.  In some ways Windows is such a pain-in-the-ass.  Now I need to learn how to modify the file by using bcdedit.  easybcd isn't very helpful.

---

### Post by derwalroszsagt on 2013-12-28
Again thanks to all of you that replied.  I finally got it working by editing bcd.  Thanks again.  Now I need to find out how to install 12.04 from the iso without having a cd or dvd on an old box.

---

### Post by hakuna_matata on 2013-12-28
```
bcdedit /set {*####*} device partition=*F:*
```
where #### is ID of Ubuntu boot loader entry. Replace #### by your value.

---

