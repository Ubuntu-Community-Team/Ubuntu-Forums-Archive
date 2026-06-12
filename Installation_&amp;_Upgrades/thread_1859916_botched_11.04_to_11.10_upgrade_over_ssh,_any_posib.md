---
title: "botched 11.04 to 11.10 upgrade over ssh, any posible sloution?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by vizzzion on 2011-10-14
I know it was risky and unnecessary, but i recently attempted to upgrade from 11.04 to 11.10 via ssh, without running screen, or having backed up any of my some 300gb or so of files.
As if that wasn't stupid enough, I got bored watching the upgrade, and fell asleep pretty soon after I started it, thinking it couldn't do much harm just going through the install automatically.
Long story short, I'm not sure what went awry during the installation, but I can now only access my server via the rescue console provided by my host. I have no physical access to the server itself, though it is a dedicated server and I do Not share it with anyone else. SSH is basically the only way I can change settings/files. KVM is possible, but only as a last resort.
Also, if you thought it couldn't get more embarrassing, I even have certifications in Unix based OS's. So arrogance was probably the root cause I guess.
My question is basically, does anyone have any ideas as to how to fix this without a format/reinstall, or a complete backup and clean OS install?

---

### Post by sikander3786 on 2011-10-14
Possibly executing a few commands from the Recovery's root shell prompt might help but you obviously need direct access to the machine. Why are you reluctant to use the KVM?

If you gain access to the root shell, here is what you might want to try:

```
dhclient eth0
```

To bring up the interface.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg --configure -a
sudo apt-get install -f
```

Please post any errors encountered during the process.

---

### Post by grim2 on 2011-10-14
I'm posting here because I can't find another thread that more closely matches my situation.
I was upgrading my server from 11.04 to 11.10.  I was not doing via ssh, but with physical access.
I'm not a certified Unix anything, but am a certified idiot.  And impatient.  

The upgrade got stuck after Generating Environments (I think).  It sat for more than 1 hour with no progress.  So...I reset the box.

Now when it boots it says something about ELF being shorter than normal and then takes me to the GRUB RECOVERY> prompt.

What should I do now?

---

### Post by sikander3786 on 2011-10-14
> **grim2 said:**
> I'm posting here because I can't find another thread that more closely matches my situation.
I was upgrading my server from 11.04 to 11.10.  I was not doing via ssh, but with physical access.
I'm not a certified Unix anything, but am a certified idiot.  And impatient.  

The upgrade got stuck after Generating Environments (I think).  It sat for more than 1 hour with no progress.  So...I reset the box.

Now when it boots it says something about ELF being shorter than normal and then takes me to the GRUB RECOVERY> prompt.

What should I do now?
Well, if you are stuck in the recovery prompt, I don't think there are many options left except to Chroot your install and try to repair it.

Is the server that important? I mean if possible, doing a fresh install would be an easier, more convenient option. After hours of Chrooting, there is no guarantee that it can be repaired.

Tell us if you still want to try Chrooting so I can help you to the extent I can.

---

### Post by vizzzion on 2011-10-14
> **sikander3786 said:**
> Possibly executing a few commands from the Recovery's root shell prompt might help but you obviously need direct access to the machine. Why are you reluctant to use the KVM?
My host charges for KVM use, and to be honest, the time I'd need to either backup my data, then reinstall/reformat later, or to mess around with a bunch of files I think might be causing the problem, would probably be more than the cost of the actual server itself. 

> **sikander3786 said:**
> If you gain access to the root shell, here is what you might want to try:

```
client eth0
```To bring up the interface.

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg --configure -a
sudo apt-get install -f
```Please post any errors encountered during the process.
using the recovery console and chrooting into the main partition, I get errors on almost every process run, regardless of what command i use to execute them.

---

### Post by sikander3786 on 2011-10-14
Can you please list any of those errors?

---

### Post by grim2 on 2011-10-14
> **sikander3786 said:**
> Well, if you are stuck in the recovery prompt, I don't think there are many options left except to Chroot your install and try to repair it.

Is the server that important? I mean if possible, doing a fresh install would be an easier, more convenient option. After hours of Chrooting, there is no guarantee that it can be repaired.

Tell us if you still want to try Chrooting so I can help you to the extent I can.

Thanks.  I'd like to try a Chroot later tonight.  The server isn't super important.  I would assume I could access the files with a bootable stick and put them on an external drive.  Right?

---

### Post by grim2 on 2011-10-15
> **grim2 said:**
> Thanks.  I'd like to try a Chroot later tonight.  The server isn't super important.  I would assume I could access the files with a bootable stick and put them on an external drive.  Right?

Update - I confirmed my boot disk and data disks are different.  I thought they were,but couldn't remember.

Second, I was able to get a bootable usb created and have the 11.10 server on the stick.  I was planning on using the rescue tool.  Is there a reason not to?  Which menu option should I choose?  Reinstall GRUB?

Thanks.

---

### Post by vizzzion on 2011-10-15
> **sikander3786 said:**
> Can you please list any of those errors?

Originally I was only mounting the root directory, and getting nothing but lengthy printouts of errors when trying to run commands, So I mounted basically every system directory along with the root, to make a sandbox-like environment I guess, then chrooted into that.

```
dhclient eth0
``` returned no response 

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install -f
``` all ran without error and listed no updates

```
sudo dpkg --configure -a
```returned no response

I've also tried purging and reinstalling grub, and reinstalling the linux kernel, but still no luck.

---

### Post by grim2 on 2011-10-15
> **grim2 said:**
> Update - I confirmed my boot disk and data disks are different.  I thought they were,but couldn't remember.

Second, I was able to get a bootable usb created and have the 11.10 server on the stick.  I was planning on using the rescue tool.  Is there a reason not to?  Which menu option should I choose?  Reinstall GRUB?

Thanks.

Ok, so "rescued a broken system" and was able to get through dpkg --configure -a, apt-get update and upgrade.  The system appeared to make it further than it did during the online upgrade.  However, I still get the error "ELF smaller than expected" and then end up at the grub rescue> prompt.

Any help on what to do next?

Thanks in advance.
g2

---

### Post by sikander3786 on 2011-10-16
> **grim2 said:**
> Ok, so "rescued a broken system" and was able to get through dpkg --configure -a, apt-get update and upgrade.  The system appeared to make it further than it did during the online upgrade.  However, I still get the error "ELF smaller than expected" and then end up at the grub rescue> prompt.

Any help on what to do next?

Thanks in advance.
g2
Just searched the web for the error you are getting as I wasn't already familiar with it. Turns out that re-installing Grub might solve the problem. Here is what you need to do for re-installing it:

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

I am not sure which method is the most convenient for you, you've to decide yourself.

---

### Post by grim2 on 2011-10-16
> **sikander3786 said:**
> Just searched the web for the error you are getting as I wasn't already familiar with it. Turns out that re-installing Grub might solve the problem. Here is what you need to do for re-installing it:

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

I am not sure which method is the most convenient for you, you've to decide yourself.
thanks  i reinstalled grum from the usb stick and now all is well  
g2

---

