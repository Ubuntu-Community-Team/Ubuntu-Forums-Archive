---
title: "Would Like To Copy Mbr Before Install"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Frederick J. Harris on 2008-05-24
I did this before on one of my laptops and it worked fine without a hitch, but now I can't get it to work on another laptop I'm wanting to install Ubuntu to.  I got this technique from one of Herman's Ubuntu tutorials.  One puts the live distro cd in and runs from that.  Then use the dd command to transfer the 446 bytes of the pre-install mbr startup code to another file to save. 

```

dd if=/dev/hda of=/home/ubuntu/ibmmbr.img bs=446 count=1 

```

Here's my Terminal Screenshot.  You can see the error...

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo dd if=/dev/hda of=/home/ubuntu/ibmmbr.img bs=446 count=1
dd: opening `/dev/hda': No such file or directory
ubuntu@ubuntu:~$ 

```

As you can see, I'm getting `No such file or directory'

Could someone help me with this?  I could just go and install Ubuntu on this machine without the mbr copy, but I'd really like to have that copy.

---

### Post by cdtech on 2008-05-24
The first sector (512 bytes) is the MBR and consists of, 446 bytes bootloader, 64 bytes partition table and a 2 byte signature.

Are you trying to copy a Window MBR?

You can read the sector with:
dd bs=512 count=1 if=/dev/hda | od -Ax -tx1z -v

Just to see if it exsist on that drive, maybe its on another drive #

---

### Post by hal8000 on 2008-05-24
> **Frederick J. Harris said:**
> I did this before on one of my laptops and it worked fine without a hitch, but now I can't get it to work on another laptop I'm wanting to install Ubuntu to.  I got this technique from one of Herman's Ubuntu tutorials.  One puts the live distro cd in and runs from that.  Then use the dd command to transfer the 446 bytes of the pre-install mbr startup code to another file to save. 

```

dd if=/dev/hda of=/home/ubuntu/ibmmbr.img bs=446 count=1 

```

Here's my Terminal Screenshot.  You can see the error...

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo dd if=/dev/hda of=/home/ubuntu/ibmmbr.img bs=446 count=1
dd: opening `/dev/hda': No such file or directory
ubuntu@ubuntu:~$ 

```

As you can see, I'm getting `No such file or directory'

Could someone help me with this?  I could just go and install Ubuntu on this machine without the mbr copy, but I'd really like to have that copy.



Thats almost correct apart from one tiny detail: the Hadry kernel now uses libATA so your IDE drive now uses scsi emulation. The drive is now  sda not hda. From the live cd type:

sudo dd if=/dev/sda of=/home/ubuntu/ibmmbr.img bs=446 count=1

this copies the first 446 bytes only (NOT the partition table).
If you are dual booting with windows, you can always replace the boot
code with the windows standard bootloader, by using the ERC and typing
fdisk /mbr or fixdisk in XP

---

### Post by Frederick J. Harris on 2008-05-24
Thanks for the info cdtech and hal.  I'll give it a shot now.  Even with my limited knowledge of Linux that scsi thing with sda vs hda did occur to me, but given my limited knowledge of all this, coupled with the potential destructive power of dd, I thought I'd ask before starting to root around with a 'hit or miss' approach!

Yes, where it had worked before was on this laptop I'm typing now which was with Edgy Eft 6.1.  I just bought an 8.1 Hardy Heron LTS disk and am trying to start another old ibm thinkpad with that, and I want to set up a dual boot with Win 2000 pro.  Its kind of going to be my new (old) dream machine.:)

---

### Post by Herman on 2008-05-24
:) Thanks for posting about this, I have updated that web page now.

Sorry for the inconvenience, it's quite a large website for one person to keep up to date, but I should have noticed that detail nad corrected that before now.

---

### Post by Frederick J. Harris on 2008-05-24
Hello Herman!  No problem about the discrepancy.  After all, from what hal mentioned, it was something that got changed.

I just tried it with sda instead of hda and it worked like a charm.

```

sudo dd if=/dev/sda of=/home/ubuntu/ibmmbr.img bs=446 count=1

ubuntu@ubuntu:~$ sudo dd if=/dev/sda of=/home/ubuntu/ibmmbr.img bs=446 count=1
1+0 records in
1+0 records out
446 bytes (446 B) copied, 0.000464332 s, 961 kB/s
ubuntu@ubuntu:~$ 

```

And thanks very much for all the work you did at your site.  It contains a lot of useful information and is appreciated!

This thing about saving the mbr now.  For a lousy 446 bytes I think its something everybody ought to do really.  I spent one truely miserable week about a year ago due to this.  It was an old Compaq Win 2000 machine I decided I didn't care that much about if I screwed it up and I screwed it up good and found out I really cared about the darn thing and wanted to fix it.  I had the Win 2000 recovery disk that came with it but I believe all that was was an image or something that assummed the mbr and booting code would be in place and working because all the recovery disk did was copy the OS to the machine without fixing the mbr.  To make a long story short I finally got it fixed through an old set of DOS 6.22 installation floppies that as part of installing DOS fixed the mbr.

---

### Post by Herman on 2008-05-24
:) Hello Frederick J. Harris,
> I had the Win 2000 recovery disk that came with it but I believe all that was was an image or something that assummed the mbr and booting code would be in place and working because all the recovery disk did was copy the OS to the machine without fixing the mbr. To make a long story short I finally got it fixed through an old set of DOS 6.22 installation floppies that as part of installing DOS fixed the mbr.
 That was a good idea. There are lots of computers that don't come with Windows 'Installation CDs' these days, and even if they do come with a 'Recovery disk', those don't have the functionality of a proper 'Installation Disk'.
A Windows 98 boot floppy disk can be used for fixing the MBR for Windows XP too.
With Vista that's no longer an option because Vista had been made dependant on the 'Disk Signature' in the MBR, which a dd backup will preserve, so I agree with you, more people should take a few minutes to make a backup of their MBR, especially if they have Vista.

 I have some more suggestions, ( a whole collection of them), for changing the MBR's boot loader code area in this web page, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm").

Regards, Herman :)

---

