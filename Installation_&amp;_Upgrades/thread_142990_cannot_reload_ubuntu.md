---
title: "cannot reload ubuntu"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by dsimpson on 2006-03-11
I am trying to reboot and reload Ubuntu installation cd and I am unable to. I get the following message and my computer is locked up and will not proceed with the installation.

grub loading stage 1.5
grub loading please wait
error 15

 I had installed and done some work with apt-get and was going to write over the old installation. What went wrong? how do I work around this?

---

### Post by kaptainlange on 2006-03-11
I don't remember exactly but I think this is the error that occurs when grub can't find the menu.lst file that is trying to see.  Or some other file in your /boot directory.

Did you already format the partion the /boot directory was in?

---

### Post by dsimpson on 2006-03-11
Yes I did format it when I first installed Ubuntu onto my hd, Ubuntu is the only OS on the computer, and I was trying to write over the old installation because I somehow lost help! on the first install. when I would try to access help files it would give me a message it couldn't be found. Is there a way to reformat and do a new install?

---

### Post by kaptainlange on 2006-03-11
I think I understand now what you are saying.  If I understand, you currently have nothing on the computer that you need to preserve and simply want to start the installation from an Ubuntu CD you have.  If that is the case, it is just a matter of making sure your BIOS is set to boot your computer from the CD-Drive before the Hard Drive.

You just need to get into your BIOS through whatever means your computer allows you to do that.  Usually you hit delete, F1, or some other combination of keys when the computer is POST'ing.  Once in the BIOS you have to look for somewhere to change the boot order of your computer.

I couldn't tell you exactly how to do this since many motherboards vary their methods and BIOS software.

When the computer is posting look for something like
Hit F1 to enter Setup
Or
Hit Delete to enter Setup

---

### Post by dsimpson on 2006-03-11
Hi, I did change the settings, it boots to the cd drive but the error message is the first thing that appears and it will not allow me to go any farther. No options appear, just the message and it stays locked there regardless of what key I may try, such as esc, del, or the fkeys.

---

### Post by kaptainlange on 2006-03-11
Well this really sounds like it is still trying to boot from the hard drive, unless you have grub installed on the boot sector of the cd, but that seems unlikely.  Maybe someone else knows if the Ubuntu CD uses grub or not, but I don't think it does.

The other idea I have is if you have more than one cd drive.  If you do, try to put the cd in the other drive and try booting then.

I would like the emphasize at this point that it seems like you are still booting from your hard disk if you are getting your grub error.

-or-

You don't happen to have a GRUB floppy disk in your floppy drive do you?  If thats the case, take it out.

---

### Post by dsimpson on 2006-03-11
hello kaptainlange,thank you very much for your patience and help, the computer was on the default settings, how I can't say, reset the order of boot and it is now loading, I can't thank you enough. Have a great weekend!!

---

