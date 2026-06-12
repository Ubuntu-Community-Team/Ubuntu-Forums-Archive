---
title: "I'm not understanding the update fix"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by wmb on 2010-12-01
I'm following this guide : [http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

copying c:\ubuntu\winboot\wubildr to  c:\wubildr  didn't work...there wasn't even a c:\wubildr file.

To edit grub.cfg:
Boot a live CD (check)
_______________________
identify your windows partition that contains the root.disk (this example assumes /dev/sd**a1**) 
I typed
```
 sudo find / -name 'root.disk'
```what came back was:
```
/media/A49ACC319ACBFDB4/ubuntu/disks/root.disk
```I'm pretty sure this is where my problem is...can someone let me know what I'm doing wrong?

in my dev directory, I have sda, sda1, and sda2.  I just don't know how to find out which one should be mounted.  I tried copy & pasting the commands below but I got an error at sudo mount /dev/sd**a1** /media/win.  "fuse: mount failed: Device or resource busy
_______________________


 and then edit grub.cfg as follows:

```

sudo mkdir /media/win 
sudo mount /dev/sd**a1** /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```

---

### Post by Rubi1200 on 2010-12-01
Hi,
if you are on the LiveCD, run the boot info script linked at the bottom of my post and get the results back here please.

---

### Post by wmb on 2010-12-01
I've been downloading it for around 15 minutes.  Some of the parts hit an incredible 2KB/sec.  I hope it's due to running off of the dvd drive.

---

### Post by Rubi1200 on 2010-12-01
Odd! It should only take a few seconds at most, even from a LiveCD. 

Give it another few minutes and if nothing post back here and I will upload and attach it for you in my next post.

---

### Post by wmb on 2010-12-01
> **Rubi1200 said:**
> Odd! It should only take a few seconds at most, even from a LiveCD. 

Give it another few minutes and if nothing post back here and I will upload and attach it for you in my next post.

Nevermind...

I installed Ubuntu on a separate partition - we'll call this U2, because I originally installed it onto windows - we'll call this U1.

Now, grub comes up.  I have the ability to choose Ubuntu(U2) or Windows.  If I choose Windows, I have the Windows Loader crap, and I can choose Windows or Ubuntu (U1).  Then I can choose Ubuntu(U1) or Windows.  And it works.

LOL...I'm reformatting after I'm done.

---

### Post by Rubi1200 on 2010-12-01
Yes, please let me know what happens.

To be honest, a full install to the drive is preferred over a Wubi install.

I am attaching the script for you in any event (in zip format because of forum size limitations)

And, you are more than welcome :)

---

### Post by wmb on 2010-12-01
Updated the previous post...still, thanks a bunch.

---

