---
title: "Installed Ubuntu on XP system. How to get dual boot?"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by RockDawg on 2007-03-10
This is my first foray into any kind of linux.  I decided to install Ubuntu on my XP machine.  I had a sperate partition that was empty and divided into two partitions.  One for / and one for swap.  I set the / partition with a boot flag and Ubuntu seemed to install fine.  When I rebooted my system it went straight to Windows.  I didn't get any dual boot screen.  I could of sworn that I saw Ubuntu say "installing GRUB" while it was installing.  What did I do wrong and how can I correct it?

---

### Post by RockDawg on 2007-03-10
I just tried the instructions in the first post of this thread...:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Every command seemed to run fine, but a reboot still didn't give me a boot menu ant it still took me directly to Windows.  What am I missing?

EDIT: I should also mention that the partition that I installed Ubuntu is on a different drive than the XP partition.  Just in case that matters.

---

### Post by ReverendWolf on 2007-03-10
perhaps your XP partition is set to boot first in BIOS, and your PC just doesn't get the chance to look at GRUB?

---

### Post by ucsdrake on 2007-03-10
> **ReverendWolf said:**
> perhaps your XP partition is set to boot first in BIOS, and your PC just doesn't get the chance to look at GRUB?


agreed ... ensure that your BIOS look at the drive that has GRUB on it first

---

### Post by RockDawg on 2007-03-10
My BIOS only offers HDD as an option.  I don't get to choose from multiple drives or partitions.

---

### Post by confused57 on 2007-03-10
> **RockDawg said:**
> My BIOS only offers HDD as an option.  I don't get to choose from multiple drives or partitions.
That's the only options I have in my Dell Dimension bios.  What you might want to do is boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"
this will show your partition tables on both hard drives

Here's how I set up a dual boot on my Dell:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by wxnker on 2007-03-10
When you boot up. Do you see "loading grub" for a second?
There should be an option to hit "esc" to access the grub boot manager.

---

### Post by RockDawg on 2007-03-10
> **wxnker said:**
> When you boot up. Do you see "loading grub" for a second?
There should be an option to hit "esc" to access the grub boot manager.

I don't see anything like that.

---

### Post by wxnker on 2007-03-10
I guees you should boot from the ubuntu CD then.

I'm off to bed in a second but try searching "grub" in this forum or "dual boot". There are lots of help here on the matter.

in short I think you need to edit your grub menu.lst. It's in /boot/grub/menu.lst


Boot from the ubuntu CD.

Open the terminal.

Make a backup:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

Edit:
```
sudo gedit /boot/grub/menu.lst
```

For starters you could try with just editing this in grub.

Find this section:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2 

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

Change timeout to 10 or 20 (seconds the menu is shown)
Change hiddenmenu to #hiddenmenu

Like this:
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

By default the grub boot manager is hidden. This should make the boot menu appear for 10 sec. if it's correctly installed.

---------------------------------------------------------------------------

Grub in general:

The first part of the menu.lst is sort of a guide. It shows how you add boot partitons etc.
If you need to edit things then you'll need information on which partitions XP and Ubuntu is on.

To see this open the terminal and write:
```
sudo fdisk -l
```

write down the numbers. (e.g hda1, hda2)

Remember, in Grub hda1= 0,0 hda2 =0,1 etc.

Good luck and welcome to ubuntu :D

---

### Post by RockDawg on 2007-03-11
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

When I run this command, I get the following error:

*cp: cannot stat `/boot/grub/menu.lst': No such file or directory*

```
sudo gedit /boot/grub/menu.lst
```

When I run this command, gedit opens and the tab says menu.lst, but the page is blank.

Following the instructions of another thread, I typed the following command from the GRUB shell:

```
find /boot/grub/stage1
```

That returned (hd0,0).  I then typed 

```
root (hd0,0)
```

followed by

```
setup (hd0)
```

That seemed to install something and if I understand things correctly, hd0,0 is my WinXP drive and partition which my computer boots from.  It would seem like it should see GRUB and run it, but it doesn't.  I suppose it has something to do with the first command returning a "can't find file" error, but I'm not sure what's wrong.  I am dying to get this figured out so I start getting familiar with Ubuntu.

---

### Post by RockDawg on 2007-03-11
Since I've seen this requested in numerous other threads, here's what comes up when I run "sudo fdisk -l":

```
Disk /dev/sda: 37.0 GB, 37018484224 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        4499    20780077+   f  W95 Ext'd (LBA)
/dev/sda5            1913        4499    20780046    7  HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10117    81264771   83  Linux
/dev/hda2           10200       19456    74356852+   f  W95 Ext'd (LBA)
/dev/hda3           10118       10182      522112+  82  Linux swap / Solaris
/dev/hda5           10200       19456    74356821    7  HPFS/NTFS

```

---

### Post by RockDawg on 2007-03-11
After further inspection, it seems that I was wrong earlier when I stated that (hd0,0) was my XP drive and partition.  I quess it would really be (sd0,0).  I getting really confused now.  How can I fix this and get a boot menu?

---

### Post by confused57 on 2007-03-11
You might want burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it is capable of booting either Windows or Linux

Also, if you want to examine your menu.lst from the live cd:
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

I don't know why grub isn't installing on your Windows SATA drive, which is where it will need to be to boot Ubuntu, since you're not able to boot first to your hda drive...grub designates your first partition on the first hard drive as (hd0,0), regardless if it's SATA or IDE.

Another possibility is the GAG boot manager:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
see the GAG section in the index

For GAG to boot Linux, grub has to be installed on the root partition, for example:
```
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)
quit
```

You can make a GAG boot floppy or cd or it can be installed to your mbr.

Evidently, your Ubuntu drive is recognized as (hd0), since find /boot/grub/stage1 returned root (hd0,0).  This would probably make your Windows drive (hd1)...you could install grub to (hd1), but I wouldn't do this, except as a last resort...at least you're able to boot Windows now, although Windows IPL code can be restored to the mbr, using the Super Grub Disk, or following these instructions:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You "might" be able to get everything to work by installing grub to (hd1), but you'd have to do sommersaults & jump through through hoops to get everything reconfigured in your /boot/grub/menu.lst file to get it work.

---

### Post by RockDawg on 2007-03-11
Thanks for that confused57.  I was able to open menu.lst after running your commands.  Here's the info from menu.lst (I read that every line the begins with a # is just a comment, so I left those out):

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

Is this any help?  What should I change?

---

### Post by confused57 on 2007-03-11
The only way I think you would be able to get your system to work, with you current menu.lst would be able to boot first to your hda drive...since grub is installed to your Ubuntu drive (hd0) & Windows is (hd1).

Here's something I found in another thread for possibly booting grub from Windows:
[http://marc.herbert.free.fr/linux/win2linstall.html#grub-for-nt](http://marc.herbert.free.fr/linux/win2linstall.html#grub-for-nt)
I've never had to try it, but you might want to read over it.

Make a copy of SGD & see if it'll boot your Linux hard drive, that's the first thing I'd try.

---

### Post by RockDawg on 2007-03-11
I downloaded and burned the super GRUB disk.  I booted from it and selected Ubuntu and got the following error mesage:

Error 17: Cannot mount selected partition.

---

### Post by confused57 on 2007-03-11
If you have your important data backed up on your Windows drive, I could probably help you really mess up your system, but you could possibly try(at your own risk, I can't guarantee it'll work):
1.) Use the live cd to install grub to your Windows drive:
```
sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd1)
quit
```
this "should" install grub to your Windows mbr

Then you'd need to change your menu.lst(using the live cd) to look something like this:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quietsavedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader +1
```

To get this to work, you may also have to modify your /boot/grub/device.map to show:
(hd0) sda
(hd1) hda

It might be best not to try this just yet...wait if someone else has some suggestions for you, check your bios again to make sure you can't find some way to boot first to your hda drive.  I just wanted to give these instructions, possibly for someone else to look over, to see if they might work.  You still may want to consider the GAG boot manager.

