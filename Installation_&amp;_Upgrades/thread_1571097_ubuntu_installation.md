---
title: "ubuntu installation"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by jagannathahm on 2010-09-09
My desktop  configuration is ASrock intel 845 gv chipset 2.4GHZ P4 processor witj Nvidia geforce fx 5500 AgP video card,  22inch LG lCD monitor, Floppy disk drive + Samsung DVD writer

I have been using Ubuntu Hardy heron with out any problems configuring nvidia graphics card as well

THought of upgrading to Lucid lynx 10.04 Downloaded i386 32 bit  image via torrents and burn to CD 

CD boots via bios, goes into the install or live CD display.  However if I chose either Install or live CD,  system stays at the ubuntu startup mode for several minutes and goes into 

"BUsy box v 13.3 initramfs unable to find a medium containing live CD system"

I also tried using the Wubi installer via the CD from windows system and after going through the initial process  shows up error "see attachments"

However, if I mount image from windows and use WUBI installation is OK ;  all systems are OK; can configure nvidia driver etc.   However, cannot use DVD writer to open any CD   No entry in fstab or device entry in /dev e.f scd0 or sr0 etc 


I have tried upgrading hardy heron  to 10.04 using alternate CD every thing is OK except for the CD writer problem mentioned above.

Same odd behavior I see even if I try the server edition

Can nay one suggest any solution since it is obvious to me that driver for CDrom is missing in the installation image  and that is the cause of this problem

Thanks
Jagannatha

---

### Post by jagannathahm on 2010-09-16
I am really surprised that there seems to be no solution for this situation. Would the developers from Ubuntu look into this please

---

### Post by mörgæs on 2010-09-17
I guess that your error message was
"Unable to find a medium containing a live file system"

Try googling this, and you will get lots of advice.

---

### Post by jagannathahm on 2010-09-17
unable to find live medium is not the issue.  I have raised multiple issues in my thread.  I have googled  for all related issues and have found no solution so far.  That is why it is time ubuntu developers look into this

Thanks for the reply

---

### Post by tommcd on 2010-09-18
When you boot the 10.04 live CD, did you first run the option "**check disc for defects**" to verify that the CD is valid?
This is *always* the first thing you should do when booting an Ubuntu install CD.

---

### Post by dirghrabadia on 2010-09-18
Did you initially install Hardy via WUBI? If so, then I don't think you would be able to upgrade from Hardy to Lucid via CD/DVD, unless you want a separate installation for Lucid. 

> When you boot the 10.04 live CD, did you first run the option "**check disc for defects**" to verify that the CD is valid?
This is *always* the first thing you should do when booting an Ubuntu install CD.

+1.

---

### Post by jagannathahm on 2010-09-18
I installed hardy via cd drive 


regarding checking cd defects,  the system does not proceed to that stage It gives the initramfs error I mentioned in my first thread

---

### Post by jagannathahm on 2010-09-18
also to add pressing esc button while live cd is trying to open  shows up "process 252 *GLIB WARNING* ** GLib - getpwuid_r():  failed due to unknown user id (0) 

Does this ring a bell?

---

### Post by jagannathahm on 2010-09-18
I downloaded ubuntu-8.04.4-desktop-i386 again burnt the cd tried the system  via cd.  No problems with getting into live cd

I also downloaded ubuntu-10.10-beta-desktop-i386 same experiment same problem as with Lucid lynx.

Why this problem.  It cant be hardware problems can it be

---

### Post by jagannathahm on 2010-09-19
OK another experiment.  Tested linux mint.  same problem  seems like a hardware problem with asrock p4i45 mother board.  Cant  be anything else. Has any one else experienced this.  Problems reported with intel 845 mobo i thought could be problems with display.  Can ubuntu developers look into this and suggest suitable solutions

---

### Post by mörgæs on 2010-09-19
> **jagannathahm said:**
> Can ubuntu developers look into this and suggest suitable solutions


No, the developers are probably not even reading this thread. 

There are well-known problems running 10.04 on Intel 845 chipsets:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) . Though you are talking of CD drivers and not the display I would not bother with 10.04, if I were you.

Have you tried installing 9.10?

---

