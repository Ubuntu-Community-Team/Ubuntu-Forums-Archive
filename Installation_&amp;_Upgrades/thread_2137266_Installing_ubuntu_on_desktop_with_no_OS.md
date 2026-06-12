---
title: "Installing ubuntu on desktop with no OS"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by JustASimpleGuy on 2013-04-20
Hi,

I'm trying to install ubuntu on a desktop with a clean hard drive. I went to [http://www.ubuntu.com/](http://www.ubuntu.com/) -> [http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop) -> [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) -> [http://www.ubuntu.com/download/desktop/thank-you?release=lts&bits=32&distro=desktop&status=zeroc](http://www.ubuntu.com/download/desktop/thank-you?release=lts&bits=32&distro=desktop&status=zeroc) and the resulting DL is this file on my hard drive: ubuntu-12.04.2-desktop-i386.iso

I then use InfraRecorder to brun the image to a DVD-RW. The DVD that has these folders:

.disk boot casper dists install isolinux pics pool pressed

and these files:

autorun.inf md5sum.txt README.diskdefines wubi.exe

Seems to me this is a wubi install and requires an OS on the target desktop. When I insert the DVD into the target desktop and after powering up and posting, it just sits there with a blank screen and the cursor in the upper left hand corner.

And yes, I've been in BIOS and my drives are in the proper boot priority. I also tried burning the imake with ImgBurn, which I've used in the past to burn various Windows install DVDs, including slipstreaming SPs, ACHI & RAID drivers.

Any help is appreciated.

---

### Post by ibjsb4 on 2013-04-20
A WUBI install requires Windows be installed.  Go here and download.

