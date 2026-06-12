---
title: "Ga-a-a-a! Alternate CD Install Not Working - Part III"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by Kerry Lange on 2007-02-01
Sorry for posting this again but I'm not making any progress although I've tried a few things now.

Asus P5LD2
Core 2 6600
2 GB Kingston DDR2 "Value RAM"
nVidia 8800 GTX

My first problem was with the video card. The system hangs during installation or if I try booting to the install I had before. That's still a problem but I have another one now.

Someone suggested trying the alternate CD. So I gave it a try.

A number of times I've gotten the following message early on in the install:

The CDROM drive contains a CD which cannot be used for installation. Please insert a CD...blah, blah, blah...

I double-checked the ISO and the md5 checksum checks out. I re-burnt the CD thinking that it might have introduced a problem on the CD while burning it. Two CDs later, I had the same problem. I burnt both CDs at the lowest speed my burner allows.

Taurus asked whether I'd burned the ISO or a data file. I was careful to select ISO from the Nero menu so I think that's okay.  I've also now tried burning the CD with Infra Record, an Open Source CD burning program but that CD hasn't worked any better.

I've checked my cables as well and they're secure.  I've also tried the install from another drive but that ended with the same failure.

During one of the failed installs I also got the following text overlaid on top of the screen that tells you the X server failed to load:

[17179710.776000] hdj: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

Does anyone have a suggestion?

---

### Post by jd65pl on 2007-02-01
Do you have any jmicron chips on your mbord, is your cd drive the IDE type, if so i think there is a known issue with the motherboard and you will only be able to install using edgy. [I had the same problem on a P5B]

---

### Post by Kerry Lange on 2007-02-01
> **jd65pl said:**
> Do you have any jmicron chips on your mbord,

Don't know.  I'll try to find out.

> is your cd drive the IDE type,

Yes.

> if so i think there is a known issue with the motherboard and you will only be able to install using edgy. [I had the same problem on a P5B]

Do you mean the regular Edgy CD as opposed to the alternate one?  Edgy is the version I'm trying to install.

---

### Post by jd65pl on 2007-02-01
Try the regular CD that worked for me.

---

### Post by Kerry Lange on 2007-02-01
> **jd65pl said:**
> Try the regular CD that worked for me.

Okay.  I'll do that.  However, I'm back to my original problem now.  That is that the install won't load the X server because of my new nVidia 8800.  

Is there a way for me to install from the command line of the prompt I get to after X server fails to load?

---

### Post by Sef on 2007-02-01
> Is there a way for me to install from the command line of the prompt I get to after X server fails to load?

Read [Psychocat's Nox]("http://www.psychocats.net/ubuntu/nox").

---

### Post by Kerry Lange on 2007-02-01
> **Sef said:**
> Read [Psychocat's Nox]("http://www.psychocats.net/ubuntu/nox").

That appears to be quite helpful if you've already got a working version of Ubuntu installed.  However, when I try loading my already-installed version, it hangs but not on the X-xerver failure.  It appears to hang before then.

As a result, I'm trying to re-install from the CD and that's where I have the problems.  When the CD loads, I get the X-server failure screen.

Or, when I'm trying to use the alternate CD, I get the message that I've got the wrong CD in the drive.

I really don't know where to go from here.

---

### Post by Kerry Lange on 2007-02-04
Finally!  It worked!

Thanks.  I've got Feisty working with my hardware.  I take it that the jmicron chip issue has been addressed in Feisty, as I was able to use the Alternate CD when installing Feisty.  I'd tried using the Alternate CD for Edgy without success.

So, here's what worked:

1.  Used the alternate Feisty CD to get everything installed.  At this point the X server didn't work with my nVidia 8800 card.

2.  I got the latest nVidia drivers from the nVidia site and, using Windows, saved them to a CD.

3.  I booted to Ubuntu and used the command line to install the nVidia drivers.  

4.  I mounted the CD and copied the drivers to the file system.  I could probably have run the driver utility from CD but I did it from the HDD.

5.  The drivers come with a utility to configure the X server so there was no need to manually edit the X server config file.  Before the installation utility would work, though, I had to have "libc6-dev" installed first.

6.  When I rebooted, everything came up as you'd expect!

---

### Post by jd65pl on 2007-02-04
Glad you got this one working!

---

### Post by kiaran on 2007-02-22
I'm glad to hear you were able to get Ubuntu installed with your 8800. I also have the 8800 GTS and I was unable to install Ubuntu, so I'm downloading the Fiesty version right now.

I want to follow your instructions, but I don't know how to install the nvidia drivers from the command line. I can download them and put them on a CD, but how do get to a command line to install them before the X-server error pops-up? And how do I install the drivers from the CD once I do get to a command line?

A little more help for a newbie would be muchly appreciated!

Thanks,
Kiaran

---

### Post by Kerry Lange on 2007-02-22
Hopefully the newest Feisty will support the 8800 card and you won't have to worry about any out-of-the-ordinary installation procedures.

In the event you need to install the driver separately, here goes...

You've said you have the nVidia driver burnt to a CD.  So, make sure the CD is in the drive.

Boot to your installation.  Don't worry about stopping the boot before you get the screen telling you X didn't load.  When you get to that bit just answer whatever questions it asks so you'll end up at the command line.  You probably won't have a regular command line though.

So, at that point press "Ctrl" + "Alt" "F1".  That'll get you to the command line.  You'll have to log in as the user who made the installation.

Once you're at the command line, you should be able to copy the nVidia driver from the CD to another directory where you can run it.  Maybe you can run it directly from the CD but that's not how I did it.

To copy from CD drive to a directory in your file system, you'll have to enter the following:

```
cp /media/cdrom/NVIDIA-Linux-x86-1.0-9746-pkg1.run /home/<your username>/Desktop/NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

That'll copy the driver file to your Desktop directory.

If you've got more than one CD drive, the cd drive may be "cdrom0", "cdrom1" or something like that.  To find out which drive your file is located on, you can "cd" to the drive like so:

```
cd /media/cdrom/
```

Then you can get a listing of the files there:

```
dir
```

Once you've copied the file to the destination, you can "cd" to the directory and run the installation.  nVidia instructs you to enter the following:

```
sh NVIDIA-Linux-x86-1.0-9746-pkg1.run
```

From this point on, it should all happen automatically. Then you reboot and all should be well--at least it was for me.

---

