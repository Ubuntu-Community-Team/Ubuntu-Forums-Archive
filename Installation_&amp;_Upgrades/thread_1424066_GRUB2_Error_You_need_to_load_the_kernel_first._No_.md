---
title: "GRUB2: Error: You need to load the kernel first. No Solutions."
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Mgamerz on 2010-03-07
Hi, I've been using Ubuntu since 7.10 Gutsy Gibbon. I only recently fully switched to Linux OS's, and Ubuntu is now my primary. I currently have 9.10 installed. **CURRENTLY** I also have Backtrack 4, and Fedora 12 (Ugh!).
**Previously**, I thought something was wrong with my my filesystem in Ubuntu 9.10, and after an upgrade of the linux kernel, I started to get _*Error: You need to load the Kernel First.*_ That's where my problems started. I had upgraded to 9.10 from 9.04 and I still had Grub Legacy, so I went through hoops to try and get it to work, but eventually everything just kind of broke, and I completely wiped off my partitions on it and started fresh installs of all 3. 
And now that the new linux kernel is released, 2.6.31-20 generic (I think... That's what the highest number on a file I can find in /boot is)
I went through a few more hoops and ladders and tried to get it to work, but to no avail. 
I've looked the internet for a solution to this and tried just about everything but there is no unified answer, and I've seen on Launchpad there are alot of bugs that are classified as 'Fixed', but the problem still remains.
I took out the 'quiet splash' part in the GRUB2 line for the newest kernel and it didn't do anything. It only changed it to "Error: Couldn't find file".
This is the top two kernels (Main and Recovery for the new, and Main and Recovery for the previous working one) 
> ### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set ab19e2f0-6d9a-483d-ae72-cef850ef02e3
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ab19e2f0-6d9a-483d-ae72-cef850ef02e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set ab19e2f0-6d9a-483d-ae72-cef850ef02e3
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=ab19e2f0-6d9a-483d-ae72-cef850ef02e3 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set ab19e2f0-6d9a-483d-ae72-cef850ef02e3
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ab19e2f0-6d9a-483d-ae72-cef850ef02e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set ab19e2f0-6d9a-483d-ae72-cef850ef02e3
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=ab19e2f0-6d9a-483d-ae72-cef850ef02e3 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}Mainly I just really hate grub2. Karmic seems to be kind of... a Vista. It just doesn't seem like it was finished.

Has anyone else had this problem? And does anyone know how to fix it? 
It's only one of the many problems Ubuntu has been giving me....

---

### Post by saejin on 2010-03-07
I am seeing a strange problem booting since I upgraded to version 2.6.31-20
The system hangs on booting.  I restart the system and about 1 out of 4 times it boots.
It seems to be a GRUB2 compatibility problem with how it finds the boot image.
It hangs after the version is selected (and now hangs with 2.6.31-16 as well) after the echo of app-armor.  Happy to work with anyone to dig deeper....
I am trying to turn on the -x  and -v scripting option to learn more, but am having no luck....

---

### Post by drcmcs on 2010-03-17
I just took the updates to load the new changes to the kernel 2.6.21.30 and get the same problem.  As this is out of my league, I fell back to the prior kernel.  I have the Ubuntu 9.10 netbook remix.

---

### Post by karthick ayyapillai on 2010-03-17
> **saejin said:**
> I am seeing a strange problem booting since I upgraded to version 2.6.31-20
The system hangs on booting.  I restart the system and about 1
 out of 4 times it boots.
It seems to be a GRUB2 compatibility problem with how it finds the boot image.
It hangs after the version is selected (and now hangs with 2.6.31-16 as well) after the echo of app-armor.  Happy to work with anyone to dig deeper....
 Hi
I am also facing the same issue with the update for grub from the repository. I am using 2.6.31-20. After the update am able to boot but the problem is when i run the command sudo upgrade-grub in the terminal i get a strange error with permission denied . I have even tried with the root privileges i get the same error . If any one knows the solution please post . Thanks in advance.

