---
title: "GRUB hangs after first install"
date: 2004-12-23
forum: Installation &amp; Upgrades
---

### Post by Peter Van Grieken on 2004-12-23
Hi, 

I have folowing hardware:
A Cubic Barbone pc (model EQ3401A) with an intel P4 2.6Ghz processor, 1Gb ram and a 80Gb Harddisk (pata) and an asus dvd writer (pata). Video card is a Matrox G550.

I just tried installing ubuntu on this pc, witch went pretty good, but after the installation finished, the computer rebooted and I got following message on screen:

GRUB loading stage 1.5
GRUB loading, please wait.

And that's it... No response anymore.

I already tried removing all USB devices from the pc, turning off hyper threading,  tried different settings regarding the sata/pata config, removed half the memory (I read somewhere ubuntu only supports up to 900Mb of ram) but the result is always the same.

Anybody got any ideas as to what this could be? The live cd booted just fine and I'ld really like to try ubuntu out.

---

### Post by aToaster on 2004-12-23
I ran into the same problem.

Heres my setup.
P2.6
Primary HD, 80g Western Digital <-- Linux
Secondary HD, 74g WD Raptor SATA<-- Windows
ATI x800

Hoping someone will have an answer.

---

### Post by Peter Van Grieken on 2004-12-24
Comeon... 38 views so far, and nobody has a clue? Am I doing something really weird here ? :D

---

### Post by Devin on 2004-12-24
I'm having the exact same issue. I have NO idea what's causing this either. Unfortunately I don't have a floppy drive so I can't boot that way. I mananged to do a fixmbr with the recovery console for Windows XP, but other then that, I have re-installed and formatted with Ubuntu many times and this still happens to me.

---

### Post by aToaster on 2004-12-25
I'm thinking since Ubuntu is a very new distro the community isn't as developed as say... the Gentoo community.  So there really might not be anyone who has figured out this problem as of yet.  I scoured the forums for an answer and there are around 4 other ongoing posts and no answers.  Lets just keep tinkering with it and see what we can find.  Good luck!

aToaster

---

### Post by Devin on 2004-12-26
I was able to get around this problem by using the expert installation mode, and then instead of GRUB I used LILO... only problem with that is it doesn't show my Windows installation and doesn't give me any options except Ubuntu when booting.... :-s

---

### Post by strady on 2004-12-27
I fixed it with an initial /boot partition :
hda1 /boot ext2 10Mb
hda2 / ReiserFs 20Gb
hda3 SWAP

now ubuntu boots, 

HTH

bye
Strady

---

### Post by bquiroga on 2005-01-12
I'm having the same problem as Peter, anyone fixed this yet?

Athlon 64 3000
74GB Raptor SATA WD <- ubuntu
120GB PATA WD

I tried installing ubuntu on both disks with the same problem

Also tried adding a boot partition, same problem..

---

### Post by bquiroga on 2005-01-12
I solved it by using LILO instead of GRUB :)

---

### Post by valadil on 2005-01-13
I had this problem too.  I used the ubuntu cd to boot and let it detect hardware.  Then I did ctrl-alt-f2 to get to a shell.  I made a new folder and mounted my root partition on that (no boot part or I would have done that too) then poked around with /boot/grub/menu.lst and device.map

There are a couple quirks with my system that made grub unhappy.  The first is that I have a pci card that gives me two more ide channels for hard drives.  The bios sees this after grub, so the drives on that become /dev/hd[e-h] and the drives on my motherboard are /dev/hd[a-d].  For some odd reason linux sees the card first and swaps the devices around.  So I end up telling grub to use hd0 as a root device but hdg is where it goes to look for the kernel.

The other problem is that my cd drives are on the primary ide cable and my hard drives are on the secondary.  I may just swap them eventually.  For now though I had to edit device map and point hd0 to /dev/hdc instead of hda because even though its the first hard drive it comes up after 2 cd drives when the bios detects things.

---

### Post by yetanothermuso on 2005-01-15
Same problem for me (warty). ASrock K8 combo-z m-board (ali 1689 chipset), 80gb HD,  512mbRam. Maybe the issue might have been related to an unrecognised PCI card - MSI PC54G2 wireless card (ralink2500 chipset). Because I couldn't get it to boot after trying to reinstall it 3 times (including downloading the iso again just in case) I'm using another distro as my "learn linux" for now, but will be back when I learn enough to troubleshoot.

---

### Post by tsalem on 2005-01-25
Thanks to xkfu on the LinuxQuestions forum, for suggesting to turn off the "LBA" option in the BIOS settings (should be in the hard drive options). Windows was giving me a bunch of problems (jokes aside :P), and Ubuntu and Mepis wouldn't boot at all.

Seems to have worked for him and me, and I'd advise giving it a shot.

---

### Post by sharkzf6 on 2005-01-26
[QUOTE=tsalem]Thanks to xkfu on the LinuxQuestions forum, for suggesting to turn off the "LBA" option in the BIOS settings (should be in the hard drive options). Windows was giving me a bunch of problems (jokes aside :P), and Ubuntu and Mepis wouldn't boot at all.

Seems to have worked for him and me, and I'd advise giving it a shot.[/QUOTE]

It worked for me as well. The first time I tried installing unbuntu, grub hung after base install/reboot [error 18]. After consulting this forum, I changed disk mode in my BIOS from LBA to NORMAL. That did it! Everything installed beautifully and is up and running...I love this OS. It combines the best of Windows with the best of Linux...from my perspective anyway.....cheers!

---

### Post by .: ronin :. on 2005-03-20
me 2, same problem

fujitsu-siemens amilo m1425
-pentium m725 (1,6 GHZ)
-512 mb ram
-60 gb sata
-radeon 9700 mobility 128 ram

but i cant find the lba-normal option in my bios

---

### Post by nrg9899 on 2007-05-15
> **aToaster said:**
> I ran into the same problem.

Heres my setup.
P2.6
Primary HD, 80g Western Digital &lt;-- Linux
Secondary HD, 74g WD Raptor SATA&lt;-- Windows
ATI x800

Hoping someone will have an answer.


[weather mapquest American Idol chemistry solar](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/index.php)

---

