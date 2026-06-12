---
title: "Can not install ubuntu 7.04"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by aliinal on 2007-05-19
Hello,

I'm new to Ubuntu. I just want to try it on a virtual machine.
I'm an AMD Athlon 64 X2 4200+ user. My host operating system is Windows XP x64 edition.
I try to install Ubuntu on a new pc created under Microsoft Virtual PC. I've checked for minimum requirements before creating new machine.
When I start virtual machine, everything seems to be fine. I see Ubuntu logo and the menu. I choose "start or install...." I wait a while then the attached message screen appear and then nothing happens...

Do you have any ideas?

Best regards,
ali

---

### Post by aliinal on 2007-05-22
If this makes sense, I've realized that not every installation attempt fail at the same point. On every try, system is locked at different points.

Anyone knows if there is a limitation installing Ubuntu on a Virtual PC??

Thanks,
ali

---

### Post by stefaan.dutry on 2007-05-22
you might want to try to put the option **ACPI=off** before selecting anything.

Personaly i don't understand why you would want to run it with virtual pc and not just boot from the CD, but maybe that's just me.  I don't think you'll be able to install when using virtual PC.  But it should start up though.

I hope this was of any help to you.

---

### Post by rjklindsay on 2007-05-22
I cant seem to install Ubuntu 7.04 on my Samsung X20 Centrino laptop.
I first install XP on a 40GB partition, and then boot off the Ubuntu Live CD, and click install.
In the Ubuntu installer, I manually create a 1025MB SWAP partion, and a 15GB Ext3 partition.

Time and again, the instllation hangs at 94%, on "Update-GRUB", which leaves the Harddrive in an unbootable state. When I try to reboot, I just get a GRUB> command line prompt.

 However, I CAN get XP to boot, by using the OSL2000 bootloader, or BootitNG, 
but neither of these is able to boot the Ubuntu partition.

Was the Ubuntu 7.04 intaller ever tested before it was released?
It seems that the bug in GRUB is interrupting the installation before the partition is bootable, but I cant see any way of skipping the bootloader step in the installation.
Is there any workaround for this problem, or is Ubuntu just not ready for release yet?

---

### Post by rjklindsay on 2007-05-24
After many many attempts at installing Ubuntu, I have finally found the cause of the problem:
It seems Ubuntu does not like my external USB harddrive. (NTFS)

When my USB drive is plugged in, I have the following problems:

 When booting from the Live CD, Ubuntu stops halfway, hangs for about 15mins, shows a few errors, and then continues to boot up.
 When installing Ubuntu, I get a few errors at 15%, and the installation hangs at 94% (update-Grub), leaving the pc in a unbootable state. 
However, if I unplug the USB drive, the liveCD boots up, and installs just fine.
The installed Ubuntu also boots up fine as long as I dont have the USB drive plugged in.
if I DO have the USB drive plugged in, the bootup hangs when the orange line reaches about 15%.

This is probably not the right place to report this Bug, but since I'm new to Ubuntu, I was hoping someone could point me in the right direction?

---

### Post by stefaan.dutry on 2007-05-24
I'm glad you found the problem.

Unfortunately i won't be able to direct you to where to post this bug.

Just to know, can you use your external HDD if you plug it in after the startup?  (I'd like to know cause i have an external HDD myself, haven't even tried if it worked on ubuntu) and I'm not at home right now.  I'll test that startup with the HDD plugged in myself later.

---

### Post by Topsiho on 2007-05-24
Try  this to report a bug:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

You'll have to register first, and find out whether this bug has been reported already. If it is you can add your comments to reinforce that report.

Topsiho

---

### Post by aliinal on 2007-05-25
Hi,

Glad to hear that you've solved your problem. Unfortunately no way out for me :( 
Tried many things. But nothing changed. still can not make it install. Install hangs somewhere during installation.

I don't know how to put that "acpi=off" thing on work. As I said this is my first Ubuntu and/or Linux installation and I do not understand the language of this thing :)

If anyone have an idea, or anyone give me a clue, I'll be really really happy...

Best regards,
ali

---

### Post by rillip on 2007-05-25
When you're at the screen where you can chose start or install, check disk, etc.  there's an option there, don't remember the exact text right off hand, that says something like "edit boot command" or something like that.  I think you hit e. Anyway, you do that and you'll get a really nasty looking string.  Just type "acpi=off" in the big long string, before you get to where it starts having things preceede by the - symbol. You'll see other stuff in a similar form, of something=something with no particular format or extra charachters if you're typing it in the right place.

Hope that helps.

---

### Post by Topsiho on 2007-05-25
If I remember it well you'll have to hit F6 when booting the Live CD and then get get a menu in which you can edit the boot string.

Topsiho

---

