---
title: "Chainload GRUB2 -&gt; GRUB2?"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2011-02-05
Anybody done it?

Little help please?

ed.:
Just to clarify; I want to edit the 'primary' GRUB 2, to show the boot option for 'secondary' GRUB2 on another HDD drive in the computer.


[I][SIZE=3][COLOR=Blue][B]EDIT:
User 'franzb' has posted the solution to this question at post #21 [here]("http://ubuntuforums.org/showpost.php?p=10439004&postcount=21").

OR, to chainload TO GRUB2, FROM GRUB-_legacy_[/B][B], your menu.lst file entry will be:
[/B][/COLOR][/SIZE][/I][B][COLOR=Blue]title [COLOR=White].......[/COLOR]                 GRUB2 
root [COLOR=White]....... [/COLOR]                 (hdX,Y)    [COLOR=Red]<-This value is derived from search for /boot/grub/core.img from GRUB command-line[/COLOR]
kernel [COLOR=White]... [/COLOR]           /boot/grub/core.img
boot[/COLOR][/B]

---

### Post by kansasnoob on 2011-02-05
Why would you want to?

I multi-boot a lot and grub2's auto-detection is generally superb:

```
lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found Ubuntu 10.10 (10.10) on /dev/sda1
Found Linux Mint 10 Julia (10) on /dev/sda10
Found Debian GNU/Linux (6.0) on /dev/sda11
Found Ubuntu 10.10 (10.10) on /dev/sda12
Found Peppermint (peppermint) on /dev/sda13
Found Ubuntu natty (development branch) (11.04) on /dev/sda14
Found Linux Mint Debian Edition (1) on /dev/sda15
Found Ubuntu natty (development branch) (11.04) on /dev/sda16
Found Ubuntu natty (development branch) (11.04) on /dev/sda17
Found Ubuntu 10.10 (10.10) on /dev/sda18
Found Ubuntu 9.10 (9.10) on /dev/sda2
done

```

---

### Post by Moozillaaa on 2011-02-05
Hi KSNoob... (Salina KS maybe?)

I want to edit GRUB2 to load a second GRUB2 loader on a second disk.

---

### Post by oldfred on 2011-02-05
While I agree with    	kansasnoob, I do this as I have 3 different grub2 in three different drives and turn off osprober.

I copied some of    	kansasnoob's suggestions on booting a partition rather than a kernel also.

The issue is in my case that drive order changes. The boot drive is always hd0 so I could not copy my chainboot entires from one to another as the hard drives change. Or when I boot sdc it is hd0, sda is hd1. but if I boot sda it is hd0 and sdb is hd1 etc. Lots of combinations. Then I added some grub2 bootable flash drive and now I am really confused.

I copied this from kansasnoob.
```
Boot most up2date kernel on sda7
menuentry "Install on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}

```
These are some of my other entries, but they vary depending on drive number:
```
menuentry "Lucid Lynx on sda (When from sdc) Chainboot" {
set root=(hd1)
chainloader +1
}

menuentry "9.04 on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

```

---

### Post by Moozillaaa on 2011-02-05
So how do I add the menu item to the 'primary' GRUB2 boot list?

I know what the entry will look like; but I don't know how to edit grub.cfg file...

---

### Post by oldfred on 2011-02-05
You do  not edit grub.cfg but 40_custom.

gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

That will write a new grub.cfg with the 40_custom entries.

More grub2 info. Also see all the links in drs305's signature.
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Moozillaaa on 2011-02-05
All the links are pink (I already visited them!). Thanks tho'! You should see my browser cache UGH!

Only chainload info is for GRUB2 into GRUB-legacy. I figured that one myself ;) [here ]("http://ubuntuforums.org/showthread.php?t=1679850").

I like to keep it as simple as possible...

---

### Post by Moozillaaa on 2011-02-05
Ok - I got 40_custom edited, updated GRUB, and it added all my custom entries to the original GRUB2 menu.

I didn't turn off 'OS prober???

And the entry for GRUB 2 Disk 2, when selected, returned:

(hd1,4): Filesystem is ext2.
error: unknown command 'kernel'.
error: no loaded kernel.

Press any key to continue....

So my entry is no good as entered:

root (hd1,4)
kernel /boot/grub/core.img
boot