---

### Post by PavelMan on 2010-03-18
Same here. I have installed Ubuntu through wubi, so it sits on my windows partition. After an update on Mar 17th, it now says that I "need to load the kernel first". 

Previous rernel (initrd.img-2.6.31-19-generic) loads just fine.
I looked at the menu settings -- they seem to be identical for both -19 and -20 (see below). It is just that one boots, and the other one does not. All "vlm-img" files seem to be there...

menuentry "Ubuntu, Linux 2.6.31-20-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a0bca050bca022b0
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a0bca050bca022b0
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}

---

### Post by RodoBabbins on 2010-03-18
Noticed this issues as well when the March 17th update, restarted the computer and getting the "need to load the kernel first" error.
 
Was able to repair it with this bit of info (working for me since installed with wubi inside windows)
 
> **drs305 said:**
> Based on the information you have provided, take a look at this fix to a bug in wubi 9.10:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)
 
Please let us know if this fixed the problem.

---

### Post by tasuki on 2010-03-19
I have the same problem, guys!

Except... my problem is a lot worse, because I've just deleted all the other kernels to save space. Ooops.

Is it possible to install one of the old kernels to the system from outside of the system? I'm on a live cd now.

PS: Obviously, I normally try the new kernel before deleting the old ones, but this time I must have forgotten to do that.

---

### Post by tpoche on 2010-03-20
Having the same trouble on my laptop as well.  Installed Ubuntu 9.10 from Windows using Wubi and everything worked fine at the start.  When trying to upgrade the kernel from  "Ubuntu, Linux 2.6.31-14-generic" to  "Ubuntu, Linux 2.6.31-20-generic" I receive the same error message instructing me to load the kernel first.  I have been scouring the internet for solutions to this problem and the only attempt at a solution was found in this post:

>                      Originally Posted by **drs305**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8986775#post8986775")                 
                 [I]Based on the information you have provided, take a look at this fix to a bug in wubi 9.10:
[http://sourceforge.net/apps/mediawik...lems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")
 
Please let us know if this fixed the problem.[/I]
I have attempted this fix on my machine with no success.  Here is a paste of my grub.cfg pertinent sections:

```

menuentry "Ubuntu, Linux 2.6.31-20-generic" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7a30c64730c60a59
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7a30c64730c60a59
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}

```Similarly to other posters on this thread, at least from my point of view the two OS entries seem virtually identical with no obvious problems...  My "Ubuntu, Linux 2.6.31-14-generic" installation still boots just fine as well as my Windows XP, however, I still would like to get to the bottom of this issue.  Any help would be greatly appreciated as it seems that there are many users encountering the same issues.

---

### Post by myp2132 on 2010-04-29
I have the same problem, however it's with build 2.6.31-21.

---

### Post by linbo on 2010-05-01
Me too!  I'm not familiar enough with the underpinnings of disks and file locations to debug this.  Sadly all the documentation assumes one knows what a grub is and how it relates to the kernel.

My best version is 
Linux 2.6.31.14-generic

I was fine on 31-20, then when I updated to 31-21 both of these versions failed with the same "load the kernel first" message

Unfortunately 31-14 isn't great, something screwed up my video card and things are pretty odd looking; I hesitate to "fix" this in case of conflicts when the newer versions start working.

Any advice appreciated!

---

### Post by JedMeister on 2010-05-24
This might be a bit late as I imagine many have just moved on to 10.04 but for those of you that haven't and any others who just want to fix 9.10 please read on...

I too encountered this error on 9.10 after a kernel upgrade (to -19) and I foolishly removed the old kernels without testing. Mine is NOT a Wubi install either (its dual boot XP with 9.10 installed to a ext4 partition).

Not sure if it'll work for others but I found that for some reason Grub2 gets it wrong. In the .cfg it counts the first partition as 0 rather than 1 so its one out. 

In mine:
```
set root=(hd0,6)
```
but Linux is on sda7 so I changed it to
```
set root=(hd0,7)
```
and it booted fine!

I edited my /boot/grub/grub.cfg from a live cd but you should only need to edit the boot entry in grub itself (while booting). Once your desktop loads, update the kernel (I used Synaptic but obviously CLI or Update Manager are fine) and you should be good to go. Installing a new kernel will trigger grub to update (and fix) grub.cfg.
Worked for me anyway. :)

