---
title: "Odd results when checking integrity of alternate install CD"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by WebDrake on 2007-06-16
I've been trying to install Kubuntu 7.04 from the allternate CD on my Lenovo ThinkPad R61.

The installation exits with claims that packages on the disc are corrupt.  However, the md5sums are correct (for the iso, and k3b confirmed that it had been burned correctly).  In addition, when I boot the CD in my old system (a Dell laptop) and use the menu option to check the CD, it reports that it is fine.

The problem, then, appears to be not the install disc but how the ThinkPad interacts with it.  The same happens with a 6.10 alternate install disc.

I've noted various errors at boot but am not sure how to record them effectively---they vanish quickly before I can write them down.

Does anyone have any idea how to deal with this?

I'd really appreciate some help ASAP as currently, thanks to the failed installation, the system is totally broken---I can't even boot into Vista, which was pre-installed.

Thanks in advance for any help.

---

### Post by wpshooter on 2007-06-16
How old is the computer ?  Is there a possibility that the CD drive needs cleaning, i.e. dust in it.

Is the firmware of the CD drive on the latest & greatest version ?

---

### Post by WebDrake on 2007-06-16
The computer is brand new, one of the latest ThinkPad models:
[http://www.linuxinsider.com/story/57292.html](http://www.linuxinsider.com/story/57292.html)

Here's the [spec]("http://www5.pc.ibm.com/uk/products.nsf/$wwwPartNumLookup/_NA01EUK?OpenDocument").

The LiveCD won't load, as per some other forum discussions:
[http://ubuntuforums.org/showthread.php?t=474954](http://ubuntuforums.org/showthread.php?t=474954)
[http://ubuntuforums.org/showthread.php?p=2848799#post2848799](http://ubuntuforums.org/showthread.php?p=2848799#post2848799)

---

### Post by cuby on 2007-06-16
Hi, if you have a strange on-board ide/sata controler like jmicron, some weird errors from the ide drive can exist. try boot the cd from external usb drive.

---

### Post by WebDrake on 2007-06-16
> **cuby said:**
> Hi, if you have a strange on-board ide/sata controler like jmicron, some weird errors from the ide drive can exist. try boot the cd from external usb drive.

That sounds like it could be promising.  I don't have a USB CD drive---could it be done from a USB pen drive and if so how?

Thanks again,

     -- Joe

---

### Post by cuby on 2007-06-16
Hi!

you can see this thread:
[http://ubuntuforums.org/showthread.php?t=5151](http://ubuntuforums.org/showthread.php?t=5151)

If you have a case for external ide hard disk drive you can plug a ide cd/dvd ;)

---

### Post by trentend on 2007-06-16
This issue had been tormenting me, but thanks to this post I've been able to make an installation.

It turns out I have a jmicron SATA controller on my ECS KN3 SLI2 motherboard.

Does this mean I can expect problems with reading /writing to the DVD ROM? Can I expect hard drive problems?

I could not run the installer, I had to boot the live DVD (with the "xforcevesa" switch, as a consequence of my nvidia 7600GT graphics card failing to play ball).  How do I now convert the partition to LVM (no choice offered in this installer)?

Now with 7.04 AMD64 installed I cannot run an update (either through the graphical manager, nor through terminal)

ie

sudo apt-get update
sudo apt-get upgrade

fails.  Also I can't do anything to update my graphics drivers.  Is this a problem with the modern hardware, or a problem with 64bit Ubuntu, in the latest guise?

I have to say this is the worst Linux installation experience I've had in the last five years, but equally it's probably the most modern hardware I've attempted it on.  Not a good advert, I'm afraid.

So, advice please.  Will going back to 32 bit solve my problems?  I've spent 3 days searching the forums for a solution, and I'm just about stuck now.  I really wanted a brand spanking new, dedicated Ubuntu machine, with all new shiny Beryl, and to keep it clean of nasty micro$oft trojan ware (except perhaps in VM Player for my CAD software).  As it is, I can't even hurdle the install. lol.

Seriously, hoping to get to the bottom of this, and any help or experience appreciated.

---

### Post by WebDrake on 2007-06-16
> **trentend said:**
> This issue had been tormenting me, but thanks to this post I've been able to make an installation.

Can you clarify what you did to get things installed?

---

### Post by Pumalite on 2007-06-16
> **WebDrake said:**
> Can you clarify what you did to get things installed?

Also, in my opinion, even if you have a 64 bit system, you'd be better off with a 32 installation.

---

### Post by trentend on 2007-06-16
> **WebDrake said:**
> Can you clarify what you did to get things installed?

I used a plug-in USB CD-ROM drive, instead of the IDE DVD-ROM, and used xforcevesa switch to prevent autodetect of the graphics card.

This allowed me to boot into the live CD and install from there.

After the install it seems anything that involves packet management (eg updates or attempting to select the built in nvidia drivers) hangs.

I have an internet connection, and a local network connection. The machine is pointing correctly at the repositiories, but hangs after 95% (every time) checking for updates.  I really don't understand what the problem is......

---

### Post by cuby on 2007-06-17
Your ethernet connection work's ok with firefox? do wou have some dead links in the update repository? Did you try the 32 bit installation?

---

### Post by trentend on 2007-06-19
> **cuby said:**
> Your ethernet connection work's ok with firefox? do wou have some dead links in the update repository? Did you try the 32 bit installation?

Yes my ethernet connection does work (Hello, here I am!).  I don't know if I have any dead links, how do I look, and what do I do to correct them?  I have tried the 32 bit installation, but had exactly the same experience, moreover the 64 bit runs appreciably faster on my machine, and really that's what I want to use.

I have tried multiple installations of 6.10 and 7.04.  I have tried installing from the alternate iso, the desktop iso, and the server iso.  I have checked the integrity of these disks, installed, had the same failure, downloaded again, checked the integrity, burned, installed rinse and repeat.  I have done this for about four days, now.  I never achieve a better end result than the one I'm currently trying to fix.

Basically upgrade manager, and sudo apt-get update; sudo apt-get upgrade, all hang the machine.  So does any attempt to install the restricted nvidia drivers.

I would be highly appreciative on any suggestions or help.  I am desperate to get this working, and I'm pretty confident that the only way is going to be to fix this problem, as any attempt at a reinstall either fails, or leaves me back in exactly this position.

feisty 64 is blisteringly fast on this machine, but I need to be able to get security updates, install the software that I need, better utilise my graphics card so I can display correctly to my monitor (1680x1050), and generally configure my machine to be a workhorse (I will also be using vmplayer, and cad software, and doing web development, and a whole host of unusual, and in some case processor and graphics intensive work).

Help would be deeply appreciated.  Should I start a new thread, as this has wandered past the initial install difficulty into other areas?

---

### Post by Pumalite on 2007-06-19
Before you give up. Download a new iso. Do a checksum. Burn at 1x. Then try again. Torrent is better than HTTP or FTP.

---

### Post by trentend on 2007-06-19
> **Pumalite said:**
> Before you give up. Download a new iso. Do a checksum. Burn at 1x. Then try again. Torrent is better than HTTP or FTP.

Honestly, I've done that four or five times.  There is nothing wrong with the CD.

---

### Post by trentend on 2007-06-19
Day five:

Really getting extremely frustrated now. (This is a serious understatement).  I downloaded (bittorrent) all of the various iso's again (7.04: 64 desk, 32desk, 64alt, 64serv; 6.06: 64serv, 32serv). Compared the checksums. Burn't on the lowest possible speed.  Booted the CD's, checked the integrity of the disk.  Tried installation.

The best that I can possibly do is with the 64bit desktop, and with xforcevesa and noapic switches (for example if I add the nolapic switch the installation always fails somewhere in the late 50%'s with a quick beep and then back to the live CD.

With this best case installation the situation is exactly what I have previously described.  Any attempt to use the update manager, or sudo apt-get update, or the restricted drivers (nvidia) handgs the machine and stops it from working.  If I don't attempt to do any of this (or install any additional packages) the installation appears fine and all the software seems to work as expected.

if I type (in the terminal):

sudo apt-get update

the command gets to 95% and then fails with the following message:

message from syslogd@machine at time/date Machine kernel:[   262.486850]Oops 0011[2]SMP

message from syslogd@machine at time/date Machine kernel:[   262.487218]CR2 ffff8100010091b8

this is rock solid repeatable.

after this the machine will not run software correctly and fails to unmount the swap drive when trying to shutdown, requiring a hard reset.

My hardware.

ECS KN3 SL12 Extreme Motherboard (nForce 590)
500Gb SATA Western HD
4 Gb RAM
3800 AM2  Dual Core Athlon 64

Any help appreciated.  My next step is probably to buy Vista to get this thing going.  I just can't continue to lavish this level of effort in trying to get it to work.

---

### Post by Pumalite on 2007-06-19
> **trentend said:**
> Day five:

Really getting extremely frustrated now. (This is a serious understatement).  I downloaded (bittorrent) all of the various iso's again (7.04: 64 desk, 32desk, 64alt, 64serv; 6.06: 64serv, 32serv). Compared the checksums. Burn't on the lowest possible speed.  Booted the CD's, checked the integrity of the disk.  Tried installation.

The best that I can possibly do is with the 64bit desktop, and with xforcevesa and noapic switches (for example if I add the nolapic switch the installation always fails somewhere in the late 50%'s with a quick beep and then back to the live CD.

With this best case installation the situation is exactly what I have previously described.  Any attempt to use the update manager, or sudo apt-get update, or the restricted drivers (nvidia) handgs the machine and stops it from working.  If I don't attempt to do any of this (or install any additional packages) the installation appears fine and all the software seems to work as expected.

if I type (in the terminal):

sudo apt-get update

the command gets to 95% and then fails with the following message:

message from syslogd@machine at time/date Machine kernel:[   262.486850]Oops 0011[2]SMP

message from syslogd@machine at time/date Machine kernel:[   262.487218]CR2 ffff8100010091b8

this is rock solid repeatable.

after this the machine will not run software correctly and fails to unmount the swap drive when trying to shutdown, requiring a hard reset.

My hardware.

ECS KN3 SL12 Extreme Motherboard (nForce 590)
500Gb SATA Western HD
4 Gb RAM
3800 AM2  Dual Core Athlon 64

Any help appreciated.  My next step is probably to buy Vista to get this thing going.  I just can't continue to lavish this level of effort in trying to get it to work.

One more thing you could try before giving up totally is to use DBAN and then use Gparted in your SATA drive ( I'm only guessing; I dont know if it's new or you had something there before) .I've read or heard that some of this 500GB SATA drives sometimes come with pre installed software friendly to Windows only. I don't know if this is the case or if it'll work, but is worth trying it as a last resort.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by trentend on 2007-06-20
> **Pumalite said:**
> One more thing you could try before giving up totally is to use DBAN and then use  in your SATA drive ( I'm only guessing; I dont know if it's new or you had something there before) .I've read or heard that some of this 500GB SATA drives sometimes come with pre installed software friendly to Windows only. I don't know if this is the case or if it'll work, but is worth trying it as a last resort.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

It's a  brand spanking new drive (I was intending to build a machine specifically for Ubuntu).  Okay, so I understand DBAN.  I'm not understanding what I should be doing with Gparted, though.  Surely if I wipe the disk with DBAN all I need to do is run the installer (.....again.....grrrr).

Thanks for the suggestions.  You can imagine how frustrating this is for me, and I do appreciate any attempted help to get me going.

---

### Post by Pumalite on 2007-06-20
> **trentend said:**
> It's a  brand spanking new drive (I was intending to build a machine specifically for Ubuntu).  Okay, so I understand DBAN.  I'm not understanding what I should be doing with Gparted, though.  Surely if I wipe the disk with DBAN all I need to do is run the installer (.....again.....grrrr).

Thanks for the suggestions.  You can imagine how frustrating this is for me, and I do appreciate any attempted help to get me going.

If you use DBAN, is better to use Gparted afterwards and make one whole LARGE partition of the entire disk formatted ext3. Then install and use: Guided>Use Entire Disk.

---

### Post by trentend on 2007-06-20
> **Pumalite said:**
> If you use DBAN, is better to use Gparted afterwards and make one whole LARGE partition of the entire disk formatted ext3. Then install and use: Guided>Use Entire Disk.


Interesting.  The DBAN CD wont boot for me.  It gets to:

1. FD 1.44MB System Type-(00)
SYSLINUX 2.13 2004-12-14

and then sits down.  Two downloads, two burns, same CD that I can install Ubuntu from.  GParted appears to boot up into a command line environment with Grub> as the prompt.  I have no idea how to use it, but it seems to be alive and running.  Help offers a lot of command line options, but no integrated environment.  Can't seem to get to a graphical partition manager, which I assumed was the point, though.

---

### Post by Pumalite on 2007-06-20
> **trentend said:**
> Interesting.  The DBAN CD wont boot for me.  It gets to:

1. FD 1.44MB System Type-(00)
SYSLINUX 2.13 2004-12-14

and then sits down.  Two downloads, two burns, same CD that I can install Ubuntu from.  GParted appears to boot up into a command line environment with Grub> as the prompt.  I have no idea how to use it, but it seems to be alive and running.  Help offers a lot of command line options, but no integrated environment.  Can't seem to get to a graphical partition manager, which I assumed was the point, though.

You can install DBAN in a floppy or a CD. It looks like you install the version meant for a floppy into a CD. Or you have a defective CD-R drive?. It's also weird that Gparted doesn't appear with a graphical interface.

---

### Post by trentend on 2007-06-21
> **Pumalite said:**
> You can install DBAN in a floppy or a CD. It looks like you install the version meant for a floppy into a CD. Or you have a defective CD-R drive?. It's also weird that Gparted doesn't appear with a graphical interface.

From the DBAN website I chose the link for a CD install.  It came as an iso which I burned to CD. Same with Gparted.

I had been using the USB CD ROM drive which I had to use to install Ubuntu (otherwise every intall failed randomly because of the controller drivers).  When I put the DBAN CD in the IDE CD-ROM drive, it loads.

Wiping disk now, assume this will work for GParted afterwards.  Do not understand why I can boot a live CD off my USB CD-ROM drive, but not DBAN or GParted.

Computers, don't you love 'em?

---

### Post by bsmith1051 on 2007-06-26
Are you sure you don't have a bad motherboard, e.g. have you successfully run any other OS, even Windows, on it before?  Also, have you tried burning the ISO on a different burner?  In my experience, burners wear out after about 1-2 years of heavy use and produce discs that are unreliable on any other drive.

---

### Post by trentend on 2007-06-27
> **bsmith1051 said:**
> Are you sure you don't have a bad motherboard, e.g. have you successfully run any other OS, even Windows, on it before?  Also, have you tried burning the ISO on a different burner?  In my experience, burners wear out after about 1-2 years of heavy use and produce discs that are unreliable on any other drive.

I'd put a brand new drive in the machine I burned the CD on, and I've verified the disk from the boot menu.

I'm not sure about the motherboard, but why would the motherboard stop the package installation working, when the network connection is functioning?  I can understand if there is a controller issue, but not the sporadic results installing the software.

It's possible there is something wrong with the motherboard.  I'll try installing windows (if I can find a disk around here) and see what happens....

---

