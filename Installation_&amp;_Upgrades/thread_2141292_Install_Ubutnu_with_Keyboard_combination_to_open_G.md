---
title: "Install Ubutnu with Keyboard combination to open Grub"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by RedCoder on 2013-05-02
Hi everybody,

First time here.

My Question :
   
     Is there a way I can install Ubuntu(actually I'll be installing **BackTrack** but I think its all the same thing because backtrack is based of **Ubuntu**) such that the GRUB screen doesn't come up every time I start up my computer? So, to start up Ubuntu, I'll have to press a key(e.g F5, or a combination ALT + F5 etc) that will boot it up. I'm tired of choosing options during startup yet I only use Ubuntu a few times - I'll use it more when I join college in a months time.

   I'll be installing it side by side with Windows 7. So I'll partition my computer(250 GB hard drive) like this : 
   Local Disk C - 40 GB, 
   Local Disk D - 80 GB, 
   Local Disk E - 80 Gb, 
   Ubuntu Partition - 40 GB

Any way I can do that?

---

### Post by TheFu on 2013-05-02
You can shorten the grub timeout in the settings before the default OS is automatically booted.. Don't make it too short, is my only warning. Google found this: [http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/) which should explain how.

Isn't Backtrack out of date?  It was replaced by Kali, right?

---

### Post by RedCoder on 2013-05-02
Is there a way I can change the default OS to be loaded by the Grub? Currently it loads Backtrack if I don't press any key for 10 seconds. I would like it to load Windows(hard disk OS) by default if no key is pressed.

---

### Post by RedCoder on 2013-05-02
By the way Is there any way I can install it(Ubuntu/Backtrack/Kali  Linux) in an NTFS partition or FAT32? Windows cannot mount any volume in  an EXT series format.

---

### Post by TheFu on 2013-05-02
> **RedCoder said:**
> Is there a way I can change the default OS to be loaded by the Grub? Currently it loads Backtrack if I don't press any key for 10 seconds. I would like it to load Windows(hard disk OS) by default if no key is pressed.

Google found this: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
BTW. I searched for "grub2 timeout ubuntu"  I'm adding this to help you improve your google-fu.

---

### Post by TheFu on 2013-05-02
> **RedCoder said:**
> By the way Is there any way I can install it(Ubuntu/Backtrack/Kali  Linux) in an NTFS partition or FAT32? Windows cannot mount any volume in  an EXT series format.

Linux OSes need a Linux file system. NTFS and FAT32 are NOT Linux file systems. They do not support UNIX file permissions and certain key features that are required for a UNIX/Linux OS to function.    You should complain to Microsoft that their OS is lacking compatibility features.  OTOH, almost every Linux can read/write both NTFS and FAT-whatever formats.

Is there **any way** - yes, but I don't have the skills to do it. Basically, you end up running a blob that acts like a Linux file system. the files will still not be available from Windows to be read.

**Wubi** used to be an easier way to accomplish this, but wubi has been removed from current Ubuntu releases due to problems.  Personally, I've never used Wubi and never thought it was a good idea.  OTOH, for people new to Ubuntu, it was a viable alternative that seemed very popular.  Of course, these new users would come for help here, but not explain they'd done a non-standard Wubi install. If you do find a way to use wubi, be certain that you** always, always, always include that information **when asking for help anywhere.

A fairly full featured Linux install doesn't take much storage. I've run with 15G the last 5 yrs.  Clearly, I keep media files on network storage, which is available to all OSes thanks to NFS and Samba.  There are many forum posts about this specific topic here. Search a little to learn more.

---

### Post by RedCoder on 2013-05-02
Thanks mate. 

I should really work on my Google-Fu. Hehe

---

