---
title: "install ubuntu using Terminal on MAC OS 10.4.8"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by David_N_Oswald on 2007-01-30
Hello,

I apologize for perhaps a simple question, but I am new to Linux and Ubuntu.

I have downloaded the ISO image for Mac and now have Ubuntu_PowerPC_edgy mounted on my Mac desktop with a bunch of folders and files in it. I have been trying to install Ubuntu by using Terminal but am running into roadblocks, largely due to my lack of experience with Unix, Linux, and Ubuntu. I have not found step-by-step instructions for installation in the documentation (they may be there, but I have not found them) so this i why I am sending out a shout for help.

Could someone please tell me, in a clear manner, step-by-step, how to get Ubuntu installed on MacOSX. Or, alternatively, refer me to the specific location where this is listed in the Ubuntu documentation.

Thank-you, I appreciate the help.   

Regards,

-David

---

### Post by jpeddicord on 2007-01-30
You cannot install Ubuntu *inside* Mac OSX. It must be installed next to it as another operating system. You have to burn the .ISO image to a CD, and then put it in your computer and restart to boot from it. That will get the installer started.

For installation help, check out [https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC)

Be careful before installing, and make sure to backup any crucial files in case something goes wrong.

Jacob

---

### Post by moon2js on 2007-01-30
To install Ubuntu on a Mac, then you're going to have reboot with the CD in and press [some kind of button during bootup]("http://www.jacsoft.co.nz/Tech_Notes/Mac_Keys.shtml") (maybe C) to get to the Ubuntu installation. You also need to make sure the installation CD you have matches the processor in your computer. Most Macs use PowerPC and newer Macs use Intel.

You can't really install Ubuntu on OS X (or you can but it's complicated) because Ubuntu is an Operating System itself. When you install Ubuntu, you will either replace Mac OSX with Linux or you need to partition your hard drive so that you can run each independently and choose which you want at startup. *If you're new to Linux/Unix, I highly suggest you don't get rid of OS X.*

Also, Mac OS X is Unix in a way and Terminal is part of that Unix environment. (This is part of why it's complicating to install Ubuntu, a Unix-y OS, on OS X, another Unix-y OS.) You can usually run most Linux/Unix apps from within OS X.

Have you tried [googling for "install mac ubuntu"]("http://www.google.com/search?q=install+mac+ubuntu&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a")? I didn't read any of the results thoroughly, but [this post at a Mac-related website]("http://forums.macrumors.com/archive/index.php/t-148617.html") looks promising at first glance.

---

### Post by three-cushion on 2007-01-30
David:  I too am a newbie to Ubuntu. I finnally have Ubuntu working (with an anti-virus... Clamav).

I think the 1st thing to do is to burn the image you have onto a bootable CD. I rec'd the CD (called LiveCD) from Ubuntu via mail. Mine is Ver 6.06 LTS .

You can't use Mac OS X to install. 

Load your CD and boot your Mac w/ the "c" key down. This will load a copy of Ubuntu onto your Mac, but OS X won't be there.
You didn't mention Hardware... there is an Ubuntu for the PPC - chip Macs and one for the Intel - chip Macs. Be sure to have the right one.

Before installing, be sure you have TWO partitions on an internal  HD ... One for Linux and one for Paging (they call it 'swap'). BEWARE... if you let Ubuntu use the same HD where you have Mac OS X it *can* overwrite your entire system!!! So set up the partitions first OR... use <parted> in Ubuntu to do it for you.

I used iPartition to get the space reserved so I could tell Ubuntu where to set its partitions.

On the Desktop of the CD boot version, you will see an 'Install' icon. Click that and follow along.

The hardest part (for me)  is setting up the partitions. so that Ubuntu can format the volume(s) it needs.

See if this gets you started... then use the forums... I found a lot of help there...

cheers, Jim B

---