[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by Karlchen on 2013-04-20
Hello, JustASimpleGuy.

No, there is no such thing as a special Wubi ISO image download file. The normal ISO image file will bring along wubi.exe, too. If you boot from the DVD Wubi will be ignored and the normal Ubuntu 12.04.2 (12.04 service pack 2) live system will come up.
If this does not work on the desktop machine which you tried to boot from the live system, try to boot the machine where you burnt the DVD from the DVD. If it works there then the DVD is all right. No need to be afraid of causing any damage to the Windows system on that machine. The live system will not touch your installed harddisk unless you tell it to do so.

When trying to boot the desktop machine where you want to install Ubuntu 12.04.2 from the DVD hit the spacebar. This should bring up a menu giving you the choice to add "nomodset" to the start parameters. Depending on the hardware specifications of the machine, you may have to launch the live system in a special way.

Without having learnt any technical specifications about the future Ubuntu machine it is more or less impossible to give any good piece of advice, though.
Therefore, the general rule applies: Follow the [installation instructions](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support) carefully.

Kind regards,
Karl

---

### Post by pfeiffep on 2013-04-20
I believe one of these 2 links will provide the DL for a direct install?

32 bit     [http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest](http://www.ubuntu.com/start-download?distro=desktop&bits=32&release=latest)
64 bit     [http://www.ubuntu.com/start-download?distro=desktop&bits=64&release=latest](http://www.ubuntu.com/start-download?distro=desktop&bits=64&release=latest)

---

### Post by JustASimpleGuy on 2013-04-20
Thanks idjsb4. I'll try precise-dvd-i386.iso in [http://cdimage.ubuntu.com/precise/dvd/current/](http://cdimage.ubuntu.com/precise/dvd/current/)

---

### Post by JustASimpleGuy on 2013-04-20
Understand. I'm looking for an install akin to a Windows install CD. No existing OS required. As far as I can determine, the desktop CD is only good for a machine with an OS already installed. I'm going to give precise a try.

By the way, the box I'm trying to install on is an ASUS P5B Deluxe MB with BIOS (AMI) version 1101, Intel C2D E6400, 2x1 GB G.Skill PC6400 HZ sticks, WD 500GB HD.

---

### Post by pfeiffep on 2013-04-20
> **JustASimpleGuy said:**
> Understand. I'm looking for an install akin to a Windows install CD. No existing OS required. As far as I can determine, the desktop CD is only good for a machine with an OS already installed. I'm going to give precise a try.

By the way, the box I'm trying to install on is an ASUS P5B Deluxe MB with BIOS (AMI) version 1101, Intel C2D E6400, 2x1 GB G.Skill PC6400 HZ sticks, WD 500GB HD.

The live CD / DVD / USB install disk enables you to boot and try the OS, and install to a hdd. They provide alternatives for partitioning a hard drive, afaik they all should work on a virgin drive. Is the drive recognized by BIOS?

---

### Post by JustASimpleGuy on 2013-04-20
Yup, the drive is recognized in BIOS. I can insert a Windows XP Pro CD into it, and it prepares to do a Windows install. However nothing happens with the burned ubuntu iso DL. I've tried burning with both InfraRecorder and ImgBurn. I'm certain ImgBurn works and I know how to use it as I've used it in the past to slipstream service packs and ACHI & Raid drivers onto a CD with an XP image. Worked like a charm.

---

### Post by pfeiffep on 2013-04-20
So can you boot the cd with the pc you used to create it? Possibly the newly created cd is somehow defective.

---

### Post by robertmax1980 on 2013-04-20
i am in trouble.i have two os in my sony vio linux or window 7 home basic i want to format my laptop but my window bootable CD is not working bec i have already another operating system i did not use linux ever how can i remove linux then i will install window again... i call Linux customer care they are saying you have to pay for technical support...any suggestion will be appreciated.....

---

### Post by pfeiffep on 2013-04-20
> **robertmax1980 said:**
> i am in trouble.i have two os in my sony vio linux or window 7 home basic i want to format my laptop but my window bootable CD is not working bec i have already another operating system i did not use linux ever how can i remove linux then i will install window again... i call Linux customer care they are saying you have to pay for technical support...any suggestion will be appreciated.....
I respectfully suggest that you create your own thread in this [forum]("http://ubuntuforums.org/forumdisplay.php?f=331") 

Answers to help you will not be co-mingled with answers to help this OP

---

### Post by JustASimpleGuy on 2013-04-20
I'm fairly certain the CD is good. The ubuntu trial/install window comes up on the desktop I used to create the CD.

I'm trying something. I put the hard drive with Windows XP back in my other box, along with the new HD. I'll boot up and see if I can do something with the CD after I get into Windows.

---

### Post by dave2001 on 2013-04-20
> **JustASimpleGuy said:**
> I'm fairly certain the CD is good. The ubuntu trial/install window comes up on the desktop I used to create the CD.

I'm trying something. I put the hard drive with Windows XP back in my other box, along with the new HD. I'll boot up and see if I can do something with the CD after I get into Windows.

Before using a live/install CD you have burnt from ISO to actually make a fresh installation of Ubuntu, I'd recommend the following: Check the MD5sum of the CD you have made. This will make sure that ALL of the information on the CD is exactly as it should be. Small file corruptions can occur in large downloads fairly easily. It could even cause the CD to work fine on one computer, and not another.

Here is a link for the md5sums of the various precise releases: [http://releases.ubuntu.com/precise/MD5SUMS](http://releases.ubuntu.com/precise/MD5SUMS)

---

### Post by JustASimpleGuy on 2013-04-20
Thanks Dave, I'll check it out. Somehow in playing with this I seem to have corrupted something in my Windows environment. Not sure if it's my graphics driver or BIOS. Going to reflash my BIOS (I have a DOS bootable flash drive with AFUDOS and my favored BIOS) and reinstall Windows, update chipset, drivers, etc...

Oh well, it's a cold and damp day here in Rochester. Guess I'll be spending more time doing this than anticipated. Funny thing is I decided to give ubuntu a try because I got a new Raedon (HD7770) for [EMAIL="SETI@HOME"]SETI@HOME[/EMAIL] GPU processing, however the AMD drivers for that card no longer support OpenCL for Windows XP. so BOINC doesn't recognize the GPU. Doh!!!

---

### Post by JustASimpleGuy on 2013-04-21
Well, after several rounds of trial & error I got it installed. I had to boot up in Windows and use wubi, including boot help. I had a second hard drive installed and I installed on it, creating a root, swap and home partition. I then shutdown and pulled the hard drive with my Windows installation, as I'm going to use that in another box I have sitting around.

I can now boot directly into ubuntu on power up and I've also got the latest software updates. All is well!!

Now I just have to figure out how to install software in linux. Basically a driver for my Raedon HD7770 and SETI@HOME BOINC. Found some stuff for that and I'll be tackling it as soon as I finish this post!

---