### Post by jagannathahm on 2010-09-19
OK I will try to my system 8.04 seems to work best

---

### Post by tommcd on 2010-09-19
> **jagannathahm said:**
> 
regarding checking cd defects,  the system does not proceed to that stage It gives the initramfs error I mentioned in my first thread
When you first boot the Ubuntu live CD, you should get to the first screen shot from this link:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Do you see that screen when you boot Ubuntu? If so, then run the option to check the CD for defects to verify that the CD is good.

You could also try to install 10.04 from the alternate CD. This is a text based install CD that should help you avoid any graphics problems that you may experience with the live CD. Then after you install Ubuntu you can install the nvidia driver for your nvidia 5500.

---

### Post by jagannathahm on 2010-09-20
well I tried 9.10  same problem As I said earlier to my config hardy is the best

Thanks for all the replies

---

### Post by tommcd on 2010-09-20
You could try installing Ubuntu 10.04 from the alternate install CD. This is a text based install CD that should help you avoid any graphics related problems during the installation. After you install 10.04 you could then install the nvidia driver for your FX 5500.

---

### Post by jagannathahm on 2010-09-21
Hi Tommcd,

My trubles are with cd drivers.  I can install via wubi not directly from CD or USB.  Have also configured nvidia drivers.  That way system IS OK.  Only  my dvd rw is unusable since device scd0 is missing pointing to cdrom driver error.  Same experience when installed via alternate cd

---

### Post by metalman2007 on 2010-09-22
Try googling all you want. I found nothing as well. I can tell you that I installed Ubuntu successfully on 2 computers in my home. However, I can't install it on my Gateway 838GM. Nothing wrong with the CD/DVD drive and nothing wrong with the disks as they worked fine on other machines. I think the issue is the fact that my hard drive is a serial ata and the cd/dvd drives are not. No matter what I do in the bios settings, nothing. So I came to the conclusion that Linux cannot simply be installed on my machine. I would rather have it as a primary os so wubi or virtualbox is not an option for me. Too bad, these are awesome os in which I would rather have than Windows any day. Has anyone else gone through this?

---

### Post by jagannathahm on 2010-09-22
hi metalman2007,

I agree most problems faced with Linux distros  are hardware related.  Developers should address this issue.  Any OS should broadly work with hitherto available hardware ; this probably achieved through development of generic drivers or alternatively developers should issue release notes detailing which hardware will not work in their released OS.  I do not know how to put this across generally to developers not just Ubuntu but to other linux distros as well.  Hope someone from the forum will advise how this can be done

---

### Post by tommcd on 2010-09-23
> **metalman2007 said:**
> I think the issue is the fact that my hard drive is a serial ata and the cd/dvd drives are not. No matter what I do in the bios settings, nothing. ...
The fact that the hard drive is SATA and the CDROM drive is IDE is not the problem. Both of my desktop computers have SATA hard drives and IDE CDROM drives and I have never had a problem installing any linux distro on them.

You should check the jumper setting on the IDE CDROM drive though. Set it to master or slave according to it's position on the IDE cable. Don't rely on cable select. Trying a new IDE cable can also help in troubleshooting problematic IDE drives.
If Ubuntu has trouble seeing your IDE CDROM drive, you could also try booting the install CD with the boot option: **all_generic_ide**.

---

### Post by jagannathahm on 2010-09-23
Thanks tommcd for your suggestion.  I tried all_generic_ide option both on gui and text based installers. Text based installation stops at " no common cdrom driver found load from floppy disk"  Gui gives the "inittramfs" error I mentioned in my first thread.   Why should an installation cd not detect cdrom drives.

Is there a source for cdrom drivers for ubuntu  I can download onto a floppy  and load the driver when required?

I also tried Mandriva 2010 spring free installation on my system  Curiously this also stops at "no common cdrom drivers found"

That is why my question  I asked in my previous post I hope we find a solution

---

