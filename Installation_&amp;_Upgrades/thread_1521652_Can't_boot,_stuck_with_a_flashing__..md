---
title: "Can't boot, stuck with a flashing _."
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Dangerouge on 2010-07-01
I just installed Ubuntu Studio 10.4. on my office computer, with XP on the first partition of the same hard disk. I installed GRUB on the master record as it suggested, and now when I try to do the first boot, I'm stuck with a black screen with nothing more than a flashing underscore ( _ ). The underscore keeps flashing for about 20 minutes, then disappears. And then I'm left with a completely blank screen, and I got tired of it after 5 minutes and restarted. XP is running fine, as you can see, and I've previously succesfully run the same Studio from a USB drive on the same computer, and it was working fine. Any suggestions?

---

### Post by dino99 on 2010-07-01
when booting, edit the boot line into grub menu and remove "quiet splash" to see the verbose comments and know what happen

(should be a video driver not activated)

---

### Post by Dangerouge on 2010-07-01
Hmm, the last thing it prints out is about how many memory pages (or something like that) it has found, then comes the flashing underscore again. What's supposed to come next?

---

### Post by Braik on 2010-07-01
Please read last one and sorry for the unwanted bumping

---

### Post by Braik on 2010-07-01
Idem

---

### Post by Braik on 2010-07-01
Hello everybody,
 
Actually I have a Ubuntu 10.04 LTS x64 as a single system installed since one month and it was working quite well... since yesterday when I accepted Update Manager new installs and a restart required demand of it. After that I have the same issue as our colleage: ***"Can't boot, stuck with a flashing _."***. 
 
I was also thinking that maybe a new kernel or option was giving an issue, but not seeing GRUB at the start and don't knowing how to access it (if it is installed), I have decided to launch my Karmic liveCD to try to fix the problem (Sorry did not found Lucid liveCD) but I get stuck exactly in the same point.
 
Please help me since I don't know what to do next :confused:.

---

### Post by Dangerouge on 2010-07-02
All right, now that the forums are working again...

I've got the system up and running 4 times now, but it's about 1/10 chance it won't get stuck, however I caught something that might be a clue of the problem: when it DOES start, it reads something like

Plymouth process shut down by KILL
or something like that, it's going too fast for my old screen and young eyes, I need a slower computer to figure... :D

So, plymouth is the load screen, right? Video card problem? I have an NVIDIA GeForce GTX 275. I tried installing the proprietary drivers, but it really makes no difference since I'm using a cathode ray tube screen (funnily, the model name is flatron, but this thang ain't seen flat), except that the unload screen makes no sense and is quite pure pixel porridge. I'm not sure if the disabling of the drivers will get me up and running nicely, since I don't think they were enabled to begin with, when the problem initially came up, however I'm giving it a try.

Any suggestions to me and my buddy here? Oh, and by the way, I enabled the proprietary drivers before installing the updates (on the same session) and it resulted in a chaos, I had to restart 30 times to get it up. I don't know if there is any connection here, since the number of successes is too low to build up any statistics.

---

### Post by Dangerouge on 2010-07-02
OK, the uninstalling of the proprietary drivers had no effect whatsoever, as predicted... I had to restart quite the hunk of times before I got this up, and again with a killed plymouth. However the thing that changed is that at one of the attempts to start I got this message:

udevd[185]: worker [x] did not accept message -1 (Connection refused), kill it
where 0 < x < 186.

---

### Post by Braik on 2010-07-02
Hi,
 
It's my turn to give some news. When I get back home I have accessed GRUB (holding shift key, thanks to GRUB manual), and removed the "quiet splash" part to launch new kernel (think 32-23??).
 
Tried to follow all the lines to see where the problem was and..... it just started without a problem :o.
 
So it worked (more or less) correctly since there was some minor things not running from the begining (as screenlets and PS media server) but nothing crucial. 
 
The final test was the shutdown and restart... but it also worked, so I am sorry but don't know why this happend and why it was repaired by itself.
 
Good luck

---

