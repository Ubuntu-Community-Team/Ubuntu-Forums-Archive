---
title: "Just says &quot;GRUB&quot; at boot."
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by frozenjim on 2007-10-30
I have freshly formatted and reinstalled my Toshiba M30 laptop.  First I installed XP Pro and then I installed Ubuntu Gutsy Gibbon.  Everything works fine in both operating systems.  No errors at all during either installation.

Rebooted after Ubuntu installation and the screen just says "GRUB".  No error message.

If I boot from any liveCD and choose "Boot from first hard drive" then it comes up with my nice little grub menu and I can load either OS just fine.

To be sure that I was looking at the RIGHT grub menu, I booted into Ubuntu and edited my menu.lst to change the color to red/white for my hilited items.  Rebooted with my liveCD, choose "Boot from first hard drive" and the menu came up fine with my new color scheme.

Why will it boot fine when prompted by a liveCD but not from a fresh boot?

Troubleshooting steps taken:
```

Repair MBR via XP Recovery Console
# fixmbr
```

```
Reinstall Grub from Ubuntu
# update-grub
# install-grub
```

```
Manual Grub Install
# find /boot/grub/stage1
# root (hd0,1)
# setup (hd0)
```

Drive List:
```
sda1 - Windows XP
sda2 - Ubuntu
sda3 - Extended
sda4 - Swap
```

None of these either repair or break the current scenario.  Anybody have an idea?

---

### Post by bswilson on 2007-10-30
You're not doing anything `wrong`, it's just that grub is looking for the boot image in the wrong place.  From the GRUB prompt, type these four commands, hitting Enter after each:

```
#rootnoverify (hd0,0)
# makeactive
# chainloder +1
# boot
```

That *should* fix you right up.

---

### Post by gsiliceo on 2007-10-30
Hey, i would try supergrub, is a bootable cd with the hability to fix grub or break it so be careful, anyway it has an explanation for all the things it does.
[http://supergrub.forjamari.linex.org/]("supergrub.forjamari.linex.org/")

---

### Post by logos34 on 2007-10-30
actually there was a small error the first time:

should have been

# install-grub [COLOR="Red"]/dev/sda[/COLOR]  (-->sends grub to mbr)

but the second time you got it correct, 'setup (hd0)' should have written grub to mbr.

You might take a look at [this page]("http://www.users.bigpond.net.au/hermanzone/p1.htm").

---

### Post by frozenjim on 2007-10-31
Thanks for the great suggestions.  In particular I was hopeful that those grub commands would make the difference (rootnoverify, makeactive etc.).  But in the end I still see the word "GRUB" instead of my boot screen.

It seems like grub just won't install into the MBR.  (But why is the word GRUB there then?)

In desperation, I created a new partition before the Windows partition and tried to install Grub there - just in case it was some kind of partition-size issue.  No dice, after resizing the Windows partition and setting up Grub as well as fixing my boot.ini, I am back at the same place.  I boot and it says "GRUB".

So deleted the new partition, resized my Windows partition again and ran "fixboot" from Windows recovery.  Booted into Windows just fine.  Then I installed Grub again and guess what?  It just says "GRUB".

So clearly, GRUB is using the correct MBR because it is overwriting the MS boot information.  But it just isn't pointing to stage2 correctly(?).

I am truly baffled.  Why can I use my Ubuntu LiveCD Grub menu to "Boot from first hard disk" but not do so from my normal boot?  Everything is working just the way it should be working - except I need that LiveCD to make my Grub menu appear.

BIOS setting perhaps?

---

### Post by adrian15 on 2007-10-31
> **frozenjim said:**
> 
Why will it boot fine when prompted by a liveCD but not from a fresh boot?


I actually do not know why does happen.
I have a kind of solution for you:

Get Super Grub Disk and then:

1) Advanced -> LILO -> Restore LILO to the MBR -> MBR LILO -> Select your only Hard Disk

2) Boot & Tools -> Activate Partition -> Select the Ubuntu partition.

3) Advanced -> GRUB -> Restore GRUB to a partition boot sector -> Select the Ubuntu partition -> Select the Ubuntu partition

4) Edit your menu.lst from a live cd so that the Windows boot entry does not have the makeactive command in it.

5) Pray to St IGNUcius and reboot.

Now the minimal LILO boot loader should chainload your GRUB which has been installed to the Ubuntu partition sector.

Another option to this is to change step 1 with: Windows -> Fix Boot of Windows but I prefer the lilo one because it's more sure.

adrian15

---

### Post by frozenjim on 2007-10-31
Wow, that's geting creative!  So I would be chaining Windows Boot to Lilo which is chained to Grub.

It might work, but I can see how every time I upgrade my kernel I would be in trouble.  That's also the same reason that I use Grub rather than just use the Windows boot loader.

----------
Here's another really interesting hint that I just discovered:
If I boot my PC with the Windows CD in it it says "press any key to boot from CD".  So I did not press any key (I was distracted) and guess what?  MY GRUB MENU CAME UP WORKING JUST FINE!  WTF!!!!

So my computer DOES see grub and it IS in the right place - but I have to have the CD fail to load first.

Baffling.

Another piece of the puzzle:  Prior to reinstalling Windows and Ubuntu this weekend, it was working just fine dual booting Windows/Debian and Windows/Gentoo using Grub in exactly the same configuration.  Only since installing Ubuntu has this failed to work and I am truly baffled.

---

### Post by adrian15 on 2007-10-31
> **frozenjim said:**
> 
Another piece of the puzzle:  Prior to reinstalling Windows and Ubuntu this weekend, it was working just fine dual booting Windows/Debian and Windows/Gentoo using Grub in exactly the same configuration.  Only since installing Ubuntu has this failed to work and I am truly baffled.

Let's see you can try this: Go to your /boot/grub folder and rename:

stage1
stage2
e2fs_stage1_5 files to 

stage1_backup
stage2_backup
e2fs_stage1_5_backup

Copy and paste these same files from the SGD cdrom (you will find them in boot/grub) to your /boot/grub folder.

Boot Super Grub Disk, Run Linux -> Fix Boot of Linux (GRUB) and tell us if the problem persists. SGD's grub is not based on Ubuntu's grub but rather in Debian (not fully based though) grub.

adrian15

---

### Post by adrian15 on 2007-11-06
> **frozenjim said:**
> I have freshly formatted and reinstalled my Toshiba M30 laptop.  First I installed XP Pro and then I installed Ubuntu Gutsy Gibbon.  Everything works fine in both operating systems.  No errors at all during either installation.

Rebooted after Ubuntu installation and the screen just says "GRUB".  No error message.

If I boot from any liveCD and choose "Boot from first hard drive" then it comes up with my nice little grub menu and I can load either OS just fine.

I was making myself a question. Do you have two hard disks maybe ?

adrian15

---

### Post by frozenjim on 2007-11-11
Well, unfortunately I have solved the problem without understanding which of the steps I took was the actual solution.

I BELIEVE that one of two things made grub work again:
Installed Grub2 from apt-get.
Changed the link to vmlinuz to a file that actually existed

One of these two things was the solution.  In either case, it's something worth looking into for the Ubuntu installation team.  Someone less dedicated might have just abandoned the installation altogether.

Anyhow. It's fine now.  Thanks guys for all of your help.

---