---

### Post by Mgamerz on 2010-06-08
Sorry I never replied back to this, but the hard drive that Karmic is still on is dying (270 bad sectors!!!), so I just disconnected it completely. I don't think that really had anything to do with it loading though. I could get it to boot, but I think it might have mounted the ext4 as ext3 cause there were some serioussss problems. I have a server on another computer now and it runs lucid with grub2 and ext4, so far I have had no problems. Although today I just an update-grub...

---

### Post by radicalx on 2010-06-25
> **JedMeister said:**
> This might be a bit late as I imagine many have just moved on to 10.04 but for those of you that haven't and any others who just want to fix 9.10 please read on...

I too encountered this error on 9.10 after a kernel upgrade (to -19) and I foolishly removed the old kernels without testing. Mine is NOT a Wubi install either (its dual boot XP with 9.10 installed to a ext4 partition).

Not sure if it'll work for others but I found that for some reason Grub2 gets it wrong. In the .cfg it counts the first partition as 0 rather than 1 so its one out. 

In mine:
```
set root=(hd0,6)
```but Linux is on sda7 so I changed it to
```
set root=(hd0,7)
```and it booted fine!


 
hi guys,

same problem over here....i still do get the "you need to load kernel first" message when booting my mac over usb (with linux 10.04 iso file and grub2 on it) via rEFIt. when it comes to grub2 bootloader screen, i choose option "a" an it says this stupid thing...


can you tell me where your posted code within the grub.cfg file is located? i can't find anything similar to this within my .cfg file....



thanks 4 help x)

---

### Post by darkod on 2010-06-25
> **radicalx said:**
> i still do get the "you need to load kernel first" message when booting my mac over usb (with linux 10.04 iso file and grub2 on it) via rEFIt. 

ISO file? You don't have it installed yet?
The discussion here is about a hdd installation of ubuntu, not booting in live mode from cd/usb.
I'm not sure why it would give that error if you are really only trying to boot in live mode.

---

### Post by rajbptl on 2010-08-09
I have the same problem, however it's with build 2.6.31-22.
my previous kernel 2.6.31-14  is working fine which i didn't deleted after updating to the present. But I want to know a solution to load the updated kernel , Can any one please help me as I am new to Linux

---

### Post by JedMeister on 2010-08-11
> **rajbptl said:**
> I have the same problem, however it's with build 2.6.31-22.
my previous kernel 2.6.31-14  is working fine which i didn't deleted after updating to the present. But I want to know a solution to load the updated kernel , Can any one please help me as I am new to Linux

Have you tried the solution I posted above?

---