(whereas it was good for menu.lst in GRUB-legacy chainload. :( )

---

### Post by oldfred on 2011-02-05
Grub2 counts partitions differently. If it is sdb5 and in old grub hd1,4 then in grub2 it is hd1,5. Grub2 now counts from 1 where grub legacy counted from 0.

Use e on grub2 menu and do one time edit to test. I find because of the way it loads hd0 as boot drive I have to manually edit hdx to find correct drive.

---

### Post by Moozillaaa on 2011-02-05
Good info - thanks!

Now, if I could just delete a few GRUB2 entries, all would be well...

---

### Post by Moozillaaa on 2011-02-05
Solved! JOY!

Get RID of GRUB2.

Install GRUB-legacy.

Add menu entry for GRUB2 on second HDD, INTO menu.lst. Elapsed time - <0:15 (I took my time)

=============================

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        fdcf20ef-a198-45be-877c-3dbc01c64ef5
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        fdcf20ef-a198-45be-877c-3dbc01c64ef5
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic



title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        fdcf20ef-a198-45be-877c-3dbc01c64ef5
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        fdcf20ef-a198-45be-877c-3dbc01c64ef5
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        fdcf20ef-a198-45be-877c-3dbc01c64ef5
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdh1
title        W7
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1



title           GRUB2            <- 10.04, Vista
root            (hd1,)
kernel          /boot/grub/core.img
boot


Perfect. Easy. menu.lst



What are they thinking?
***Are*** they thinking?
GRUB2 / GRUB2 GUI / grub.cfg / 40_custom / /etc/default/GRUB.d/ ...
yikes! Gadzoinks!!! ugH!

Keep it simple. Not like Windows.

Just my opinion here...

---

### Post by oldfred on 2011-02-06
I resisted grub2 for awhile, but find grub2's osprober alone worth the conversion. It almost always finds other installs and sets up a boot stanza that works.

If you are staying with old grub for now, you may prefer a grub only partition and then just manually edit every entry.

chainboot 145 systems - saikee
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)
[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

---

### Post by Moozillaaa on 2011-02-06
Thanks again there fred...

Why and how long did you stay off of GRUB2?

Just the feature alone, that you describe - os prober, is too Windows-like, in my opinion. I'm going to post up an opinion thread in CC on it...



ed.:
On second thought, maybe I won't post an opinion thread in CC, especially since it's CLOSED.

---

### Post by Moozillaaa on 2011-02-06
Well now GRUB2, that I chainloaded from GRUB-legacy, has filled its' menu with a dozen defunct kernels, and that was the whole point of trying to edit the PRIMARY GRUB2 (and for which I happily reverted to GRUB GOOD (legacy).

Of course, this is great if I changed my mind in mid-click, and want to go back to the original default OS.

BUT I DON'T!!!

So how do we delete these items???

GRUB2 stinks. It is PURE WINDOWS-like, in its' behavior.

---

### Post by davidmohammed on 2011-02-06
if grub 2 is finding all those kernels - its time for you to do some house keeping.

Install ubuntu tweak and use it to delete all the obsolete kernels.

---

### Post by kansasnoob on 2011-02-06
> **davidmohammed said:**
> if grub 2 is finding all those kernels - its time for you to do some house keeping.

Install ubuntu tweak and use it to delete all the obsolete kernels.

Or use grub-customizer:

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

Although I actually agree with you. If you have a truck-load of old kernels it's time to clean up.

I've pretty much stayed out of this conversation because I seldom find any need to actually revert grub or manually edit grub now. About 98% of the time I find grub2 to just work if it's allowed to!

---

### Post by Moozillaaa on 2011-02-06
Housekeeping? You're kidding - right? 

exec sudo -s apt-get install HOUSEKEEPER???

:lolflag:

2 d'tops, 2 laptops, 22 HDD's, about 19Tb, about 85% capacity, and a partridge in a pear tree!

Housekeeping? Ha.



[SIZE=1](yeah I do)[/SIZE]

---

### Post by oldfred on 2011-02-06
I did like the chainloading as then my grub partition was only links to each grub install in each partition. But I still had to manually edit it with every change. I only kept it for about 6 months as my boot but I still have it as I have not reorganized.

With grub2 I half reverted. I used drs305's instructions to limit grub menu to 2 kernels and copied my custom entries from the osprober into 40_custom. 40_custom is then just like menu.lst as you can do whatever you want.

I copied from this entry from kansasnoob that lets me boot any (Debian) partition as it puts a link in root to the newest kernel.
```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

```

For future reference:

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The easiest way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by franzb on 2011-02-07
It simply can't be that there is no way for booting into a second GRUB 2.

There should be a solution apart from having to switch to grub-legacy or grub4dos.

What I've given a try so far:

```

menuentry "sda5" {
        insmod ext2
        set root=(hd0,5)
        linux (hd0,5)/boot/grub/core.img
}


```

This doesn't work, though.

Any ideas?

---

### Post by Moozillaaa on 2011-02-07
> **franzb said:**
> It simply can't be that there is no way for booting into a second GRUB 2.

There should be a solution apart from having to switch to grub-legacy or grub4dos.

What I've given a try so far:

```

menuentry "sda5" {
        insmod ext2
        set root=(hd0,5)
        linux (hd0,5)/boot/grub/core.img
}


```This doesn't work, though.

Any ideas?

I think you are on the right track there Franz, with your code strings...

If (SINCE) GRUB-legacy can do this task, with the following menu entry:

> root (sdX,Y)
kernel          /boot/grub/core.img
bootthen GRUB2 should be able to do so as well.

I had GRUB2 command line with root access at my partition for core.img, but the error then was no kernel loaded, after trying different commands.

INSMOD 'xyz' returned some error - I don't remember, but seemed to indicate that only the switch 'xyz' was incorrect...

---

### Post by franzb on 2011-02-08
Issue solved.

In order to load Grub 2 from another Grub 2 you have to use the command **multiboot** instead of linux or kernel or...

```

menuentry "sda5" {
        insmod ext2
        set root=(hd0,5)
        multiboot /boot/grub/core.img
}

```

Make sure to adjust the line set root=(hd0,**x**) to your needs, pay attention to the fact that Grub 2 starts the counting of the partitions with 1, unlike Grub's 0.

Regards,

Franz

---

### Post by Moozillaaa on 2011-02-08
Good info - thanks!

This will come in handy in the near future, as Linux evolves into quasi-Windows operating environment.

I have found NOwhere on the web the correct syntax for this task - after MUCH searching, and Trial and Error.

Judging by the number of hits, this might be worthy of a blog page, IMO. In the meantime, I'll link your solution into OP. If you blog it also, PM me the weblink. Or re-write into a new cleaned up post, and mods can delete this one.

---

