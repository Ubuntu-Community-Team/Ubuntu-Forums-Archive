---
title: "unknown filesystem"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by Eugeneslipped on 2010-09-20
Hey there.

I've had a look around and found a few threads with people getting 
"error: unknown filesystem.
Grub rescue>"
error, but following those threads didn't seem to help - most likely because of a completely stupid mistake I made.

(Note: I had Windows 7 already installed, Ubuntu was on a separate partition)

I had installed Ubuntu Netbook 10.04 onto my EeePC this morning and it was going swimmingly until it had an error while downloading and installing updates, and then it froze up. I couldn't get it started again, so I forced a reboot.

When Ubuntu rebooted, the mouse and keyboard were unresponsive. Couldn't do anything.
I figured screw it, I'll just reinstall Ubuntu and try the update again. 

So, I couldn't figure out how to reinstall Ubuntu during startup. Figured okay, I'll just log back into Windows, delete the partition that Ubuntu was on, and start from scratch like when I first installed it.

What didn't occur to me until after, was that deleting the partition would mean deleting Grub (well, I assume this is what happened), and so now I'm stuck at the "error: Unknown filesystem" menu and cannot progress from there. Can't even log into Windows.


Oops. #-o ](*,)

So, is there any saving this poor stupid sod? :\

---

### Post by wilee-nilee on 2010-09-20
Boot a live ubuntu cd and run the script in my signature. When you copy and paste the text to a reply click on the # and put the text between the code tags.

Getting Windows reloaded to the mbr is easy we just need to see the whole setup.

---

### Post by Eugeneslipped on 2010-09-20
My netbook doesn't have a CD drive, I used a USB drive to boot up and install Ubuntu. Can I do the same thing through the USB stick?

EDIT: "Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection."

The issue is I don't actually know how to get that far :\ I've got my USB stick plugged in, but I can't progress from there. The instant I press the power button, it goes to the error menu.

---

### Post by wilee-nilee on 2010-09-20
> **Eugeneslipped said:**
> My netbook doesn't have a CD drive, I used a USB drive to boot up and install Ubuntu. Can I do the same thing through the USB stick?
** Yes**

EDIT: "Boot into any Linux based operating system, LiveCD 
or LiveUSB with an Internet connection."

The issue is I don't actually know how to get that far :\ I've got my USB stick plugged in, but I can't progress from there. The instant I press the power button, it goes to the error menu.

Your computer can boot the usb with a f-key prompt, mine is f12. This is just a method of having a choice of what to boot from instead of changing the bios. The key could be any F-key or esc.

---

### Post by Eugeneslipped on 2010-09-20
Mmmm well right now I feel like a bit of a fool. 
I thought I'd set up the boot sequence properly, but obviously I had not. Got Ubuntu reinstalled again, and it's all working fine. Didn't realise I could get into the boot menu, I thought I was stuck at the error screen.

Hah, well thanks. All solved then! :)

---

### Post by wilee-nilee on 2010-09-20
> **Eugeneslipped said:**
> Mmmm well right now I feel like a bit of a fool. 
I thought I'd set up the boot sequence properly, but obviously I had not. Got Ubuntu reinstalled again, and it's all working fine. Didn't realise I could get into the boot menu, I thought I was stuck at the error screen.

Hah, well thanks. All solved then! :)

A lot of people don't know about this key prompt, I never change the bios order, but I have only 1 HD in all my computers. Glad you got it fixed, as without a cd reader it would of been hard to reload the mbr with the W7 bootloader, at least for me.

Make sure that it didn't boot because you had the thumb in and grub was put it in its mbr rather then the hd, if this is the case post the bootscript

---