### Post by Camilia on 2010-09-20
> **JedMeister said:**
> Have you tried the solution I posted above?
I tried set root=(hd0,6) set root=(hd0,7)and got bash: syntax error near unexpected token `('. I tried set root=hd06 I tried set root=hd0,6 and nothing happened.

---

### Post by drs305 on 2010-09-20
> **Camilia said:**
> I tried set root=(hd0,6) set root=(hd0,7)and got bash: syntax error near unexpected token `('. I tried set root=hd06 I tried set root=hd0,6 and nothing happened.

Camilla,

Is your Ubuntu install on sda6 or sda7? That is not a common partition to install it on although it could be there. If you don't know which partition it is on, you can type "ls" at the grub prompt and it will show you which drives (hdX) and partitions (hdX,Y) it sees.

---

### Post by JedMeister on 2010-09-22
> **Camilia said:**
> I tried set root=(hd0,6) set root=(hd0,7)and got bash: syntax error near unexpected token `('. I tried set root=hd06 I tried set root=hd0,6 and nothing happened.
Although I said that it should work from Grub on boot up, perhaps not? As I stated above, my Linux install was sda7 and manually editing the line in the grub config file to *set root=(hd0,7)* did the trick for me (all I did was change the '6' that was there to a '7' - everything else was left exactly the same). The file to edit is /boot/grub/grub.cfg To edit it I booted from a LiveCD and mounted the filesystem. I think I've updated the kernel since my original post on this thread but I definitely haven't had the same problem again. I put it down to a specific issue that has since been resolved. 

I'd definitely consider drs305's suggestion to check which partition your Linux install lives on (perhaps you don't even have an sda6 or sda7?

Beyond that I'm not sure what suggestions to offer you sorry.:confused:

---

### Post by dino99 on 2010-09-25
> **Camilia said:**
> I tried set root=(hd0,6) set root=(hd0,7)and got bash: syntax error near unexpected token `('. I tried set root=hd06 I tried set root=hd0,6 and nothing happened.

[COLOR="Blue"]bash: syntax error near unexpected token `('[/COLOR]

got the same error on my end, replacing () by [] did the trick

---

### Post by Mgamerz on 2010-09-27
I hate to point this out, but Windows got it right when they had a bootloader compared to linux. Linux is a nightmare with bootloaders and kernel versions.

---

### Post by JedMeister on 2010-09-28
> **Mgamerz said:**
> I hate to point this out, but Windows got it right when they had a bootloader compared to linux. Linux is a nightmare with bootloaders and kernel versions.Thanks for your opinion but I guess it depends on how you look at it really. A few points to consider:

1) Linux kernel and bootloader have come a long way IMO. For the kernel, hardware vendors fall over themselves to support Win OS, whereas for Linux much of it has had to be reverse engineered or begged and borrowed, or written from scratch by clever people with minimal vendor support (I know there are exceptions). Because of their market share, to some degree Win dictate the 'standard' and there is a lot of interplay and agreement forged between hardware vendors and MS. Linux doesn't have that luxury. Because of the breadth of hardware, Linux devs can never check ever iteration against every hardware configuration. In fairness neither can MS but because of vendor support and agreement, Win still has a significant advantage in this regard.

2) Linux bootloader is much more powerful and flexible than Win bootloader so by nature it will be more complex. With greater complexity comes greater opportunity for bugs to creep in. Can Win bootloader boot another (no-Win) OS? Can Win bootloader boot from an ISO? Can the Win bootloader be relatively easily customised including changing the wording of boot options, adding a custom background or change font colour? Can Win bootloader be 'skinned' with a graphical bootloader screen (BURG)? No to all those questions AFAIK. I know some of these are relatively minor (aesthetic) points and not pivotal to the function of a bootloader but I still think they're relevant.

3) (Sort of related to 2) I'm sure that if Linux made a simpler Win style bootloader (ie just booted Linux, minimal recovery and customisation options) then it would be more reliable. But besides the fact that it would be counter productive (many, if not most Linux users have Win/Lin dual boot) it would not go down well with the Linux community IMO. Ability to apply end user or distro customisations is one of the fundamental features of Linux.

4) Despite all the things going for Win bootloader it still has its share of issues (although in fairness I have had little to do with Vista/7 bootloader - but I have read about issues on many a forum). After a number of years working on/with Win (mostly XP) I can assure you that there is/are many a Win system with bootloader issues (although in fairness probably not as many as Linux proportionately).

If you also factor in that Linux is free and is quite fragmented (all the different distros) I think overall, in balance it is incredibly reliable, not to mention powerful and customisable (is that even a word?) Obviously those factors may not be compelling enough for you or others to use Linux, but that's ok, you/they can continue to use Win! A win-win situation so to speak! :)

---

### Post by ibbuntu on 2011-10-09
Thanks! You just saved me a very long evening reinstalling Ubuntu from scratch.

---

### Post by oldos2er on 2011-10-09
Back to sleep, closed.

---

