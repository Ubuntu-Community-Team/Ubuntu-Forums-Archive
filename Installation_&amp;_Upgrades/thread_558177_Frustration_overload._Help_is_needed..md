---
title: "Frustration overload. Help is needed."
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by fairlady350z on 2007-09-23
Please bear with me, this is gonna be a long post.

I have tried installing in 4 different ways:
1. Ubuntu Ultimate
2. Ubuntu Live CD
3. Ubuntu Alternate
4. Kubuntu Alternate

Most Ubuntu installation were successful BUT, when loading UBUNTU for the first time, it fails at the loading screen (the loading bar doesn't budge / move) and after a while I receive this message 

**"/bin/sh: Can't access tty; Job control turned off"**

So out of my frustration, I downloaded Kubuntu Alternate CD then installed it.
Hey it worked :) I could get into the GUI/desktop. Browse, use internet and stuff.. **BUT THEN** I installed nVIDIA driver thru ADEPT (nvidia-glx). Reboot.
Then the same 'curse' I describe above was spelled on this one too.
The loading bar doesn't move at all.
Same message occur:

**/bin/sh: Can't access tty; Job control turned off**

I did a research, a few people wrote that AHCI needs to be enabled and it has to be all SATA.
So I did, I bought a SATA DVD-Drive and make sure this time all SATA.
I -then- enabled AHCI.
This time was even worse, **BIOS could not detect my SATA HDD**. 
NO harddrive listed in BIOS either

The I was told to edit GRUB maybe it doesnt point to /dev/hda1/.
The thing is, when I hit ESC when ubuntu was loading, it went back straight to BIOS :(

So I'm frustrated beyond measure. It feels like everything I did was eventually hit the deadend.

I just want to get my linuxMCE working for home automation.

If anyone can give me ideas or solution.. you have no idea how thankful I will be.

Thank you

---

### Post by southernman on 2007-09-23
I know you've done a lot of research on your own, but I can't really help other than to help you research.

I do know that if your using all sata drives then > The I was told to edit GRUB maybe it doesnt point to /dev/hda1/. will not be hda, but will be sda.

Although this is for Feisty it may be related to fixes used in [this thread]("http://ubuntuforums.org/showthread.php?t=279884"). The ultimate solution for this OP was to use the alternate cd verses the livecd. If in fact you used the livecd, this maybe a viable option.. although it's most surely a fixable problem without reinstalling.

Good Luck and post back your findings please.

---

### Post by Pumalite on 2007-09-23
According to your post you had a system working: Xubuntu. All you have to do is install it back and do not install the nvidia drivers. Please post your specs for me to have a clearer idea of your problem.

---

### Post by fairlady350z on 2007-09-23
Thank you all for your replies.

Here's my spec:
Mobo: Abit ip35-Pro
Graphic: PNY nVIDIA 8800GTS 320mb
CPU: Q6600 (GO Stepping)
1 Internal SATA HDD
1 Internal SATA DVD drive 

update:
I did another Ubuntu installation this time (the ultimate version). However I wasn't aware of your respond at that time and installed the nVidia driver using Envy.
It turns out that the mail culprit is the path. Correcting the path, I see a shed of light.

Now Ubuntu loads pass the loading screen. :D

Long list of text came in afterward, then I got an error message regarding xserver.
It says: 
[B]failed to start the xserver
failed to load module "nvidia"[/B]

So should I did another installation without deleting the partition? or should I go from here and try to fix this nvidia issue?

Thank you

---

### Post by Pumalite on 2007-09-23
Your Nvidia card is a problem; it's too new.
You can install again after cleaning your partition with Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
When you get to the failure of xserver (at the end), you can try this:
sudo dpkg-reconfigure xserver-xorg, accept most dafaults, choose 'vesa' as the driver, then: startx
If you don't have a command line, try this: Ctrl+Alt+F1

---

### Post by fairlady350z on 2007-09-24
Hi all,

Problems have been fixed. Now I can log in into Ubuntu with no problem. even with a dual screen :)
I'm so excited since this is the first time I got it up and running :)
Now I have to fix sound :) but it can wait until tomorow.

Thank you all for the help.

-------------------------------------------

---

### Post by Pumalite on 2007-09-24
Glad you got it working.

---