### Post by metalman2007 on 2010-09-23
Right again [jagannathahm]("http://ubuntuforums.org/member.php?u=1142890"), some machines are just not a perfect fit for any of these linux distros. I've tried linux mint, ubuntu, fedora, mandriva, opensuse, & opensolaris, and to no avail. It's my machine. tommcd there's something different about your machine in which you've had success. Think about it, what makes Microsoft windows xp so special that It can get installed into my machine that easily. I would love to think that I can place any linux distro cd into my drive and install it successfully just like I did with my other workstations. I think it's worth while for these programmers to look into. Hell, I'll even volunteer to send them my machine if I have to. This is killing me, I love Linux LOL.

---

### Post by perspectoff on 2010-09-23
Rarely do I find a user that I recommend that he buy paid support.

This user needs paid support from someone. Very demanding customers ought to be charged a lot, too.

---

### Post by perspectoff on 2010-09-23
> **mörgæs said:**
> No, the developers are probably not even reading this thread. 

There are well-known problems running 10.04 on Intel 845 chipsets:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) . Though you are talking of CD drivers and not the display I would not bother with 10.04, if I were you.

Have you tried installing 9.10?

I run two computers with the 845 chipset. The problem was with the Intel integrated graphics, and I finally found the workaround so now they both run Lucid fine.

This guy has nVidia graphics, though (and the forums have tweaks for that, as well).

I have never, ever had a computer within the past 11 years whose CD drive was not recognized by the Debian (/ Ubuntu) installer. Rare situation, indeed.

---

### Post by metalman2007 on 2010-09-23
Yeah, I have two CD/DVD rom drives and 1 is set as master and the other set to slave. Previously, I've also swapped out with another CD rom drive just to rule that out and sure enough same error.

---

### Post by jagannathahm on 2010-09-23
> **perspectoff said:**
> I run two computers with the 845 chipset. The problem was with the Intel integrated graphics, and I finally found the workaround so now they both run Lucid fine.

This guy has nVidia graphics, though (and the forums have tweaks for that, as well).

I have never, ever had a computer within the past 11 years whose CD drive was not recognized by the Debian (/ Ubuntu) installer. Rare situation, indeed.
Well I do not have any problems with graphics.  Only I have to first install lucid via wubi using onboard graphics controller configure nvidia blacklist some modules load some modules and come back to graphics card display.. Problems with cdrom driver only

---

### Post by jagannathahm on 2010-09-23
> **perspectoff said:**
> I run two computers with the 845 chipset. The problem was with the Intel integrated graphics, and I finally found the workaround so now they both run Lucid fine.

This guy has nVidia graphics, though (and the forums have tweaks for that, as well).

I have never, ever had a computer within the past 11 years whose CD drive was not recognized by the Debian (/ Ubuntu) installer. Rare situation, indeed.
Please let me know how u installed lucid on your comps with 845 chipset.  via cd or wubi or usb is your system reading cds have u come up with any workaround

---

