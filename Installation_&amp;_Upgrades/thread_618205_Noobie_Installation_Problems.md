---
title: "Noobie Installation Problems"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by Jophiel on 2007-11-20
Hi, this is my first time trying out a Linux distribution and I thought I read somewhere that this was one of the easier distributions for first-time Linux users.  I am fairly computer savvy and built the rig I'm trying to install Ubuntu on myself.

Specs: 

2x 160GB WD SATA 3 GB/s 16MB drives (One drive is where the windows install is, and the other is for my music library.  Both are single partition drives.)
1x 80GB Samsung SATA 3 GB/s drive (I deleted the former windows partiton from this drive in the disk manager and did not format it.  This is also the drive I want to install Ubuntu on.)
AMD Athlon XP 3000+ 64 bit processor
Asus A8N SLI-Deluxe Mobo
1x PowerColor x800GT graphics card
X-fi Xtreme Music sound card
2GB (4x512MB) Corsair ValueSelect DDR 400 RAM
DVD/CDRW drive
Floppy
Viewsonic VA702b 17" monitor



Okay, so on to the troubles I'm having.  I downloaded 7.1 I grabbed the 64 bit version and wasn't sure if that was the right decision or not.

Basically I burned the ISO onto a CD, ran the CD in windows and then rebooted, changing the BIOS to load from CD before loading from an hdd.  When I selected install / run it spools the progress bar then the screen switches to a screen that flashes too quickly for me to be able to read it (like some BIOS screens) then my monitor goes black.  The computer is still on, but I have an amber light on the monitor.  It momentarily says no signal on the monitor before it goes to the black screen w/ the amber light by the way.

When I tried to verify the CD it did the exact same thing.  I tried switching around how I had the hdd's connected to the mobo and had the same issues.

Am I going horribly wrong here somewhere, ie. I should have gotten the x86 version?


Thanks for the help, I really want to try Linux for the first time, (yay for vista huh?) but am having a little trouble getting started.

Oh, and one last question, as a first time Linux user (bear in mind I understand a lot about computers and can learn quickly) is Ubuntu the best distribution for me to start with or should I maybe look into another?

---

### Post by KIAaze on 2007-11-20
Have you tried the "Start Ubuntu in safe graphics mode" option?

If this still doesn't work, maybe you should try the previous 7.04 version.
You can get it here: [http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

I am saying this because the latest ATI driver that comes by default with Ubuntu Gutsy (v7.10) doesn't work for me (display is scrambled). So I am now using v7.10, but with an older driver.
Since you also have an ATI card, it might be the cause of this problem. (altough the safe graphics mode really should work I think)

> Oh, and one last question, as a first time Linux user (bear in mind I understand a lot about computers and can learn quickly) is Ubuntu the best distribution for me to start with or should I maybe look into another?

It's definitely a good choice.
But if you have problems installing it, you could always try other easy distros like [Fedora]("http://fedoraproject.org/"), [Mandriva]("http://www.mandriva.com/") or [OpenSUSE]("http://www.opensuse.org/").

---

### Post by KIAaze on 2007-11-20
I found something interesting:
> Blank screen with some ATI hardware

      People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf. [Bug #132716]("https://bugs.launchpad.net/bugs/132716")


[http://www.ubuntu.com/getubuntu/releasenotes/710]("http://www.ubuntu.com/getubuntu/releasenotes/710")

In this case, what you should do is:
-Install using the safe graphics mode (which should work)
-Reboot from the Live-CD in safe graphics mode again (unless it works after installation, in which case you don't need to proceed ^^)
-Go to Applications->Accessories->Terminal
-Run the following commands:
```
sudo mkdir /mnt/ubuntu
sudo fdisk -l

```
Locate the partition where you installed Ubuntu. Let's say it's /dev/hdaX. (If you need help post the ouput of "sudo fdisk -l" here.)
Then run those commands:
```
sudo mount /dev/hdaX /mnt/ubuntu/
cd /mnt/ubuntu/etc/X11/
sudo cp xorg.conf xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf

```

Search for the "driver" section and add the following line into it:
```
 Option "LVDSBiosNativeMode" "false"

```
It should look like this for example:
```
Section "Device"
 Identifier "ATI Technologies Inc M24 1P [Radeon Mobility X600]"
 Driver "ati"
 BusID "PCI:1:0:0"
 Option "LVDSBiosNativeMode" "false"
EndSection

```
(identifier will probably be different for you)

-Save the file and exit gedit.
-Reboot and hope it works.

I can't give any guarantee that this will work, but the bug description is very similar to what you are facing, so it might just be the right solution.
Otherwise, you should at least try the Ubuntu Feisty v7.04 version or another distro.

---

### Post by Jophiel on 2007-11-20
Yeah, I was not able to load it in safe graphics mode, I probably should have mentioned that, so I'm going to give 7.04 a try.

Thanks for the help by the way :)

---

### Post by Jophiel on 2007-11-21
I couldn't get 7.04 to work either so I went ahead and downloaded Mandriva and got it installed and working.  It's even playing nice with Vista and Grub :)  Thanks though.

---

### Post by KIAaze on 2007-11-21
Did you use Mandriva Linux One 2008 or Mandriva Linux Free 2008 (without proprietary drivers)?

---