If you happen to do the above, & it works, make sure not to update your Ubuntu, until you change this line in your /boot/grub/menu.lst"
# groot=(hd0,0)
to
# groot=(hd1,0)

---

### Post by RockDawg on 2007-03-11
OK.  Half the battle is won.  I now get the boot menu on startup and if I select Ubuntu it boots into it fine.  BUT, if I select Windows, it just goes to a black screen with a cursor.  It won't boot into Windows.

The only things I did were install GRUB on the Win drive and edit the menu.lst file according to the post above.  I didn't modify my device.map or the last suggestion.  Should I do one of those now?  Will either help me boot into windows?

---

### Post by confused57 on 2007-03-11
> **RockDawg said:**
> OK.  Half the battle is won.  I now get the boot menu on startup and if I select Ubuntu it boots into it fine.  BUT, if I select Windows, it just goes to a black screen with a cursor.  It won't boot into Windows.

The only things I did were install GRUB on the Win drive and edit the menu.lst file according to the post above.  I didn't modify my device.map or the last suggestion.  Should I do one of those now?  Will either help me boot into windows?

Yes, try changing your /boot/grub/device.map...and you might try adding a separate Windows entry, just below your current entry in /boot/grub/menu.lst:

title		  Microsoft Windows XP Professional test
rootnoverify  (hd0,0)
makeactive
chainloader   +1

see if this entry might boot Windows.

I don't know for sure, but you maybe didn't need to make the changes to your former menu.lst after installing grub to your Windows drive mbr(I'm not sure)...I just thought of this and was checking back in to add this to my last reply.

You can always restore your Windows IPL code from the links I gave you earlier, if you need to, grub on the mbr shouldn't affect your Windows installation.

---

### Post by RockDawg on 2007-03-11
> I don't know for sure, but you maybe didn't need to make the changes to your former menu.lst after installing grub to your Windows drive mbr(I'm not sure)...I just thought of this and was checking back in to add this to my last reply.

I tried booting after installing GRUB on the Win drive and before editing the menu.lst file and I got the boot menu, but couldn't boot into Win or Ubuntu.  Editing the menu.lst at least got me into Ubuntu.

I will try your suggestions now.

---

### Post by RockDawg on 2007-03-11
Kudos!  That worked!  I suppose I can now correct the same lines for the original XP entry in menu.lst and delete the entire entry I added so that I only have one Windows selection on the boot menu.

Also, I just did this:

```
If you happen to do the above, & it works, make sure not to update your Ubuntu, until you change this line in your /boot/grub/menu.lst"
# groot=(hd0,0)
to
# groot=(hd1,0)
```

I'm not sure why though.  Doesn't "#" specify a comment?

Can I now update Ubuntu?

---

### Post by confused57 on 2007-03-11
> **RockDawg said:**
> Kudos!  That worked!  I suppose I can now correct the same lines for the original XP entry in menu.lst and delete the entire entry I added so that I only have one Windows selection on the boot menu.

Also, I just did this:

```
If you happen to do the above, & it works, make sure not to update your Ubuntu, until you change this line in your /boot/grub/menu.lst"
# groot=(hd0,0)
to
# groot=(hd1,0)
```

I'm not sure why though.  Doesn't "#" specify a comment?

Can I now update Ubuntu?
Great, I'm glad it worked...just leave the Windows entry that works.  The comment(#) doesn't apply for this entry(# groot=(hd1,0)), update-grub reads this line when a kernel is updated and applies it accordingly to make your new kernel entries in menu.lst.
You shouldn't have any trouble updating Ubuntu now...

---

### Post by RockDawg on 2007-03-11
Thanks so much for your help!  I truly appreciate it and learned a little along the way.  Now I can go play around with Ubuntu and find tons more questions I'll be on here asking about. :lolflag: 

Also, thanks to everyone else who tried to help earlier.

---

