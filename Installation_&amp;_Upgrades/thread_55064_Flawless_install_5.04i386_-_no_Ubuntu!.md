---
title: "Flawless install 5.04/i386 - no Ubuntu!"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by thecdn on 2005-08-07
This morning I installed 5.04 i386 on my amd 3500+, ATI X800 XL, machine and it went perfectly, I thought. The grub install said it was successful and the last thing Ubuntu said was rebooting into Ubuntu to continue the install.

But it goes straight into xp, there isn't even the word 'Lilo' flashed across the screen during bootup - just into xp.

I did the install twice, both went perfectly, both times no ubuntu. What could be causing this? I'm pretty much a linux noob, I've played with xandros for the last couple of months and wanted to look at ubuntu.

Speaking of xandros, I want to install it after ubuntu. It uses lilo and from what I've seen on the xandros forums it's supposed to be good at picking up all other os's on the drive and putting them on the boot menu. Think if I try installing xandros now it might pick up my wayward ubuntu install?

I have both knoppix and ubuntu live cd's available as tools to use to check things out. Any thoughts or ideas would be greatly appreciated. 

PS.  I tried loading the amd64 version yesterday and it was a disaster. The grub install failed, the lilo install semi-worked - enough so that you could see the word 'Lilo' flash on the screen before it loaded into Ubuntu, no xp in sight. I tried all my limited means to get things working before I gave up and reformatted the drive (to get rid of lilo) and reinstalled xp. Anyone else have such issues with the amd64 install?
I really liked the look and functionality that I saw of Ubunu and want to have a machine with xp, ubuntu, and xandros so I can compare and contrast. I need the xp for some of the wifes programs.

Edited to add:
In lieu of an answer to the above issues, is there a way to confirm whether or not ubuntu did indeed load properly and this is just a grub issue?

---

### Post by edwina on 2005-08-07
Okay, I'll see if I can help, but I'm no expert ...

The GRUB menu isn't kicking in, it would seem. Where did you install GRUB to? Personally I stuck it on the Master Boot Record (MBR), which seemed to do the trick, although there are alternatives about. The MBR method seemed easiest to me, especially as you can always use the XP rescue disk to fix it if it all goes horribly wrong. Probably not the sort of thing you're supposed to say on Linux forums, eh?  [-X 

Did you put a boot flag on the partition that Ubuntu was installed to? Check out the help file in the expert installer page for advice on that one. Did you mount the Ubuntu partition to "/" (root)?

Check out my installation post: [http://www.ubuntuforums.org/showthread.php?t=54817](http://www.ubuntuforums.org/showthread.php?t=54817)

I used a parallel-install of XP to revive my initial XP install and over-write my stuffed up MBR. That allowed me to try Ubuntu again, slightly better informed second time around. Might be better than starting from scratch and losing all of your original XP set-up.

Your best bet for checking out your Ubuntu install (assuming it exists) is with a live CD. I use Knoppix because I already had the CD, but I'm sure Ubuntu Live works just as well. Look for your GRUB boot file (not sure where it is, as I'm not on my Ubuntu machine, but it's something like boot.lst in your /boot/GRUB directory) and post the contents here.

I've never used Xandros I'm afraid, so can't help there.

Let us know how you get on!

---

### Post by thecdn on 2005-08-07
Well, not being the patient type I went ahead and installed Xandros to see what would happen. At first it did the same as Ubuntu, flawless install followed by nothing, a boot straight to XP. 

When I tried it again I noticed that xandros loaded it's lilo by default on my ide drive, the second one. I changed this to point to my main drive, a sata one and installed again. Voila!!! The xandros os selection menu picked up itself, xp, and ubuntu. I certainly can't explain why or how but right now I'm just thrilled to have a triple boot machine and hope it stays healthy for awhile.

Thanks for your thoughts on this matter.

Dale

---

