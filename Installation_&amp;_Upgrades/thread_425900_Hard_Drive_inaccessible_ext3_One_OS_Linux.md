---
title: "Hard Drive inaccessible ext3 One OS Linux"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by kb0pxn on 2007-04-28
Here is what I do know:
Everything was working fine...
I installed the Direct upgrade:
   to Ubuntu 7.04 ("Feisty Fawn")
   from Ubuntu 6.10 ("Edgy Eft")
There is no other Operating System involved.

It prompted me for decisions throughout.
I tried to take the defaults, and not retain any previous settings.

Now I wished I would have written all of the promptings down...

Additional Complication:

The motherboard's PS/2 keyboard port is not working, so I am using a
USB keyboard.  I think this causes me a problem getting into the grub 
or being able to Boot up from CD and selecting Recover a broken system

Here is a description of the Hard Drive
===============================================================================
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30287   243280296   83  Linux
/dev/hda2           30288       30401      915705    5  Extended
/dev/hda5           30288       30401      915673+  82  Linux swap / Solaris
===============================================================================

Now, it DOES start to boot,
goes through the Splash Screen,
and appears to lock up at a black screen and spinning cursor

I go to power off and for a moment, the black screen disappears and I see
a progression of what had loaded, showing for about 20-30 seconds before it shuts off:
===============================================================================
[I]Starting VMware services:
  Virtual machine monitor                                               done
  Virtual ethernet                                                      done
  Bridged networking on /dev/vmnet0                                     done
  Host-only networking on /dev/vmnet1 (background)                      done
  Host-only networking on /dev/vmnet8 (background)                      done
  NAT service on /dev/vmnet8                                            done
*  Starting NFS common utilities                                           [OK]
*  Starting NTP server ntpd                                                [OK]
*  Setting up ALSA...                                                      [OK]
*  Setting up disc parameters...                                           [OK]
*  Starting anac(h)ronistic cron anacron                                   [OK]
*  Starting deferred execution scheduler atd                               [OK]
*  Starting periodic command scheduler crond                               [OK]
*  Starting additional executable binary formats binfmt-support            [OK]
*  Starting web server (apache2)...
apache2: apr_sockaddr_info_get() failed for bosshogg-desktop
apache2: Could not reliably determine the server's fully qualified domain name,
using 127.0.0.1 for ServerName

* Checking battery state...                                                [OK]
* Running local host scripts (/etc/rc.local)                               [OK][/I]

[B]Timidity is not yet configured.
Enable Alsa Sequencer first by editing /etc/default/timidity.[/B]
===============================================================================

I booted with an Ubuntu Live CD (cousin brought over version of Live 6.06.1 LTS)
and tried to get into the Hard Drive to edit [/etc/default],
but I do not know how...


Using Live 6.06.1 LTS, I went to System - Administration - Disks and opened the
Disks Manager.  It was able to see the HDD:

ST3250623A
232.89 GiB
/dev/hda

with 2 partitions:

Partition 1      /dev/hda1   extended 3
         STATUS: INACCESSIBLE
and
Swap Partition   /dev/hda5   memory swap


I am new to Ubuntu and to Linux, if responding.  Thanks for any help.

---

### Post by kb0pxn on 2007-04-29
I have gone on and tried more things.

I have learned to MOUNT the inaccessible Hard Drive using:

sudo mount /dev/hdb1 /mnt

I was able to copy off the pictures and spreadsheets and some things I wanted off

couldn't figure out how to get KMyMoney data files...

anyway...

learned about not being the owner to change files
created a launcher on the desktop that did :

gksudo "gnome-open %u"

drag and drop files -  and Read Only files became accessible

played with mnt / etc / default / timidity
changing the remark statements

I had at least a cause/effect going activating the remarked lines,
but nothing that would get me past that point.

tried [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
and tried to strip the machine of Timidity

Deactivating init-scripts
1. Method one: Deleting the rc*.d links

   I did a search for Timidity and found what I thought was offending


  I copied them to another folder and deleted them where they were found (/etc/rcX.d)
see attachment - jpg picture of the screen if it works

It didn't seem to help, so I will put them back next.

I am muddling through this alone,  Anyone want to help?

Thanks, Jim

---

