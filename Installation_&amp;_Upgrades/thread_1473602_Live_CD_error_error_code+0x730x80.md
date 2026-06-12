---
title: "Live CD error: error_code+0x73/0x80"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by krzysiekgi on 2010-05-05
Hi, I have the following problem: I burn  a Cd with Ubuntu 10.04 and when I turn on the live cd pops up the  following error: error_code 0 x73/0x80. Does  anyone else have any idea how to deal with this?


Intel Celeron D 325 2533 MHz
ASRock  P4i65GV
Ram 512 MB (PC3200 DDR SDRAM)
BIOS Type AMI (06/10/2004)
Video  Card: WinFast A340 128MB

When you try to install pops up this  error: 0 work_notifysig x13/0x1b.
[COLOR=#000000]
Sorry for my English.[/COLOR]

---

### Post by tommcd on 2010-05-05
How did you "turn on the live cd"??

You have to burn an *iso image* of the CD.
You then have to set the computer's BIOS to boot from the cdrom drive as *the first boot device*.
The first thing you should always do when booting from the Ubuntu CD is to first run the option "*check disk for defects*" and let that run. If it passes without any errors, then the CD is good.
If you are burning the CD from a Windows system, you should use Iso Recorder or Infra Recorder:
 [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And be sure to burn the CD at the *slowest possible speed*.
I would suggest burning a new CD *at the slowest possible speed* using ISo Recorder or Infra Recorder. Then boot from the CD and check the CD for defects. Then try to install Ubuntu.
Write back if you need more help.

And welcome to the Ubuntu forums!!

---

### Post by krzysiekgi on 2010-05-06
Thank you for your welcome.

I burned the CD  using Brasero. He recorded a speed of 2x. I checked the  checksum, and it turned out that he agreed, so the picture is well  recorded. When trying to select the "check media in order to find  mistakes" again comes to the same error: error_code 0 x73/0x80. I thought she  might try to install ubuntu with alternate installation. We'll see what happens.

Edit :

However, an  alternative installation did not help. This time  by selecting "install" installation stops at "verifying network  equipment." I waited about 3 minutes, then jumped  me as always. But this  time I was armed with pictures of the screen. Sorry for the quality.  

[IMG]http://img153.imageshack.us/i/error80.jpg/[/IMG]
[[IMG]http://img153.imageshack.us/img153/866/error80.jpg[/IMG]]("http://img153.imageshack.us/i/error80.jpg/")

and
[U][[IMG]http://img130.imageshack.us/img130/3636/error81.jpg[/IMG]](http://img130.imageshack.us/i/error81.jpg/)

[/U]

[IMG]http://img130.imageshack.us/i/error81.jpg/[/IMG]

---

### Post by krzysiekgi on 2010-05-07
Does no  one is able to help me? I guess I will leave with ubuntu 10.04. :(

---

### Post by tommcd on 2010-05-07
> **krzysiekgi said:**
> 
 When trying to select the "check media in order to find  mistakes" again comes to the same error: error_code 0 x73/0x80.
Do you mean that, when you booted the Ubuntu live CD, you ran the option "*check disc for defects*, and you got that error: error_code 0 x73/0x80??
If this is what you mean, then this should not happen. It should run through a check of every file on the CD and report if there are any errors. It takes a minute or 2 to run.
The first thing you need to do is make sure you have a valid CD. Try burning a new CD and see if you can then run the "check CD for defects" check when you boot the live (or alternate) CD.
You might also try downloading the Ubuntu iso from a different a different mirror, just to rule out a bad download.

---

### Post by krzysiekgi on 2010-05-07
Yes, when I select "check errors Live CD"  pops up this error. The same is true if I select "test". When you choose  to install it receives this error: 0 work_notifysig x13/0x1b. The cd is ok, because the checksums are correct,  and I installed Ubuntu 10.04 on a notebook from it.

---

### Post by krzysiekgi on 2010-05-07
bump . . .

---

### Post by krzysiekgi on 2010-05-07
bump ;(

---

### Post by tommcd on 2010-05-07
> **krzysiekgi said:**
> Yes, when I select "check errors Live CD"  pops up this error. The same is true if I select "test". When you choose  to install it receives this error: 0 work_notifysig x13/0x1b. The cd is ok, because the checksums are correct,  and I installed Ubuntu 10.04 on a notebook from it.
The CD can not be considered "ok" if the *check disc for defects* check will not pass. It is possible for the CD md5sum to pass even though 1 or more files on the CD may be corrupt. I have had this happen to me.
 If many files on the CD are corrupt, then the md5sum check will not pass. If only 1 or 2 (or possibly a few more) files are corrupt, the md5sum may still pass even though a few files on the CD are bad.
Note that it is possible to install *buntu from a CD with 1 bad file. I managed to install Lubuntu beta on my laptop even though 1 file was corrupt. I would not recommend this though.
I have tried googleing: **ubuntu install +error_code+0x73/0x80**
There is one report that says it *may* be video related:
[http://art.ubuntuforums.org/showthread.php?t=1392395](http://art.ubuntuforums.org/showthread.php?t=1392395)
If this is the case, then installing from the alternate (text based) install CD should avoid this, since it sidesteps graphics related problems.
Another report suggests the CD may be bad:
[http://newyork.ubuntuforums.org/showthread.php?t=1471681](http://newyork.ubuntuforums.org/showthread.php?t=1471681)
I have not found any other info on this error. I have tried searching to try to help you.
 I would strongly suggest burning another CD. If you are burning the CD from Ubuntu, you may want to try installing Gnomebaker, or even K3B, if Brasero is unable to create a valid CD. Note that installing K3B will require you to install all of the KDE dependencies; but K3B is the best CD burning app in the linux world imo.
I burn all my linux install CDs using **cdrecord** from the terminal on Slackware, so I can not say how reliable Brasero or Gnomebaker are for burning iso images these days.
 When I did try burning iso image CDs using Gnomebaker or Brasero from Ubuntu in the past, I would sometimes get a bad burn. I have rarely if ever, had a bad burn with K3B on Slackware.

---

### Post by krzysiekgi on 2010-05-07
Thank  you very much for your reply. I will try to record a CD GnomeBaker.

---

### Post by krzysiekgi on 2010-05-07
Hi,

I suggested to  [http://art.ubuntuforums.org/showthread.php?t=1392395](http://art.ubuntuforums.org/showthread.php?t=1392395), where I read that  someone has set that image was reproduced from the motherboard.
Since I am "green" in these cases entered in the  bios, I went to Advanced> and then came to the option of "chipsed  configuration" and was set by default AGP> PCI?> Motherboard. So I switched to Motherboard> PCI?> AGP. Then I chose the option to save & reset. It turns out that the LED on the monitor is orange all the  time, which is at rest. I hear a single sound  which means that everything is ok, but the screen is idle. By this, I can not enter the BIOS and restore default settings.  Please, quick help.

Paul

---

### Post by krzysiekgi on 2010-05-07
Okay, reset the bios on the  motherboard via a jumper CLRCMOS. But it still did  not solve my problem. Now try to record a CD  using GnomeBaker.

Paul

---

### Post by krzysiekgi on 2010-05-08
Hi,
But the problem does not lie with the CD. The image burnt on Verbatim disc, using the previously  mentioned programs. And again there is the same  problem. The alternative version of the error  occurs during the "check network hardware", and the desktop version when  selecting "Live CD mode" and "Checking CD read errors." I have no idea of what to do next, and much depends on my  ubuntu 10.04. I would add that currently I  am using Ubuntu 8.04 and is all about testing for downloaded from the  internet version 9.04 and the same error in version 10.04.

Paul

---

### Post by krzysiekgi on 2010-05-08
Hi,
I already know the cause of the problem. It  is a AGP card. When it was disconnected ubuntu  10.04 installed without any problem. I've updated  it, turned on the NVIDIA proprietary driver, then switched back to the  AGP card. And what is it? Again  the same error. Has anyone any idea? This may be a BIOS fault?

Paul

---

### Post by tommcd on 2010-05-08
> **krzysiekgi said:**
> 
I already know the cause of the problem. It  is a AGP card. When it was disconnected ubuntu  10.04 installed without any problem. I've updated  it, turned on the NVIDIA proprietary driver, then switched back to the  AGP card. And what is it? Again  the same error. Has anyone any idea? This may be a BIOS fault?

So your motherboard has integrated video, plus you have a nvidia AGP card, is that correct?
What nvidia card is this?
As for the BIOS, I would think that if you are using the AGP card, then that BIOS option should be set to AGP.
If you install Ubuntu 8.04, or use the 8.04 live CD with the nvidia card, do you get this error? Is it possible the nvidia card is defective? 

Since you had previously said you successfully installed Ubuntu 10.04 on your laptop, can you at least boot up the 10.04 live CD on the laptop and run the option "*check disc for defects*" on the laptop. If the disc check passes on the laptop, then at least we know that the CD is good. If the disc check fails on the laptop, then the CD is unreliable. 
If I can find out anything else about this error, I will post back.

---

### Post by krzysiekgi on 2010-05-08
Hi,
Yes, the motherboard has integrated graphics, plus my AGP  card. It is a GeForce 5200 (Leadtek WinFast A340).  Currently, the BIOS is set to the order of the  AGP> PCI> Motherboard graphics. At  installation time switched on motherboard> AGP> PCI and  installation went without any problems. When  switched on the motherboard graphics could "check for errors in the  media" and showed that the CD is fine. I tested  Ubuntu 8.04 Live CD and everything works, like the older versions. The problems begin with the version 9.04 and later. But when I switch on the motherboard graphics Live CD and  installation is in order. The graphics card is  certainly functional. I think that there is a  conflict between Ubuntu 10.04 and my graphics card. This may create problems bios?

Paul

---

### Post by tommcd on 2010-05-08
> **krzysiekgi said:**
>  I think that there is a  conflict between Ubuntu 10.04 and my graphics card. This may create problems bios?

Ubuntu will not cause any problems with your BIOS. An improper BIOS setting could cause problems for Ubuntu though, or for any OS for that matter.
Since you verified that the CD is good, and since you can install Ubuntu 10.04 with the integrated graphics, try this:
1. Install Ubuntu 10.04 using the integrated graphics. Then boot into the installed Ubuntu using the integrated graphics.
2. Edit the /etc/default/grub file. Find the line:
```
GRUB_CMDLINE_LINUX=""
```
 In between the quotes "" at the end of the line:
```
GRUB_CMDLINE_LINUX=""
```
Put **nomodeset** in between the quotes so it looks like this:
```
GRUB_CMDLINE_LINUX="nomodeset"
```
Save and exit the file. Then run:
```
sudo update-grub
```
Reference for editing /etc/default/grub: [https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29) 
Then install the nvidia AGP card and then try booting into the installed Ubuntu using the nvidia card.
This guy in post #2 of this thread reports that his nvidia 5200 card would only boot with the live CD with the nomodeset  option:
[http://ubuntuforums.org/showthread.php?t=1442625](http://ubuntuforums.org/showthread.php?t=1442625)
Then (assuming you can get to the Ubuntu desktop with the nvidia card) install the nvidia-173 driver:
```

sudo apt-get install nvidia-173 nvidia-settings
sudo nvidia-xconfig

```
Then reboot.
The nvidia-173 driver supports your 5200:
[http://packages.ubuntu.com/lucid/nvidia-173](http://packages.ubuntu.com/lucid/nvidia-173)
I really hope this gets us somewhere!

---

### Post by krzysiekgi on 2010-05-08
Hi,

I used to advise You. I installed ubuntu  from scratch, then edited the grub file, added the "nomodeset", write  down the file and upgraded grub. I put the  graphics card to the pc. Switched to the AGP>  PCI> Motherboard Graphics and reset the pc. It  turns out that once you receive the same error. Ubuntu  and my card is probably interfere with each other. I do not know what to do.

Paul

---

### Post by krzysiekgi on 2010-05-08
bump

---

### Post by krzysiekgi on 2010-05-09
bump

---

### Post by tommcd on 2010-05-09
> **krzysiekgi said:**
> 
I used to advise You. I installed ubuntu  from scratch, then edited the grub file, added the "nomodeset", write  down the file and upgraded grub. I put the  graphics card to the pc. Switched to the AGP>  PCI> Motherboard Graphics and reset the pc. It  turns out that once you receive the same error. Ubuntu  and my card is probably interfere with each other. I do not know what to do.

Crap!!!

Ok, it seems that **nomodeset** has been rendered obsolete by recent Ubuntu updates. I was hoping it work for you from a fresh install of 10.04.
If you see post #6 from the thread I linked to in my last post:
[http://ubuntuforums.org/showthread.php?t=1442625](http://ubuntuforums.org/showthread.php?t=1442625)
it seems that the correct format is:
```
yourchipsetname.modeset=0
```
Do you know what motherboard your computer has? And what chipset does the motherboard use?
What make and model computer do you have? If you built the computer yourself, what motherboard is in the computer?
If you do not know the chipset on your motherboard, run the command: ```
lspci
``` in the terminal and post the output here.
With the chipset of your motherboard we can (hopefully) edit the /etc/default grub file, and put the correct option in the line **GRUB_CMDLINE_LINUX=""** that will get your Ubuntu 10.04 to boot with the nvidia 5200.

---

### Post by krzysiekgi on 2010-05-10
Hi,
> Crap!!! 
I was hoping it work for You from a fresh install of 10.04.Yes, I started to  work with the new installation. You may have misunderstood me, because i  use the translator.

The motherboard is a model for ASRock  P4i65GV
Chipset:                Intel 865

Paul

---

### Post by tommcd on 2010-05-11
> **krzysiekgi said:**
> 
Yes, I started to  work with the new installation. You may have misunderstood me, because i  use the translator.
The motherboard is a model for ASRock  P4i65GV
Chipset:                Intel 865

So based on the info from post #6 in the thread I linked to in my last post:
[http://ubuntuforums.org/showthread.php?t=1442625](http://ubuntuforums.org/showthread.php?t=1442625)
You would edit the **GRUB_CMDLINE_LINUX=""** line of /etc/default/ grub and place: **i865.modeset=0** in between the quotes at the end of that line, so it looks like this:
```
GRUB_CMDLINE_LINUX="i865.modeset=0"
```
Then try to reboot into the installed Ubuntu 10.04 with the nvidia card and see if it will work.
This is of course after installing 10.04 using the integrated graphics as I discussed in my last post.
If this does not work I am not sure what else to try.

---

### Post by krzysiekgi on 2010-05-12
Hi,

This code does not help. Again the same  error pops up, and once jumped out a bug with the game port. I do not know if it's not my fault, because my motherboard is  equipped with two bridges: Northbridge: Intel Morgan Hill i865GV and  Southbridge: Intel 82801EB ICH5. And I gave only  one. Maybe something will help you exactly how to  print parts of my pc.

Processor Intel  Celeron D 325, 2533 MHz
Motherboard: ASRock  P4i65GV
Ram: 1x 512mb
Bios:  Ami
Video Card: WinFast A340
Graphics Chipset: GeForce FX 5200
HDD:  WDC WD800BB-00FJA0 (74 GB)
The AGI (Women AGP)  graphics card is inserted.
The PCI slot I have  inserted a card with TV tuner, is this: AVerMedia Super 007.

Paul

---

### Post by tommcd on 2010-05-12
> **krzysiekgi said:**
> 
This code does not help. Again the same  error pops up, and once jumped out a bug with the game port.
I don't know if this will help, but if you are getting errors about the game port then I would try disabling the game port in the BIOS.
> **krzysiekgi said:**
> 
 I do not know if it's not my fault, because my motherboard is  equipped with two bridges: Northbridge: Intel Morgan Hill i865GV and  Southbridge: Intel 82801EB ICH5. And I gave only  one. Maybe something will help you exactly how to  print parts of my pc.

Try using i865GV in between the quotes at the end of the line: GRUB_CMDLINE_LINUX="" in the /etc/default/grub file.
Also, post the output of **lspci** in the terminal.

Your motherboard has integrated Intel graphics:
[http://www.asrock.com/MB/overview.asp?Model=P4i65GV](http://www.asrock.com/MB/overview.asp?Model=P4i65GV)

I am about out of ideas here.
There is a possibly relevant bug report on Launchpad that mentions your motherboard way down on post #73 here:
[https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/553745](https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/553745)
I did not see a solution or a workaround anywhere on that page though.

---

