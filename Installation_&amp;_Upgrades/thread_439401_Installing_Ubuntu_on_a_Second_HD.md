---
title: "Installing Ubuntu on a Second HD"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by a.ranic on 2007-05-10
I'm new to all of this so my question may sound rather naive.  I want to install Ubuntu onto a secondary HD in my computer.  My primary HD has Windows XP and I would like to keep that as the default OS.  I've read many posts about this but I'm still not sure if they apply in my situation.  In a nutshell, will the Fawn installer catch this and provide me with a boot menu automatically or do I have to change some settings?  Thank you in advance for your help.

---

### Post by ohgod on 2007-05-10
The installer should handle this pretty much automatically.  It'll ask you if you want to use all the unused space on your 2nd disk.  And it'll install the boot loader on your first disk and setup a menu option to boot into XP (make sure you choose the 'install grub to mbr' option).  It's pretty easy...I doubt you'll have any trouble.

---

### Post by Shinobi326 on 2007-05-10
This is the setup I chose to do and in short to answer your question is YES the regular Live CD GUI installer WILL be able to install Feisty on a secondary HD.

I would recommend popping in the Feisty CD, click "install" which actually boots you into Ubuntu as a Live CD.  From there I forget which menu navigation takes you to install Ubuntu but once you do it should detect your second hard drive and then ask you how you want to install it.  Just be careful you select the option where it's installing on your second hard drive and not your XP drive (which is NOT the default selection).  It's obvious to say but make sure you do have a good backup/image of your XP HD in case something gets botched.

After it goes though the motions the install will install the GRUB bootloader that will come up right after the BIOS post.  It will default to go into Ubuntu instead of your XP partition but this is something you can change later if you want (search forums).

Without knowing anything about Linux or Ubuntu I was able to pull this off successfully without any hitches but again just make sure your XP drive is backed up.

---

### Post by a.ranic on 2007-05-10
Thank you for the advice.  I'll post if I run into any problems.

---

### Post by a.ranic on 2007-05-10
The install onto the second HD went off with nary a hitch.  I just have to search to find out how to change the default OS option to XP and not Ubuntu (my wife gets freaked out when I change things).  Thanks again.

---

### Post by confused57 on 2007-05-10
> **a.ranic said:**
> The install onto the second HD went off with nary a hitch.  I just have to search to find out how to change the default OS option to XP and not Ubuntu (my wife gets freaked out when I change things).  Thanks again.
See the section on changing the default OS booted:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Shinobi326 on 2007-05-12
A.Ranic,

You and I must have a wife from the same gene pool because mine also flipped out when the Grub came up and Windows XP was not the default partition.  I searched through forums to figure it out but the link above seems good too.

All I did for mine is not worry about change the position of any of the entries.  All I did was change the default to 5 (I think) instead of 1 and change the timer to 5 seconds.  This way I just tell my wife "Don't worry the computer will automagically go into WindowsXP if you don't touch anything"  She was very happy with that and all is right with the world again  :lolflag:

---

### Post by maddee on 2007-05-25
My wife and kids freaked also! I told them to get used to Ubuntu because windows sucks and Linux Rocks!

---