### Post by landersohn on 2010-07-02
I observed the same behavior when I tried to boot the 2.6.32.2 kernel that comes with 10.04 LTS. Booting the 2.6.32-23 version of the kernel, which is also on the live CD and gets installed, works just peachy (so far).

---

### Post by Dangerouge on 2010-07-06
Hmm, the same behaviour continues, I'm running the -23 kernel and the problem appears to be in the plymouth process somewhere, I never get the load screen, always the same messages about killing plymouth and fcsk something (when I don't get the flashing _, which come 9/10 times I try to boot). Is there anyway to make the system kill these failing processes every time instead of randomly?

---

### Post by Dangerouge on 2010-07-07
Ok, now I did a clean install with a new disc (the previous one didn't work anymore so I thought the disc had been defected, and that's why I'm experiencing these problems, but no), which I checked for defects and it was ok. I still get the same messages when this actually boots and still no splash. Could this be my partitioning? I have one hard disk (~1TB), with first partition being WinXP, 210 GB, second ext4, about 200GB, third is ext4 @ /home/, 555GB and the rest (20GB) is swap.

---

### Post by Braik on 2010-07-07
Hi Dangerouge,
 
I had a similar problem as yours, and I was looking in other forums and I found this solution (works for UBUNTU) and I suppose it works with Ubuntu studio, It concerns this PLYMOUTH problem and apparently is present in a FAQ (don't ask me where), I copy paste the possible solutions:
```
5. Bootup/Plymouth. 
Users should experience a much faster boot however some users may experience problems with Plymouth after the nVidia graphics driver has been enabled. Users may experience plymouth using lower graphics resolution. 
[[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013[/COLOR]]("https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013")
 
Graphical solution : [[COLOR=#444444]http://news.softpedia.com/news/How-t...4-140810.shtml[/COLOR]]("http://news.softpedia.com/news/How-t...4-140810.shtml")
 
Command line :
(Some of the fixes put forward dont work for everyone.)
One that works for nVidia and to try is this.
Code:
gksu gedit /etc/default/grub
and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD_LINUX=1680x1050 Save the file and run
Code:
sudo update-grub
The resolution chosen should be your monitors native resolution.
 
Other graphics card users may get a black screen with flashing cursor and then a very short duration plymouth. 
[[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801[/COLOR]]("https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801")
One fix for this is to create this file.
Code:
gksu gedit /etc/initramfs-tools/conf.d/splash
and add this option FRAMEBUFFER=y, save the file.
Then
Code:
sudo update-initramfs -u
Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS. The advice is, if you don't want a graphical boot then uninstall any plymouth themes.
 
If the problem is a slow boot, and you have no floppy drive, disable the floppy in the bios. This has been reported as a fix to this. [[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...ks/+bug/551712[/COLOR]]("https://bugs.launchpad.net/ubuntu/+s...ks/+bug/551712")
 
If the problem is plymouth not displaying, and a black screen from grub to gdm, this could be due to graphics drivers needing to be loaded quicker. This is bugged.
[[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...ux/+bug/539787[/COLOR]]("https://bugs.launchpad.net/ubuntu/+s...ux/+bug/539787")
 
Plymouth is installed with 2 themes by default you can install more via synaptic.
To change themes this code is used.
Code:
sudo update-alternatives --config default.plymouth
```
 
I used the:
```
gksu gedit /etc/initramfs-tools/conf.d/splash
```
 
add this option :
```
FRAMEBUFFER=y
```
save the file and then
```
sudo update-initramfs -u
```
 
I don't know if this can help you our maybe (if you have a nVidia card) try another proposed solution.
 
Good luck

---

### Post by Dangerouge on 2010-07-07
The problem seems to be fixed I've gotten this up a few times in a row now, I'm even getting a load screen splash after a few init messages. The bug I was experiencing seems to be this one: [Bug #594839 in plymouth (Ubuntu): “Plymouthd SIGSEGV on Lucid Xen Instance”]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/594839") or at least the fix worked... So thanks to everyone who tried to help me, I'm happy we share our problems! ^^

---

