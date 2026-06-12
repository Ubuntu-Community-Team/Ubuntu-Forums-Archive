---
title: "grub-probe: error: cannot find a device for /."
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by SchneiderIS on 2009-12-22
I am installing Mythbuntu 9.10 on an AppleTV and when entering the following command I get an error.

[FONT="Courier New"][COLOR="Blue"]sudo sed -i -e "s/^# kopt=root=UUID=.* ro$/& processor.max_cstate=2/" /atvdrive/boot/grub/menu.lst 
sudo update-grub[/COLOR][/FONT]

The error that I get is:

[FONT="Courier New"][COLOR="blue"]grub-probe: error: cannot find a device for /.[/COLOR][/FONT]

Does anyone have any idea what this error is about?

---

### Post by SchneiderIS on 2009-12-23
Anyone have any ideas?

---

### Post by SchneiderIS on 2010-01-15
Still no takers?

---

### Post by Leppie on 2010-01-15
> **SchneiderIS said:**
> [FONT="Courier New"][COLOR="Blue"]sudo sed -i -e "s/^# kopt=root=UUID=.* ro$/& processor.max_cstate=2/" /atvdrive/boot/grub/menu.lst 
sudo update-grub[/COLOR][/FONT]
i don't know what the first line does, unfortunately i'm not familiar with sed...
however, karmic (9.10) ships with grub2 as opposed to grub legacy. grub2 doesn't have menu.lst and AFAIK doesn't use kopt to pass options to the kernel (i use kernel options without any trailing statement)

what is it exactly you are trying to achieve?

---

### Post by SchneiderIS on 2010-01-15
This is where my newbism comes in.  I am trying to load Mythbuntu 9.10 (Ubuntu at the core) onto an AppleTV.  The problem is that GRUB2 is not supported in the EFI process that was working with 8.04.  So in the installation I selected not to load the boot loader but it appears to me that it has.  From other posts this process was recommended but there is no response on that forum.  I have been trying to figure out why this does not work (I did try it with the install of the boot loader with the exact same results.

So, perhaps what I would like to do, as it would appear GRUB2 is in fact installed, is remove GRUB2 and install the prior version so that the boot manager from my ATV-bootstick will work.

---

### Post by Leppie on 2010-01-15
to remove all grub instances and install grub legacy do the following:
```
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub
```

---

### Post by kansasnoob on 2010-01-15
Just purging packages and installing legacy grub will get you to boot but you'll end up with both legacy grub and grub2 files in the /boot/grub directory. Anyway you can achieve a truly clean install of legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

### Post by Leppie on 2010-01-15
> **kansasnoob said:**
> Just purging packages and installing legacy grub will get you to boot but you'll end up with both legacy grub and grub2 files in the /boot/grub directory. Anyway you can achieve a truly clean install of legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)
from your own post:
> First remove grub2:

Code:
sudo apt-get --purge remove grub-pc grub-common

You'll be confronted with this text:

[QUOTE][B]Do you want to have _*all*_ GRUB 2 files removed from /boot/grub? 
Your system would be then unbootable if you don't install another bootloader. Remove GRUB 2 from /boot/grub?
Yes, you do! We've created a backup anyway.[/B][/QUOTE]

purging removes the package and all the configuration files. "--purge remove" should be the same as "purge". from man apt-get:
> purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).


---

### Post by SchneiderIS on 2010-01-24
Well, this didn't work as I got the following errors:

```
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: IO Error saving source cache
E: The package lists or status file could not be parsed or opened.

```

There is plenty of room left but I am still in the Live CD so my thinking is that the drive might be write protected but that doesn't make sense either unless it is trying to remove the Live CD grub, if that is possible.  At any rate I am sort of stuck on this one.

It might be noted that the unit has been sitting in Live CD execution since I last wrote about this problem.  There is a notice for updates but Synaptic won't launch which makes me think there is another issue at play here as well.

---

### Post by kansasnoob on 2010-01-24
> **SchneiderIS said:**
> Well, this didn't work as I got the following errors:

```
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: IO Error saving source cache
E: The package lists or status file could not be parsed or opened.

```

There is plenty of room left but I am still in the Live CD so my thinking is that the drive might be write protected but that doesn't make sense either unless it is trying to remove the Live CD grub, if that is possible.  At any rate I am sort of stuck on this one.

It might be noted that the unit has been sitting in Live CD execution since I last wrote about this problem.  There is a notice for updates but Synaptic won't launch which makes me think there is another issue at play here as well.

And that was the result of ........ ?

Why not post the full output of the terminal?

I also have to wonder if you read the warning I put up on my "revert" HowTo:

> Caution: check software sources before proceeding!  As of 01/09/2010 I've encountered several problems with the packages "grub" and "grub-common" (or even "grub-pc") not being available for installation during this procedure (particularly with the Australian server).

So before proceeding go to Synaptic Package Manager and click on Reload. When it's done click on Search and type grub, make sure that the packages grub, grub-pc, and grub-common are all available there.

If they're not we need to straighten out the software sources. Since we're in Synaptic I'd begin by just clicking on Settings > Repositories and change to the Main Server. Also be certain that all four of the Ubuntu repos are checked, but that the CD-ROM box is NOT checked.

Then click on reload again, and Search, type grub and check again to see that grub, grub-pc, and grub-common are all three there! If not DO NOT proceed, I'll need to see the output of:

Code:

cat /etc/apt/sources.list

Feel free to send me a brief PM pointing me to your specific thread here on the forums if need be.

But with only a snippet of the terminal output I have no idea what you were doing. Electronic ink is cheap.

Don't leave me guessing.

---

### Post by SchneiderIS on 2010-01-24
was following Leppie's instructions and on the first line of:

```
sudo apt-get purge grub grub-pc grub-common

```

I got the error.

Your instructions assume the ability to run Synaptec but apparently you did not read my posting in which I said it could NOT be run.  My preference is to run this from the command line.

---

### Post by old_el_pedro on 2010-05-04
had the same problem. you are on your live-cd. with
```

sudo update-grub

```
you are trying to update grub related to your live-cd system (false grub root-directory).

you have to mount your root-directory of your native system (for example, to /mnt/sdXY), then do something like
```

sudo update-grub /mnt/sdXY

```

---

