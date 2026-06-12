---
title: "Unable to Install Ubuntu 10.04.4 Desktop"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by minecraftmeun5 on 2014-05-26
[FONT=arial][SIZE=3]I am trying to install [/SIZE][/FONT][FONT=arial][SIZE=3]Ubuntu 10.04.4 LTS (Lucid Lynx)[/SIZE][/FONT] on a blank PC. it is about 12 years old. i have used a live CD and i would of used live USB but USB booting does not work on this PC. It work fine up to this part isapnp: No Plug and Play device found

Images to come.

-meun5

---

### Post by Bashing-om on 2014-05-26
minecraftmeun5; Hi ! Welcome to the forum.

Be advised that release 10.04 is no longer supported. The required software repositories no longer exist for the desktop.

May I suggest you install a current release Lubuntu ? Lubuntu is designed for "older" hardware.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

I trust that will be a much better experience.

[INDENT][INDENT]one big step
[/INDENT][/INDENT]

---

### Post by minecraftmeun5 on 2014-05-26
Thank you i will install it now

---

### Post by Bashing-om on 2014-05-26
minecraftmeun5; Hey.

You are quite welcome.

Any other problems, remember we are here .

[INDENT][INDENT]help is one of the things 
[INDENT][INDENT][INDENT]we do best
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by minecraftmeun5 on 2014-05-26
I tried installing Lubuntu 14.04 but it froze at Boot from CD: Loading bootlogo...
[IMG]https://snt148.afx.ms/att/GetAttachment.aspx?file=78107e82-32c0-41b2-9d12-02f7c2586837.jpg&ct=aW1hZ2UvanBlZw_3d_3d&name=cGhvdG8uSlBH&inline=0&rfc=0&empty=False&cid=ed5cf8b6baefc513&entryPt=filename&biciPrevious=3ba0551a-9e0e-46a5-b5ff-ad513dfe70d1_005d4c7b00f_5707&hm__login=clamy4&hm__domain=msn.com&ip=10.148.170.8&d=d971&mf=0&hm__ts=Tue%2c%2027%20May%202014%2001%3a16%3a39%20GMT&st=clamy4%402&hm__ha=01_d064c792b7c94519c5384975d8c530c63fd929ff78f0fd9af00c179c0745051f&oneredir=1[/IMG]

-meun5

---

### Post by nu2u904 on 2014-05-26
I am trying to make a new post and can't find  spot to click on!

---

### Post by minecraftmeun5 on 2014-05-26
Try the Post new Thread Button near the top left corner of the page

---

### Post by Bashing-om on 2014-05-26
minecraftmeun5; Well,

That is not good !
OK, Roll our sleeves up and go to work.
Let's find the cause ->
Can you boot the liveDVD ( you did burn to a DVD, yes ?) to "try ubuntu" mode  to the desk top ?
What processor are you using in the computer ?
What Graphics card are you using ?

Maybe we can tweak the boot parameters and get you to boot in "try ubuntu" mode ? see then what it will take in the actual install.

[INDENT][INDENT]look'n for cause and effect
[/INDENT][/INDENT]

---

### Post by minecraftmeun5 on 2014-05-27
I can not get to the "try ubuntu" part as this happenes when the bios boots from the CD. the graphics card looks like a eVGA GeForce4 MX440. the processor is a Intel Pentium 4 but i am not sure. The Motherboard is a Gigabyte GA-8IEXP rev 1.2 i think.

---

### Post by Bashing-om on 2014-05-27
minecraftmeun5; Well !

Let's try this:
Boot the liveDVD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets" - not of concern at this time.
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point, as we can fix that at a later time too.

For now we just want to get you booting to the desktop within the "try ubuntu" mode. Once we know the booting parameter required, we can see about starting the installer.

[INDENT][INDENT]we keep plugging away at this
[/INDENT][/INDENT]

---

### Post by minecraftmeun5 on 2014-05-27
Is this in Lubuntu or Ubuntu

---

### Post by Bashing-om on 2014-05-27
minecraftmeun5; Yuk,

Yeah the "purple splash screen" is directed at 'ubuntu'.. the process though is the same.
As soon as the bios screen clears, depress and hold the right **** key -> language screen, escape key to accept the default -> boot options screen.

regret that I confused you.

---

### Post by minecraftmeun5 on 2014-05-27
In Ubuntu when i try the boot argument it stops at input: At Translatation Set 2 keyboard as /devices/platform/i8042/seroid0/input/input1
[IMG]http://i.imgur.com/7KyVpF4.jpg[/IMG]

Thanks,
-meun5

---

### Post by Bashing-om on 2014-05-27
minecraftmeun5; Not Good !

I see 2 problems:
edd information not available -> is this an old old CRT monitor ?
set2 keyboard -> try and see if there are settings in bios to set the keyboard to "legacy", and what ever is set now for plug and play, change it to the alternate.

