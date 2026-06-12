---
title: "Can't reinstall grub"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by gorgory on 2011-03-29
I have Ubuntu 10.10 and Windows 7 on my computer. After not booting into my Ubuntu partition for a while, I noticed that grub had disappeared, being replaced by the windows bootloader. I followed the steps [here]("https://help.ubuntu.com/community/Grub2") under "reinstalling from liveCD" and I was able to get a grub command line when I rebooted, but no boot menu. So I booted into Ubuntu and ran update-grub like the instructions say, and the output indicated that Ubuntu and Windows had both been successfully found and added to grub.cfg. But when I rebooted, I still only got the grub command line. When the instructions had steps for if you had a separate boot partition, I used /dev/sda1 because it is marked by fdisk as being the boot partition. I thought that maybe update-grub was only seeing /boot on the Ubuntu partition and wasn't touching the boot partition, so I tried mounting /dev/sda1 as /boot, but after that grub didn't boot at all, it just goes straight to Windows and I haven't been able to reinstall grub even after following the steps again several times.

How can I get grub back?

---

### Post by wilee-nilee on 2011-03-29
Click on the bootscript link in my signature follow the instructions to generate a text file. Come back to the thrtead open a reply click on the (#) in the reply panel=code tags, and paste all the generated text between. Also let us know the computer model and manufacturer, sounds like a Dell.

---

### Post by gorgory on 2011-03-30
Well, this is kind of embarrassing, but I'll post what happened in case it helps anyone.

I ran the boot script and it said that everything was set up the way it was supposed to be, so I got doubly confused about why it wasn't working, but then I remembered that the last time I used Ubuntu, I set grub to default to Windows and have a 0 second timeout because I thought I wouldn't be using Ubuntu anytime soon and didn't want to see the grub menu every time I rebooted. So today when I wanted to get to the grub menu I pressed escape to make it come up despite the 0 second timeout and instead of grub I got the Windows boot manager so I thought grub had been overwritten, but apparently I was just pressing escape at the wrong time because I tried resetting the timeout to 10 seconds and ran update-grub from the live CD, and it worked.

So there wasn't actually anything wrong with grub, but that script solved the problem anyway. Thanks wilee :P.

---

### Post by wilee-nilee on 2011-03-30
> **gorgory said:**
> Well, this is kind of embarrassing, but I'll post what happened in case it helps anyone.

I ran the boot script and it said that everything was set up the way it was supposed to be, so I got doubly confused about why it wasn't working, but then I remembered that the last time I used Ubuntu, I set grub to default to Windows and have a 0 second timeout because I thought I wouldn't be using Ubuntu anytime soon and didn't want to see the grub menu every time I rebooted. So today when I wanted to get to the grub menu I pressed escape to make it come up despite the 0 second timeout and instead of grub I got the Windows boot manager so I thought grub had been overwritten, but apparently I was just pressing escape at the wrong time because I tried resetting the timeout to 10 seconds and ran update-grub from the live CD, and it worked.

So there wasn't actually anything wrong with grub, but that script solved the problem anyway. Thanks wilee :P.

I use the script on my own setup on occasion as well, good job figuring it out.:)

---

