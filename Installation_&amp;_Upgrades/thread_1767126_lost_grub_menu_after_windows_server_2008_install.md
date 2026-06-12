---
title: "lost grub menu after windows server 2008 install"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by priyamvaidya on 2011-05-25
hi

I was getting ubuntu grub menu, and i was able to **login to windows xp, windows server 2008 and ubuntu 10.10**. 

Recently there was some problem with windows server 2008 and i had to reinstall it, once i did that i **lost my grub menu.**  now i am getting plain windows menu with option of login into windows xp and windows 2008. 

So how can i restore the grub menu, so that i can login into all the three os from one point.

thanks

---

### Post by Pumalite on 2011-05-25
Reinstall Grub

---

### Post by priyamvaidya on 2011-05-25
@ [Pumalite]("http://ubuntuforums.org/member.php?u=263028")

can you give me the exact steps to do this.   i tried this with booting ubuntu with pendrive, but it did not work 

i followed the steps from [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) 

the only difference is that, instead of ubuntu live disc, i used usb pendrive to boot

the above steps did not worked


thanks

---

### Post by ksprasad on 2011-05-25
Hi,
 
Did you give the correct device name?
Exactly what error did you get?
 
Regards,
ksprasad

---

### Post by cbowman57 on 2011-05-25
> **priyamvaidya said:**
> hi

I was getting ubuntu grub menu, and i was able to **login to windows xp, windows server 2008 and ubuntu 10.10**. 

Recently there was some problem with windows server 2008 and i had to reinstall it, once i did that i **lost my grub menu.**  now i am getting plain windows menu with option of login into windows xp and windows 2008. 

So how can i restore the grub menu, so that i can login into all the three os from one point.

thanks

[Download Rescatux]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Recovery Using the Unofficial Rescatux") and make restoring grub simple.

---

### Post by priyamvaidya on 2011-05-25
@[ksprasad]("http://ubuntuforums.org/member.php?u=835842")

all the steps were completed fully..  it did not gave any error.  after the completion, when i restarted the machine, the grub menu was not there.  it was just simple windows menu 

thanks

---

### Post by ksprasad on 2011-05-25
ok can you please post the output of 'sudo fdisk -l' here?
 
Regards,
ksprasad

---

### Post by priyamvaidya on 2011-05-26
Dear Ksprasad


i can no longer login to ubuntu as i have lost grub menu and windows boot.ini file does not show that


i had installed windows 2008 server on my other partition (after i installed ubuntu), which have replaced grub.

help is appreciated

---

### Post by priyamvaidya on 2011-05-26
Dear Ksprasad


sorry, i forget to mentioned one thing here.  i can use the usb stick to boot the computer in ubuntu and will post the fdisk-l output here

---

### Post by priyamvaidya on 2011-05-26
@Ksprasad

please find my fdisk-l output here 

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       60800   385977659+   f  W95 Ext'd (LBA)
/dev/sda5           12749       25496   102398278+  83  Linux
/dev/sda6           25497       38244   102398278+   7  HPFS/NTFS
/dev/sda7           38245       50992   102398278+   7  HPFS/NTFS
/dev/sda8           50993       60800    78782728+   7  HPFS/NTFS

my linux is on sda5 and my windows server 2008  is on sda6, xp is on sda1

---

### Post by priyamvaidya on 2011-06-20
[Rescatux]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Recovery%20Using%20the%20Unofficial%20Rescatux")

had solved my problem

thanks

---