All I can think of presently, see what we can do in bios.

back'n up to punt

---

### Post by minecraftmeun5 on 2014-05-27
It is not a CRT monitor it is Fuji Plus LCD monitor. I think that the keyboard issue could be that the keyboard is really USB but the computer doesn't support USB keyboards so it is through a adapter but i change the bios settings i think.

---

### Post by mörgæs on 2014-05-27
The graphics card is old and there are reports that it does not work well in 14.04. 
I suggest something 12.04-based. See more in the link in my signature.

---

### Post by minecraftmeun5 on 2014-05-27
I tried Lubuntu 14.04 but it froze at the Loading bootlogo[IMG]http://i.imgur.com/jnmG9gf.jpg[/IMG]

I cant fit 12.04 Desktop on my CD but i can fit the server edition, can i start a desktop from there?

---

### Post by kansasnoob on 2014-05-27
> **minecraftmeun5 said:**
> I tried Lubuntu 14.04 but it froze at the Loading bootlogo[IMG]http://i.imgur.com/jnmG9gf.jpg[/IMG]

I cant fit 12.04 Desktop on my CD but i can fit the server edition, can i start a desktop from there?

Rather than use a server image I'd use the archived 12.04.1 image:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

I know the header says 12.04.3 but if you look the 12.04.1 images are there. My reasoning behind that is due to the LTS hardware enablement stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Basically the current 12.04.4 images use the Saucy kernel and X-stack so in a few months you'd have to upgrade to the Trusty kernel and X-stack which appear to be causing you problems anyway. The original Precise kernel and X-stack are supported throughout April 2017 so much less likely to cause major problems.

Also though both the 12.04.1 desktop and alternate i386 images are still CD size :D

---

### Post by Bashing-om on 2014-05-28
minecraftmeun5; kansasnoob; Hey;

Initially, on release, 12.04.1 did fit on a CD, however with the upgrades to 12.04 it no longer fits on a CD. shucks.
I recently (re-)installed 12.04.1 ( I want to keep the older xserver) and I had the thought rather than downloading all the recent updates on that original liveCD to download it again. Guess my consternation when I found it no longer fits on a CD .. had to go all the way into town a buy some DVD blanks.

Same story when I went to clean install Lubuntu, no longer fits on a CD (36 bits to big !)

Being the case we are restricted to CDs, how about we try bodi-linux ?

[INDENT][INDENT]hey it is a thought
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-05-28
Silly question, but you are using the 32bit version and not the 64bit Ubuntu??? You could always go for a minimal install. It will install just the kernel. Don't choose to install anything else during the process. Once complete, the computer reboots to a CLI screen with cursor. Login and issue:

```
sudo apt-get install ubuntu-desktop
```

Reboot and you should get to a graphical login screen then into Ubuntu. The minimal install details are here:

[https://help.ubuntu.com/community/Installation/MinimalCD#A32-bit_PC_.28x86.29](https://help.ubuntu.com/community/Installation/MinimalCD#A32-bit_PC_.28x86.29)

This is a good way to get a full Ubuntu when you can only boot from CD. The minimal ISO will fit on a CD with room to spare ... ;)

---

### Post by Bashing-om on 2014-05-28
+ 1 for Bucky Ball ! 

[INDENT][INDENT][INDENT]maybe we ought to nude that '1' up a bit
[/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2014-05-28
-1 to everything Ubuntu for this graphics card. Again, the way to go is something 12.04-based, light and supported.

---

### Post by kansasnoob on 2014-05-28
> **Bashing-om said:**
> minecraftmeun5; kansasnoob; Hey;

Initially, on release, 12.04.1 did fit on a CD, however with the upgrades to 12.04 it no longer fits on a CD. shucks.
I recently (re-)installed 12.04.1 ( I want to keep the older xserver) and I had the thought rather than downloading all the recent updates on that original liveCD to download it again. Guess my consternation when I found it no longer fits on a CD .. had to go all the way into town a buy some DVD blanks.

Same story when I went to clean install Lubuntu, no longer fits on a CD (36 bits to big !)

Being the case we are restricted to CDs, how about we try bodi-linux ?

[INDENT][INDENT]hey it is a thought
[/INDENT][/INDENT]

Errm, no idea what you're thinking :confused:

I just zsynced 12.04.1 and it's 696mb:

```
lance@lance-desktop:~$ cd Downloads/Ubuntu
lance@lance-desktop:~/Downloads/Ubuntu$ ls
precise-desktop-i386.iso         ubuntu-14.04-desktop-amd64.iso
trusty-desktop-i386.iso          ubuntu-14.04-desktop-i386.iso
ubuntu-11.10-desktop-i386.iso    utopic-desktop-i386.iso
ubuntu-12.04.1-desktop-i386.iso  utopic-desktop-i386.iso.zs-old
lance@lance-desktop:~/Downloads/Ubuntu$ [B]ls -sh ubuntu-12.04.1-desktop-i386.iso
[COLOR="#FF0000"]696M ubuntu-12.04.1-desktop-i386.iso[/COLOR][/B]

```

---

### Post by kansasnoob on 2014-05-28
Just thought to add that Precise still offers Unity-2D and it's easy to set up a [classic desktop w/metacity]("http://ubuntuforums.org/showthread.php?t=1966370") if Unity isn't your thing :)