### Post by jagannathahm on 2010-09-24
I just came across another distro "lucid puppy"  here is the link  [http://easylinuxcds.com/blog/?p=4030](http://easylinuxcds.com/blog/?p=4030)

I have not tried it yet will do soon may be you can have a go

---

### Post by jagannathahm on 2010-09-24
> **metalman2007 said:**
> Yeah, I have two CD/DVD rom drives and 1 is set as master and the other set to slave. Previously, I've also swapped out with another CD rom drive just to rule that out and sure enough same error.
I just came across another distro "lucid puppy"  here is the link  [http://easylinuxcds.com/blog/?p=4030](http://easylinuxcds.com/blog/?p=4030)

I have not tried it yet will do soon may be you can have a go

---

### Post by grahammechanical on 2010-09-24
I used the upgrade path to go to 10.04 but I also download the 10.4 ISO image and burned it to CD. When I tested it as a live CD the screen that allows you to choose a language did not appear and the process just froze.

I assumed it was due to the CD not being large enough for the ISO image. I had previously installed from CD (DVDs actually) given free by Linux magazines. Earlier versions of Ubuntu might have had a smaller ISO image or there could be something with the 10.4 ISO image. That is, if more than one person is having a problem. For 10.10 I intend to use a DVD disc and not a CD.

Regards

---

### Post by metalman2007 on 2010-09-24
Hi [grahammechanical]("http://ubuntuforums.org/member.php?u=1087323")

I don't think the physical media DVD or CD would make a difference. I tried both and to no avail. I also tried 10.10 and I thought to myself "Yes! this could be it" but no luck. I've installed Ubuntu on everyone else's computer at home. We have 4 but It won't install on mine LOL. Mind you, I've used the same CDs and tested every linux disto out there with the same error message.

---

### Post by jagannathahm on 2010-09-24
> **jagannathahm said:**
> I just came across another distro "lucid puppy"  here is the link  [http://easylinuxcds.com/blog/?p=4030](http://easylinuxcds.com/blog/?p=4030)

I have not tried it yet will do soon may be you can have a go
I tried both lucid puppy (lupu-510)  and ubuntu-10.04-dvd-i386 (4.3GB) same problem

---

### Post by ssulaco on 2010-09-25
> **jagannathahm said:**
> 
"BUsy box v 13.3 initramfs unable to find a medium containing live CD system"

Take a look at this...
[https://answers.launchpad.net/ubuntu/+question/123044](https://answers.launchpad.net/ubuntu/+question/123044)

---

### Post by jagannathahm on 2010-09-25
> **ssulaco said:**
> Take a look at this...
[https://answers.launchpad.net/ubuntu/+question/123044](https://answers.launchpad.net/ubuntu/+question/123044)
well I have gone through these steps But have not found a solution

---

### Post by metalman2007 on 2010-09-25
I just wanted to update and share another attempt and experience with everyone as per another recommendation. It was recommended to download a software called IMGBurn. IGMBurn is a free ISO image burner that will allow for you to burn a CD image at the slowest speed possible. The theory is that if you burn the image onto the CD at the slowest speed possible, that would get the liveCD to work. Well, guess what? That didn't work either. Now that's not to say that this will not work for you guys, it just didn't work for me.

---

### Post by ssulaco on 2010-09-26
> **metalman2007 said:**
>  IGMBurn is a free ISO image burner that will allow for you to burn a CD image at the slowest speed possible.(Windows)Imgburn:[http://majorgeeks.com/ImgBurn_d4870.html](http://majorgeeks.com/ImgBurn_d4870.html)
+1

jagannathahm,Have you tried the Alternate "torrent"

[http://releases.ubuntu.com/releases/10.04/](http://releases.ubuntu.com/releases/10.04/)

---

### Post by metalman2007 on 2010-09-26
Hi [ssulaco]("http://ubuntuforums.org/member.php?u=540748")

That's one thing I didn't try. I'm downloading it now and will update everyone on the status. Also as an FYI I did check the MD5sum of the last burn and the hash codes were right on target so unfortunately that didn't work either.

---

### Post by metalman2007 on 2010-09-26
Ok, I did try using the alternate Ubuntu install and just when I thought it was going to happen, at the point of partitioning and formatting, it gets to 33% and does nothing. So, in conclusion, I think the problem has to do with my Sata Hard drive. Maybe I have to find one that's specifically made for a linux installation. As an FYI, my hard drive is a Maxtor 200gb Sata.

---

### Post by mörgæs on 2010-09-26
A SATA drive should not be a problem. How much memory is on your machine?

---

### Post by jagannathahm on 2010-09-26
> **ssulaco said:**
> (Windows)Imgburn:[http://majorgeeks.com/ImgBurn_d4870.html](http://majorgeeks.com/ImgBurn_d4870.html)
+1

jagannathahm,Have you tried the Alternate "torrent"

[http://releases.ubuntu.com/releases/10.04/](http://releases.ubuntu.com/releases/10.04/)
I used "alternate" cd to upgrade from 8.04 to 10.04.  Upgrade was successful.  But 10.04 did not show cdrom drives on system.  I did not know that it can be used for fresh install Can it be Have I understood you correctly.  Metalman2007 post seems to suggest that it is possible.

---

### Post by jagannathahm on 2010-09-27
just to inform I downloaded debian lenny cd1 and tried installing on my system. Installlation was perfect and cdrom was detected in my system Kernel is 2.6.26-2

Of course I have other things to learn about debian system  seems very different from ubuntu   What is the difference between lucid and lenny kernels?

---

### Post by ssulaco on 2010-09-27
> **jagannathahm said:**
>  Installlation was perfect and cdrom was detected in my system Kernel is 2.6.26-2
 What is the difference between lucid and lenny kernels?
Glad you got it going......as far as the kernel difference,not sure.

> **jagannathahm said:**
>  I did not know that it can be used for fresh install Can it be Have I understood you correctly.  Metalman2007 post seems to suggest that it is possible.
yes

---

### Post by mörgæs on 2010-09-27
If in doubt, always go for a fresh install.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by metalman2007 on 2010-09-27
> **mörgæs said:**
> A SATA drive should not be a problem. How much memory is on your machine?

This is what I have:

Intel® Pentium® 4 630 with Hyper-Threading Technology 
[LIST]
[*]3.0 GHz
[*]800 MHz FSB
[*]2 MB cache on die Level 2
[/LIST]
For memory, I used to have:

512 MB PC3200 DDR SDRAM
Two 256 MB memory modules

But I upgraded to 1GB of memory

---

### Post by jagannathahm on 2010-09-28
> **ssulaco said:**
> Glad you got it going......as far as the kernel difference,not sure.


yes
I also checked out ubuntu 10.04.1 alternate cd installation This also does not read cd drive and have to abort installation. There is  some problem for detecting ide cdrom drives in the lucid kernel  I hope ubuntu developers provide generic drivers for all ide sata etc devices in subsequent releases.  Some body please advise how I can pass on this request to ubuntu developers

---

### Post by mörgæs on 2010-09-28
> **metalman2007 said:**
> This is what I have:

Intel® Pentium® 4 630 with Hyper-Threading Technology 
[LIST]
[*]3.0 GHz
[*]800 MHz FSB
[*]2 MB cache on die Level 2
[/LIST]
For memory, I used to have:

512 MB PC3200 DDR SDRAM
Two 256 MB memory modules

But I upgraded to 1GB of memory

This is fine hardware for Ubuntu.

---

### Post by metalman2007 on 2010-09-28
Hi everyone, you're not going to believe this. I successfully installed Ubuntu and over came the "unable to find medium containing a live file system" issue. Here's what I did; I have an NVIDIA graphic card that I added to my system last year. This morning I decided, what the heck and removed it. When I booted my pc up and it read to CD to my surprise, Walla, Ubuntu is now installed. I think there must be some pre-checking in Ubuntu that freezes at the point when the extra hardware is installed. Then it triggers the infamous error  "unable to find medium containing a live file system". Of course we're all going nuts because we're playing around with CD burns, CD drives, mdsum5. So if this happens to be your situation, and you do have a graphic card that you added, remove it and use the original onboard video card. Let me know if this works, if it does, I may want to share this with the developers. 

Kind Regards,

---

### Post by jagannathahm on 2010-09-28
> **metalman2007 said:**
> Hi everyone, you're not going to believe this. I successfully installed Ubuntu and over came the "unable to find medium containing a live file system" issue. Here's what I did; I have an NVIDIA graphic card that I added to my system last year. This morning I decided, what the heck and removed it. When I booted my pc up and it read to CD to my surprise, Walla, Ubuntu is now installed. I think there must be some pre-checking in Ubuntu that freezes at the point when the extra hardware is installed. Then it triggers the infamous error  "unable to find medium containing a live file system". Of course we're all going nuts because we're playing around with CD burns, CD drives, mdsum5. So if this happens to be your situation, and you do have a graphic card that you added, remove it and use the original onboard video card. Let me know if this works, if it does, I may want to share this with the developers. 

Kind Regards,
wow!!! thats great news I also have an nvidia card  will try your method.   Is the system reading cd drives?   Did you put back graphic card and test the system

---

### Post by jagannathahm on 2010-09-28
> **jagannathahm said:**
> wow!!! thats great news I also have an nvidia card  will try your method.   Is the system reading cd drives?   Did you put back graphic card and test the system
I tried your method. did not work with lucid lynx.   I would like to share my experience with hardy heron installation

My system is asrock p4i45gv (intel) mobo , with 750MB ddr1RAM +  NVIDIA GeForce FX 5500 (256MB VRAM) with LG  22inch LCD monitor.  I could successfully open live cd with ubuntu 8.04 and install.  Reboot into ubuntu opened desktop while display was on nvidia graphic card and card was not configured.  OS could be used as such with out any further display configuration.  Configuration net work ,  management of packages with synaptic were good.  It was also possible to configure nvidia card and launch compiz.   

This performance is just like windows where you can install base system irrespective of graphics card  and system can be customized as per need

unfortunately with 10.04, could not boot from live cd ; it was possible to install only via wubi.  CD drive was not recognized.  However,  other aspects of OS e.g configure graphics card, package management via synaptic were excellent.

I believe it will be great if ubuntu could restore the hardy heron configuration in its subsequent releases and thus enable users to install the base system irrespective of graphics card status and use.  Later OS can be customized as per need

I hope developers will look into this suggestion

---

### Post by metalman2007 on 2010-09-29
Here's what I don't get. After I pulled the card out it recognized the CD and let me do the installation. At lease I finally had Ubuntu. I was excited until I put the card back in and then that's when I was having problems. My machine just wouldn't boot up into Ubuntu so I took the card back out and downloaded and installed the Nvidia drivers but to no avail, same problem. The other problem too is that I have a yamaha sound midi card that I use to connect my keyboard to, that wasn't recognized by Ubuntu either. It took me the whole day trying to get Ubuntu to recognize the card but no matter what I tired, I ran into problems. So back to square 1. At least getting Ubuntu was half the battle. I just don't have time to continue playing around with it.

---

### Post by mörgæs on 2010-09-29
> **metalman2007 said:**
> Here's what I don't get. After I pulled the card out it recognized the CD and let me do the installation. At lease I finally had Ubuntu. I was excited until I put the card back in and then that's when I was having problems. My machine just wouldn't boot up into Ubuntu so I took the card back out and downloaded and installed the Nvidia drivers but to no avail, same problem. The other problem too is that I have a yamaha sound midi card that I use to connect my keyboard to, that wasn't recognized by Ubuntu either. It took me the whole day trying to get Ubuntu to recognize the card but no matter what I tired, I ran into problems. So back to square 1. At least getting Ubuntu was half the battle. I just don't have time to continue playing around with it.

I have lost track of what you have tried and what the results were (and you have probably tried more than written here). 

Please give a short bullet list of your experiments, and then I will see if I can give some advice.

Let's wait with the sound card for now.

---

### Post by metalman2007 on 2010-09-29
> **mörgæs said:**
> I have lost track of what you have tried and what the results were (and you have probably tried more than written here). 

Please give a short bullet list of your experiments, and then I will see if I can give some advice.

Let's wait with the sound card for now.


Fair enough [mörgæs]("http://ubuntuforums.org/member.php?u=939075") as I know you're being very helpful and I appreciate it. Here's how it initially went down:

1. First I tried to install Ubuntu from the liveCD. Keep in mind my Nvidia 6200 graphics card is already in the machine.

2. I kept on getting the infamous cannot find medium containing a live system (something like that).

3. Assuming that this meant bad CD or bad Burn. I started to experiment with everything and anything possible related to that.

4. Of course I knew better because there's nothing wrong with my cd/dvd drives or the media that I burnt the CDs on so I decided to pull out the graphics card from the tower.

5. I was able to perform not only a successful install of Ubuntu but I experimented with the other distros and installed them without a problem.

6. I put the graphics card back into the tower, booted up the pc, and started to run into the same issues. I couldn't boot into Ubuntu. I pull out the card again and everything runs fine. 

7. the only area where I'm stuck at is determining which one of the linux drivers I should use for my Geforce Nvidia 6200A graphics card. I tried a couple but was unsuccessful. The problems occur when I put the card back into the pc. I did everything possible as far as the bios is concerned and nothing. 

Thank you my friend for responding.

---

### Post by mörgæs on 2010-09-29
You are welcome. Soon it is your turn to answer posts in the forum...

Since you have not talked about releases, I guess everything is done using 10.04. How does the machine work with 9.10 and/or 10.10 (beta)?

---

### Post by metalman2007 on 2010-09-29
> **mörgæs said:**
> You are welcome. Soon it is your turn to answer posts in the forum...

Since you have not talked about releases, I guess everything is done using 10.04. How does the machine work with 9.10 and/or 10.10 (beta)?

LOL. I appreciate that. Hey, if I can solve my issue, I wouldn't mind sharing this everyone. I used the latest and greatest versions of the linux distros. Ubuntu 10.04, Linux Mint, etc... It somewhere within the linux code for new installations, there's something glitchy with reading systems hardware (if I'm making any sense).

---

### Post by mörgæs on 2010-09-29
> **metalman2007 said:**
> I used the latest and greatest versions of the linux distros.

That is a dangerous assumption. Latest is by no means greatest - for example in this thread, Jagannathahm had most luck with 8.04.

---

### Post by metalman2007 on 2010-09-29
> **mörgæs said:**
> That is a dangerous assumption. Latest is by no means greatest - for example in this thread, Jagannathahm had most luck with 8.04.

I can try 8.0.4 but what happens if I want to go to 10.04?

---

### Post by jagannathahm on 2010-09-29
> **metalman2007 said:**
> I can try 8.0.4 but what happens if I want to go to 10.04?
Hi Metalman 2007,

If you have successfully installed 10.04 and only nvidia is the problem,   I suggest the following :


install nvidia 96 + nvidia 96 kernel source 2.6.32-21-generic +nvidia-96-modaliases+ nvidia settingsdkms using synaptic manager ( this was for my nvidia card  check what is applicable to you)

blacklist agp and intel_agp by adding blacklist agp (change as appliable to your system)
blacklist intel_agp in /etc/modprobe.d/blacklist.conf using gksudo gedit /etc/modprobe.d/blacklist.conf

add load nvidia modules using  sudo gedit /etc/modules

reboot into nvidia monitor

---

### Post by metalman2007 on 2010-09-30
> **jagannathahm said:**
> Hi Metalman 2007,

If you have successfully installed 10.04 and only nvidia is the problem,   I suggest the following :


install nvidia 96 + nvidia 96 kernel source 2.6.32-21-generic +nvidia-96-modaliases+ nvidia settingsdkms using synaptic manager ( this was for my nvidia card  check what is applicable to you)

blacklist agp and intel_agp by adding blacklist agp (change as appliable to your system)
blacklist intel_agp in /etc/modprobe.d/blacklist.conf using gksudo gedit /etc/modprobe.d/blacklist.conf

add load nvidia modules using  sudo gedit /etc/modules

reboot into nvidia monitor

Thanks my friend. I'm going to give that a try and will update you later.

---

### Post by ssulaco on 2010-09-30
> **metalman2007 said:**
> I can try 8.0.4 but what happens if I want to go to 10.04?
8.04 and 10.04 are LTS.. you can upgrade LTS to LTS
[https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS)


8.04.4(LTS) is solid.,and will be supported until april 2011 (desktop)...by april,Lucid will have matured even more and the upgrade should be painless.since you can upgrade LTS to LTS.....if Hardy works well for you,you can wait until april to decide to upgrade to Lucid.if upgrade fails,reinstall,and hope the issue with Nvidia is resolved...I tend to agree with the old saying "you dont pick the distro,your hardware does":)

> **mörgæs said:**
> That is a dangerous assumption. Latest is by no means greatest - for example in this thread, Jagannathahm had most luck with 8.04.
agreed...

---

### Post by jagannathahm on 2010-10-02
> **ssulaco said:**
> 8.04 and 10.04 are LTS.. you can upgrade LTS to LTS
[https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS)


8.04.4(LTS) is solid.,and will be supported until april 2011 (desktop)...by april,Lucid will have matured even more and the upgrade should be painless.since you can upgrade LTS to LTS.....if Hardy works well for you,you can wait until april to decide to upgrade to Lucid.if upgrade fails,reinstall,and hope the issue with Nvidia is resolved...I tend to agree with the old saying "you dont pick the distro,your hardware does":)


agreed...
just a clarification.  If I am happy with 8.04 , I can continue with 8.04 forever without really worrying about support until I find another good release. Isnt it

---

### Post by mörgæs on 2010-10-02
Technically yes, but don't use a release longer than it is supported. It will be a security threat.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

