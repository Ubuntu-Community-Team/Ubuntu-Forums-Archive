---
title: "Black Screen W/ Cursor Instead of Ubuntu Boot Screen"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by SendDerek on 2007-04-15
Hello All...

I have a problem with a fresh install of Ubuntu.  I installed edgy eft with the alternative CD and everything is working very well except the startup/shutdown process on my Dell Dimension (model number unknown right now since I'm not there).

Basically, when I start the computer up, I get the GRUB menu and then after that, I get a black screen with no Ubuntu Logo or Progress Bar.  Instead I get a blinking cursor in the corner and I have to press a key on the keyboard (space bar) to get it to go away, and then I have to press the space bar again to get it to start loading.  I have to wait for a little while until it shows the login screen like normal.

Same thing happens on shut down.  When I shut down, I don't get the Ubuntu logo and progress bar.  Instead, I get the same blinking cursor waiting for some sort of input in order to continue shutting down.

It's not a very complicated setup... the PC has a P4 2.8GHz with 512MB PC2700 RAM and a 15in LCD display (1024 x 768 resolution).

Does anybody have any idea?

Thanks in advance...
-Derek

---

### Post by SendDerek on 2007-04-17
I'm thinking that maybe I should just re-format with fiesty since it's coming out really soon...  what do you think?

---

### Post by moterpent on 2007-04-25
SendDerek,

I know your question came up a week ago and you may have already solved the problem.  If not, you may want to check this post:

  [http://ubuntuforums.org/showthread.php?t=417729](http://ubuntuforums.org/showthread.php?t=417729)

I had the same/similar problem.  In a nutshell, I've partially solved the problem by adding the "vga=792" option to the /boot/grub/menu.lst file.  The relevant portion of my "menu.lst" file looks something like this:

```

title       Ubuntu, kernel 2.6.17-11-386
root        (hd0,1)
kernel      /boot/vmlinuz-2.6.17-11-386 root=UUID=74cfa60b-3b72-4b8c-a002-8c7037a51de1 resume=/dev/hda5 ro pci=noacpi acpi_sleep=s3_bios quiet splash vga=792
initrd      /boot/initrd.img-2.6.17-11-386
savedefault
boot

```

I still have a problem with the splash screen not being centered but at least I'm getting close.  I hope this helps.

---

### Post by SendDerek on 2007-04-25
Thank you very much for your help!

I ended up just scrapping the linux/vmware thing and went with pure windows instead for right now.

---

