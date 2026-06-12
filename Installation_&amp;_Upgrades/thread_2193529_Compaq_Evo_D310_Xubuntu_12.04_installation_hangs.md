---
title: "Compaq Evo D310: Xubuntu 12.04 installation hangs"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by tim-cornelissen on 2013-12-13
Hi all,

I'm trying to revive an old Compaq Evo dekstop by installing Xubuntu on it. I created a bootable USB with Xubuntu 12.04 on it which works fine when I boot it on my laptop.
But when booting the USB from the Compaq (using PLOP boot manager to boot from usb) it gives the Xubuntu loading screen, but the bar stops moving back and forth after several seconds. I also tried booting with nomodeset enabled and the (simplified version of) the loading screen appears, after which the following error message appears:

Xubuntu 12.04
[29.290786] floppy: unknown parameter: 'allowed_drive_mask'

I tried disconnecting the floppy drive (don't need it anyway), but the same error occurs.

Hardware specs: Compaq Evo D310, pentium 4 2.40 GHz, NVidia Vanta

Any idea how to fix this? If you need more info please let me know! Thanks for your help!

Tim

---

### Post by fantab on 2013-12-13
How much RAM do you have there?

Some Info: [http://ubuntuforums.org/showthread.php?t=2143118](http://ubuntuforums.org/showthread.php?t=2143118)

---

### Post by tim-cornelissen on 2013-12-13
Thanks for the fast reply!
I knew I forgot something important in the specs ;) It has 1GB of RAM, so that shouldn't be a problem right?

I had no idea the graphics card was that ancient. But doesn't the fact that the loading screen works and the error message about the floppy suggest that this is not a problem?

---

### Post by mörgæs on 2013-12-13
Better to try Lubuntu 13.10. 
It's lighter and it fits to a CD, so there's no need for PLOP.

---

### Post by tim-cornelissen on 2013-12-13
Thanks for pointing out Lubuntu to me, I didn't know it existed! 

Unfortunately trying Lubuntu gives the same error: the loading screen appears but hangs after some time. I couldn't find how to enable nomodeset this time, but I assume it will give the same error message...
 I'm still using PLOP btw, as I don't have an empty CD available right now. Could PLOP be the issue? If so, I'll try to get my hands on an empty CD.

---

### Post by mörgæs on 2013-12-13
PLOP is an unnecessary complication. I suggest using a CD.
Did you disable the floppy drive in BIOS?

---

### Post by Topsiho on 2013-12-13
You say/think you have 1 GB of Ram, which should be enough. But ... if some of the Ram is defect, you easily could have the error that not all the necessary files for the install can be loaded into Ram: and the process will halt.

So first thing to do is checking your Ram, which is one of the items that you can choose from before installing.

Topsiho

---

### Post by fantab on 2013-12-13
If you have 1Gb of RAM then both Xubuntu and Lubuntu are an option. They are both light on System Resources, Lubuntu is lighter.
Disable Floppy in the BIOS. Can you boot with USB drive?

---

### Post by tim-cornelissen on 2013-12-15
Thanks for all your suggestions! Unfortunately, none of them worked...
- I did the memory check and it came back with no errors
- I disabled the floppy in the BIOS
- I burned Lubuntu to a CD and booted from that (no PLOP involved)
The installation (or selecting trying without installing)stills hangs after some time. With nomodeset enabled I don't get an error message this time though, it just stops loading. Any more suggestions?

---

### Post by Topsiho on 2013-12-16
Thank you for trying my suggestion and check the Ram.

I am convinced it must be your hardware, and if it isn't the Ram, it must be something else.
That something else that comes to mind is the CD reader, or the CD itself might be at fault.

Another possibility is that your .iso file is not OK. Did you check it?

If at booting you checked the CD (one of the options) and it comes out OK, than both the reader and the CD are OK, and we have to look elsewhere again. Maybe some other reader might have an idea where that elsewhere is?  :)

Topsiho

---

### Post by mörgæs on 2013-12-16
For how long did you wait before considering it a failure?

---

### Post by Topsiho on 2013-12-16
I have been thinking some. You write: "The installation (or selecting trying without installing) stills hangs after some time."
"Some time" is very vague indeed. When does the install stop: during the copying of the install files (into memory), or when the installation actually happens? In the latter case files are copied onto the hard disk, and if the hard disk is failing, the install might halt for that reason.

In Ubuntu you have a tool called schijfgereedschap (dutch, don't know the english name, but it means something like disk tool or disk utility, to check the health of your disk drive(s)). But then you should have Ubuntu up and running, chicken and egg problem.

Maybe you have an other disk ( large enough, > 8 GiB) circulating somewhere around you that you might try.

Topsiho

---

### Post by tim-cornelissen on 2013-12-17
It hangs during the loading screen, so technically, the installation hasn't even started yet. After about 1 minute, the loading dots stop moving. And I've been waiting for over 20 minutes now, so I think it is safe to assume that nothing will happen anymore.
Unfortunately, I don't have any spare harddisks lying around...

---

### Post by mörgæs on 2013-12-17
I don't think the hard disk is the problem, but the screen card. 
Have you tried the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") or [Bodhi Linux]("http://www.bodhilinux.com/")?

---

### Post by tim-cornelissen on 2013-12-17
Nope, I've only tried Mint, Xubuntu and Lubuntu normal installations so far. I'll be gone for a two weeks holiday tomorrow, so when I come back I'll give some other versions/distributions a try and let you know what happens!

---

### Post by Topsiho on 2013-12-17
OK, so it is not the HD then.

I don't know in what phase of the install the downloading of the first files starts, it might be in the beginning when some files needed are not on the CD, e.g. localisation files, if your native language is other than English (your name/alias is Dutch, so i might answer you in Dutch, but this is an English language forum :) ). For downloading a working internet connection is necessary, and when you install directly from the CD then it must be a cabled connection (I think, and some wireless cards don't work out of the box).

How is your cabled network connection? Is that OK? How do you know it is?

Topsiho

---

### Post by tim-cornelissen on 2014-01-08
Got it working! I used the alternate installer of Lubuntu, which got me up to the point where I could chose which software to install. I selected Lubuntu desktop, but this gave an error when I continued. But when I selected minimal install it worked. Only annoying thing is that I now have to install a lot of things manually, but at least it works! Thanks for all your suggestions!

---

### Post by Topsiho on 2014-01-08
Great. Congratulations.

"But when I selected minimal install it worked". Must have been something that prevented a normal install.

Well, happy computing! :)

Topsiho

---

### Post by Topsiho on 2014-01-08
According to

[http://reviews.cnet.com/desktops/hp-compaq-evo-d310/4505-3118_7-20583858.html](http://reviews.cnet.com/desktops/hp-compaq-evo-d310/4505-3118_7-20583858.html)

your computer originally was equipped with only 250 MB of Ram. As it now has 1 GB of Ram, this means that some Ram (where is my calculator) was added. A possibility is that the different (?) Ram modules don't cooperate as well as they should, you might think of timing problems. This is not a problem anymore now, but this maybe might crop out again later, and then you might consider this possibility :)

Topsiho

---

### Post by mörgæs on 2014-01-08
> **tim-cornelissen said:**
> Only annoying thing is that I now have to install a lot of things manually

No, you just have to run one command, as seen in the link.

Anyway, good that you got it working. Please promote the minimal ISO whenever a similar problem arises.

---

