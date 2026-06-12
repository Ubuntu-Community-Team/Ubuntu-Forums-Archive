---
title: "CD Boots HD Hangs"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by Sigmeister on 2007-09-28
I have downloaded the iso file, burned it to a disk. When loading 7.04 from CD disk my machine hangs. I found that if I change the screen resolution to anything but VGA it will load normally. Then I installed to a blank external HD and disable my regular HD's. It seemed like the install went ok. When loading it now hangs like the cd did but there is no way to change the resolution. The tabs that were at the bottom of the screen on the cd boot are not on the screen of the HD boot. Any ideas?

AMD 64 7.04
PCIE ATI video
1 gig dual channel

---

### Post by Sigmeister on 2007-09-29
Is there some knid of code I can enter to change the resolution durring startup? I have an ATI video card. How do I do it? It works quite well from the CD, but slow. My download speed is three times my download speed in windows, which really makes me want to make it work, form the hard drive. I've tried all that a person who knows next to nothing can. I really don't wnat to give up.

---

### Post by Pumalite on 2007-09-29
Memory?

---

### Post by Sigmeister on 2007-09-29
ATI 128 mb x700 video card

---

### Post by Pumalite on 2007-09-29
Memory of the computer.

---

### Post by PmDematagoda on 2007-09-29
I think it's I Gb Pumalite.

> 1 gig dual channel

Try cleaning your RAM modules by removing them and cleaning across the gold contacts using a soft, clean and dry cloth. Then clean the slots, though I'm not very sure if you clean the slots using a clean, soft and dry cloth or by blowing some dry air to get rid of any dirt.

---

### Post by Pumalite on 2007-09-29
Thanks. Sorry, my mistake. Your hardware is fine. Your only problem is your ATI. Because of that, get an Alternate CD and install with that. If you have a problem with xserver, post back. You should be OK.

---

### Post by PmDematagoda on 2007-09-29
Pumalite I believe he already has installed Ubuntu:-
> 
Then I installed to a blank external HD and disable my regular HD's. It seemed like the install went ok. When loading it now hangs like the cd did but there is no way to change the resolution.

---

### Post by PmDematagoda on 2007-09-29
The tabs(Options) you get with the Live CD disappear after you install Ubuntu, unless of course you boot with the Live CD.

But about the ATI driver I'm not very good at it since I have an Nvidia. But it may be your RAM in addition to your video card. But it is better to ensure that the VGA card is fine before jumping to the RAM.

---

### Post by Pumalite on 2007-09-29
If that's the case, lets see if he has a command line. Do you? If not, try: Ctrl+Alt+F1
If you get a command line, try this:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by PmDematagoda on 2007-09-29
The CLI is the master and savior here. I'll help whenever I can.:)

The guy we're trying to help has gone offline(sigh).

But Pumalite, if there is a problem with the xorg.conf file doesn't X-server itself not function?

---

### Post by Sigmeister on 2007-09-29
I believe I can get a command line. I get     grub> 
 I need to know what commands ect. to cahnge the screen resolution.

---

### Post by Sigmeister on 2007-09-29
What is an alternate CD and where do I get it? I am currently using the AMD64 version.

---

### Post by PmDematagoda on 2007-09-29
The Alternate CD is the text based installer for Linux.

You can get the alternate CD from here:-

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Sigmeister on 2007-09-30
Well I downloaded the Alternate CD installed it without a hitch to my hard drive. Set the resolution to 1024x768. When booting form the hd I get the same black screen as before. I don't see how I can boot from the CD with no problems but get nothing from the hardrive. It looks like if I had memory, video card problems ect. ect. ect. that neither version would work.

---

### Post by Pumalite on 2007-09-30
Get a Knoppix Live CD and take a look at your system: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Boot from it. From the Terminal post:
sudo fdisk -lu
And from the appropriate partition:
cat /boot/grub/menu.lst

---

