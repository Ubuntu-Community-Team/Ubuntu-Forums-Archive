---
title: "black screen when trying to install Ubuntu 10.10"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by the_Terminator on 2010-10-26
[SIZE=4][COLOR=DarkOliveGreen]I have a Machine
Intel Celeron 325 2530Mhz
768MB DDR RAM
Geforce FX5500 nVidia 128MB
WD 320GB SATA

I have already XP SP3 and Open SuSe 11
I am trying to install Ubuntu 10.10 but everytime I started installation I got a black screen
with errors (__bad__semaphore blabla)
i tried more than one cd and all of them worked on other machines
please help me :confused::confused:
[/COLOR][/SIZE]

---

### Post by the_Terminator on 2010-10-26
pleaaaaaaaaaaaaase help :(

---

### Post by Uncle Spellbinder on 2010-10-26
Same issue here. 

I initially posedt this question in the testing section (now closed) about 10.10 RC. No real answer was attained. Still having the same iss with final release...

Can't get past the initial dialogue on install of 10.10. Goes to black screen and I have to do a hard reboot. Same when I try using WUBI. My system recently had the video card (nVidia 9800GT) and the power source go out. Had them both replaced. I now have an ATI card. I'm going to assume this is a video card issue. Any ideas?


My current desktop specs...

HP Pavilion Elite M9360F(KQ499AA) 
Operating System - Windows 7 Ultimate 32-bit
Processor - Intel Core 2 Quad Q9300(2.50GHz)
Processor Main Features - 64 bit Quad-Core Processor
Cache Per Processor - 6MB L2 Cache
Memory - 8GB DDR2 800
Hard Drives - 2 x 500GB SATA 7200RPM
Optical Drive - Blu-ray player & SuperMulti DVD burner with LightScribe Technology drive
Graphics - ATI XFX Radeon 4650, with 512MB dedicated video memory (DirectX 10 ready).
Audio - Realtek Integrated High Definition Audio
Ethernet - Integrated 10/100/1000Mbps network interface
Wireless Card - Wireless LAN 802.11 b/g/n
NTSC TV tuner, over-the-air ATSC high-definition Digital TV tuner, and FM tuner
[Hauppauge WinTV HVR-1800 (Model 78xxx, Combo ATSC/QAM)]
HP Media Center remote control with IR (infrared) receiver

---

### Post by Rubi1200 on 2010-10-26
Hi guys,
have a look at these links and see if there is anything that can help:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues)
[https://help.ubuntu.com/9.10/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/9.10/installation-guide/i386/boot-troubleshooting.html)
[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by the_Terminator on 2010-10-26
thnx guys
do you think is the problem with 10.10 version itself????

---

### Post by Rubi1200 on 2010-10-26
It would really help if you could try and give us the whole error message and at what point in the process you see it.

Also, although this does not really answer your question, but have you tried 10.04?

---

### Post by Clodzilla on 2010-10-26
Rubi,
  None of the links you posted helped. When I get the prompt line, the computer goes into a black screen after about 1 minute and I have to do a hard reboot to get back out.

Also, I tried 10.4, but I could not get the wired or wireless connection to work from it. I also tried the 64-bit version (since I have a 64-bit machine), but the install failed. Can ONE of these work?

Thanks!

---

### Post by the_Terminator on 2010-10-26
here is the problem:
when i get the first screen either I choose "test without install" or "install"
i get a black screen with long error message some content :
init Tainted: G       D   2.6.35-22-generic  #33-Ubuntu
[ 5.609664]     Call Trace:
[ 5.609723]     ? printk +0x2d/0x35
..............        error 4 in libc.so.6
..................    panic+0

---

### Post by Uncle Spellbinder on 2010-10-26
I get no error message at all. Just a blank, black screen like my monitor has turned off.

---

### Post by Uncle Spellbinder on 2010-10-26
> **Clodzilla said:**
> Rubi,
  None of the links you posted helped. When I get the prompt line, the computer goes into a black screen after about 1 minute and I have to do a hard reboot to get back out.
Ditto for me.  Just tried 10.04 same result. Tried several other distros with live CD's and the same thing happens. This must be an ATI issue in my case. So far, the only distro to boot a live CD has been Katonix. All Ubuntu variants have gone to black screen, a few non-Debian based distros have also gone black. 

I think as soon as I can afford it, I'll be heading back to nVidia. 

:(

---

### Post by Rubi1200 on 2010-10-27
I'm sorry none of these things worked for you guys.

I think, from what I have seen and read, that a lot of these issues are related to graphics cards: ATI and Intel often seem to be problematic, but NVIDIA as well.

Unfortunately, it also seems that it is pot luck as to whether your card works with the latest kernel version etc. 

There are workarounds, but there is no one size fits all solution...yet.

But, don't give up; there are tons of LiveCD distros out there to try:
[http://www.livecdlist.com/](http://www.livecdlist.com/)

---

### Post by Uncle Spellbinder on 2010-10-27
> **Rubi1200 said:**
> I'm sorry none of these things worked for you guys.

I think, from what I have seen and read, that a lot of these issues are related to graphics cards: ATI and Intel often seem to be problematic, but NVIDIA as well.

Unfortunately, it also seems that it is pot luck as to whether your card works with the latest kernel version etc. 

There are workarounds, but there is no one size fits all solution...yet.

But, don't give up; there are tons of LiveCD distros out there to try:
[http://www.livecdlist.com/](http://www.livecdlist.com/)

I'm bookmarking and downloading many distros that appear to interest me. So far, Katonix (KDE) and PCLinuxOS (LXDE) are the only live CDs that will boot past the black screen. Still several more to attempt. Once I narrow down the bootable live CDs, I'll choose the one I like best and attempt an install. 

Appreciate the link, Rubi1200. I've also bee reading [DistroWatch](http://distrowatch.com/), another good source.

---

### Post by Rubi1200 on 2010-10-27
+1 to DistroWatch; I use it all the time.

Depending on what you want to do on your system, you might want to look at distros like Archbang, SliTaz, and AntiX.

---

### Post by Uncle Spellbinder on 2010-10-27
> **Rubi1200 said:**
> ...you might want to look at distros like Archbang, SliTaz, and AntiX.

AntiX looks interesting. Downloading now to test the live CD. Thanks for the suggestions.

---

### Post by GeekGirl1 on 2010-11-05
Black screen here also. HP Pavilion dm4t, installed with Windows 7.

I booted from a DVD image and initially saw a solid color (Ubuntu 10.10 background color) boot screen with the Ubuntu logo on the bottom. Then, it went to black.

That tells me all was OK until it switched video modes. I'll have to dig into this more.

Intel HD Graphics (core i5), 1366 x 768 resolution.

Update: Found the problem. The brightness defaults to "off", or low enough to show a black screen. All I did was hit the function key to increase brightness and everything was OK. Solution found on this thread: [Ubuntu on a HP Pavilion dm4-1060u]("http://ubuntuforums.org/showpost.php?p=9641991&postcount=13")

---

### Post by Tobeus on 2010-11-16
I've had the Potluck nightmare with 10.04 and 10.10.  Started using onboard ATI Radeon Xpress 200 onboard video.  Black screen on installer and after installation (used alternate installer).  So I grab an old nVidia geforce 7200GS.  Same problem.  So I buy a geforce 8400gs, same problem.  I have now ordered a new ati card that is set to arrive in about a week or so.  I'm really hoping that I do not have this problem with the new card.

I'm beginning to think that the issue may be with something different, but I have no clue where to start.  I managed to get the 8400gs to boot in failsafe graphics mode, but as soon as an nvidia driver is loaded (using nomodeset to boot and tried all versions in repository, and several directly from the nvidia website).  The only thing I can seem to get working on this machine is Ubuntu 9.04.

Anyway, I am not going to steal the thread, I just wanted to share the models I have not had luck with.  Hope everyone else gets this thing figured out.  Looks like some of us are just not meant to run ubuntu 10.04 or 10.10.  I blame tin whiskers.  ;-P

---