---

### Post by minecraftmeun5 on 2014-05-28
Just to let you guys know I was trying to install 10.04 Ubuntu not 14.04 because 14.04 doesn't fit on my CDs

---

### Post by kansasnoob on 2014-05-28
> **minecraftmeun5 said:**
> Just to let you guys know I was trying to install 10.04 Ubuntu not 14.04 because 14.04 doesn't fit on my CDs

In post #17 you said "I tried Lubuntu 14.04 but it froze at the Loading bootlogo":

[http://ubuntuforums.org/showthread.php?t=2226356&page=2&p=13034867#post13034867](http://ubuntuforums.org/showthread.php?t=2226356&page=2&p=13034867#post13034867)

Besides 10.04 desktop has reached EOL:

[http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/](http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/)

The 12.04.1 images will fit on a CD.

---

### Post by minecraftmeun5 on 2014-05-28
I am able to get 12.04 server edition to boot( i already had the CD). Am i able to start a desktop from a server?
EDIT: Am Not ABLE

---

### Post by Bucky Ball on 2014-05-28
No, but you can install one. Once you've installed the server version, simply,

sudo apt-get install ubuntu-desktop

All this has been explained recently. We know why you are using 10.04, but that is unwise, those reasons have also been explained.

---

### Post by minecraftmeun5 on 2014-05-28
I just realized that i am out of blank CDs. Scince there is not bios supoort for USB booting is there a way i can trick it in to booting from a USB. Or is there a way i can rewrite a CD-R CD.

---

### Post by deadflowr on 2014-05-28
> **minecraftmeun5 said:**
> I just realized that i am out of blank CDs. Scince there is not bios supoort for USB booting is there a way i can trick it in to booting from a USB. Or is there a way i can rewrite a CD-R CD.

Do you still have the 12.04 server version installed?

If so, then follow Bucky Ball's advice and install the ubuntu-desktop package.
It should install all the needed gui packages to run Ubuntu's desktop.
when it installs, you will need to reboot.
```
sudo reboot
```
(I guess maybe a logout might work, but rebooting is easier)

Since your graphics card is rather poor, you will be logging into unity-2d, by default.

---

### Post by minecraftmeun5 on 2014-05-29
Ubuntu server 12.04 was previously installed on one of the hard drives  but i am not sure which one or even if it will still be there. I can try to  boot from the different hard drives to see if it is still there. But if it is not there is there any way i can trick the bios into booting from USB.

Turns out that Ubuntu server is not on either of the hard drives and the computer is no longer booting from the Ubuntu server CD.


Not sure if this makes a difference but the Motherboard is Gigabyte GA-8IEXP Bios Version F9.

---

### Post by rosswmcgee on 2014-05-29
If it has an amd chip you can forget  14.04 lts Ubuntus period, they will not work with the drivers. Install Mint Quina instead. I spent days trying to install U 14.04 kubuntu etc.. finally Qiana was released.

---

### Post by deadflowr on 2014-05-29
> **rosswmcgee said:**
> If it has an amd chip you can forget  14.04 lts Ubuntus period, they will not work with the drivers. Install Mint Quina instead. I spent days trying to install U 14.04 kubuntu etc.. finally Qiana was released.

¿
huh?

News to me.
I guess my amd machine's are running on fantasies.

Back on-topic,
> Turns out that Ubuntu server is not on either of the hard drives and the  computer is no longer booting from the Ubuntu server CD.

Does the machine boot into any system, now?

---

### Post by QIII on 2014-05-29
Three of my machines run AMD CPUs and AMD/ATI GPUs.  My primary machine, AMD & AMD/ATI,  is Trusty -- 14.04.

Please refrain from dispensing FUD.

Thanks.

---

### Post by minecraftmeun5 on 2014-05-30
Sorry for the late reply but my Internet was being goofy but anyway my machine does not appear to boot into any system I currently have throw at it

---

### Post by Bashing-om on 2014-05-30
minecraftmeun5; Welp;

Have you to this time reviewed mörgæs' thread -  [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640) - in this respect ? // A P4 processor should run fine with any of the lighter distributions. I expect it is but a matter of the graphics card and the peripheral devices.

where there is a will there is a way

---

### Post by minecraftmeun5 on 2014-05-31
What Distro would you recommend...

---

