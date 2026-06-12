---
title: "Installation help for newbie, please."
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by SPr on 2006-11-29
Hi,

as the title says I'm complete newb with anything that isn't MS related. I've searched these forums and not found anything to help me so if these questions have already been answered I apologise.

I downloaded the Live CD for Edgy and decided that I'd install it to my external Western Digital USB HDD.

The install went very smoothly (or so I thought). Grub was installed to the external HDDs MBR. I shutdown, restarted and got the Grub error 21. After reading this forum I know now that I should have expected this to happen.

Can I re-install Edgy but without Grub? If so, how? If it can be done I plan to use a Windows boot manager to boot into Ubuntu then (maybe) configure Grub from there.

If installing without Grub can't be done then is it possible to use the Live CD as a rescue disc and will these instructions ([www.ubuntuforums.org/showthread.php?t=80811](www.ubuntuforums.org/showthread.php?t=80811)) work for Edgy?

Thanks in advance for any help anyone can offer :)

Edit:
I would download the alternative install CD but my ISP has started to come down hard on people making large downloads :(

---

### Post by bazerk on 2006-11-29
Are you short of space on your internal harddrive? cos the obvious solution is to reinstall edgy on to it and grub will do what it does properly.
otherwise fixmbr on you windows rescue disk will get rid of grub, I can't see it easily working on a usb hard drive.

---

### Post by SPr on 2006-11-29
Hi,

thanks for the reply.

I'm not short of space on the internal HDD but I have an external drive that I use to back up my internal drive and I'd rather use the external drive rather than the internal for Ubuntu.

The Windows MBR is fine :) I installed Grub to the external HDD MBR.

I've had a play with the live CD and I assume the answer to my question is that I ought to open a terminal and sudo the commands from the link in my original post.

---

### Post by SPr on 2006-11-29
I've tried following the instructions here. 
[www.ubuntuforums.org/showthread.php?t=80811](www.ubuntuforums.org/showthread.php?t=80811)
I loaded the live cd, mounted my ext USB HDD and changed the root to my USB HDD and edited the required files and ran mkinitramfs with no luck.

mkinitramfs worked, or at least I assume it did because the external hard drive was busy for a couple of seconds.

Any ideas?

---

### Post by SPr on 2006-12-02
Hi,

i got an alternative CD installer and ran through the installation with it. I then followed the instructions in the link in my first post but I still can't boot into Ubuntu. I still receive the GRUB error 21 at stage 1_5.

I've searched this forum and Google for more info but I'm afraid GRUB doesn't want to work for me.

Does anyone have any ideas?

Please ask for more info if it's needed, thanks.

---

### Post by rsambuca on 2006-12-02
does the USB drive show up in your bios?

---

### Post by SPr on 2006-12-02
Hi,

yes the USB drive does show up.

The BIOS allows the USB drive to emulate various drive types (floppy, CD rom, HDD etc) so I changed this to no emulation and now I can boot into Ubuntu! :D

Such a simple solution that has been so difficult to find.

Thanks for your reply.

---

### Post by rsambuca on 2006-12-02
good stuff.  Just a lucky guess!

---

