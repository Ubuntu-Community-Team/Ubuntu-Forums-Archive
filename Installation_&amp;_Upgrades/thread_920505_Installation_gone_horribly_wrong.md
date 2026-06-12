---
title: "Installation gone horribly wrong"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by Seadog01 on 2008-09-15
Hey all,

I just got a new laptop (Asus m50vm-b1), and got stupid.  I tried to install Hardy on it alongside vista, but did so without reading anything on the subject.  Ubuntu worked fine, but it didn't recognize my windows installation.  So instead of doing the smart thing and looking at these forums, I decided to reformat again and reinstall windows clean (I have a recovery disc...).  Then I'd find out the proper way of installing Ubuntu.

This plan worked well up until the computer tried to restart.  I then got a message that GRUB had had an error, a "System Error 22".  The computer then refuses to do anything else.  So now I have neither windows nor ubuntu to work with.  I thought that the reformatting thing would've taken care of GRUB too, but I see I was mistaken...

This is causing me some considerable consternation, as I'm no expert on any of this! (clearly...)  I have no data that I need to save anywhere (it being a new new computer), so pretty much anything you people can suggest would be amazing!  I hope I haven't caused more or less irreversible damage.  At least the BIOS still works...

Thanks!

Colin

---

### Post by Steve1961 on 2008-09-15
> **Seadog01 said:**
> Hey all,

I just got a new laptop (Asus m50vm-b1), and got stupid.  I tried to install Hardy on it alongside vista, but did so without reading anything on the subject.  Ubuntu worked fine, but it didn't recognize my windows installation.  So instead of doing the smart thing and looking at these forums, I decided to reformat again and reinstall windows clean (I have a recovery disc...).  Then I'd find out the proper way of installing Ubuntu.

This plan worked well up until the computer tried to restart.  I then got a message that GRUB had had an error, a "System Error 22".  The computer then refuses to do anything else.  So now I have neither windows nor ubuntu to work with.  I thought that the reformatting thing would've taken care of GRUB too, but I see I was mistaken...

This is causing me some considerable consternation, as I'm no expert on any of this! (clearly...)  I have no data that I need to save anywhere (it being a new new computer), so pretty much anything you people can suggest would be amazing!  I hope I haven't caused more or less irreversible damage.  At least the BIOS still works...

Thanks!

Colin

As you only have a recovery disk you may need to download the vista recovery disk to repair the vista bootloader:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Boot from the disk and choose the option to repair the vista installation

---

### Post by Elfy on 2008-09-15
IF you are going to reinstall ubuntu then the grub should be sorted out then and the error will go. If no then you will as said need to repair the bootloader.

---

