---
title: "Advice on getting started with Ubuntu installation"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2008-08-06
Greetings; I'm back.

After the debacle I experienced in May, it took me a while to grow back the nerve but I want to try again.  I had posted my solution on that, that I bought Acronis Disk Director Suite and removed all traces of Ubuntu so that I could get my Windows back.

Now I want to try again, this time *NOT* with the guided install.  I am attaching a screen shot of my disks. As you can see, on Disk 1 there is a 28GB EXT3 partition labeled Ubuntu8-8.04. This is where I would like to install the OS.  (Once I have the OS installed, I would carve another couple of partitions (like 64G and 32GB) from the G drive but that's another story.)

The advice I need is mainly how to divide up logical partitions on that Ext3 partition.  Here's what I *think* I would like to do:
[LIST]
[*]A /boot logical partition of whatever size is needed, a couple of MB I would guess.
[*]The root partition (AKA /) about 2GB
[*]/swap, about 4GB
[*]/tmp, about 4GB
[*]/usr, about 6GB
[*]/var, ~12GB for installing additional software, like database or some other cool application.
[/LIST]

What options should I choose under the installation in order to achieve the above layout?

If this is covered in the docs that come with the CD image, it's buried under reams of other information. :confused: I need a distillation of exactly this info to just get started.

Thanks much for useful advice.

---

### Post by Pumalite on 2008-08-06
Boot an Ubuntu Live CD and post:
sudo fdisk -lu

---

### Post by SarahKH on 2008-08-06
Your C:\ is where???  Hmm.  Okedokey. :)

First thing to do is to figure out what that drive is in Ubuntu terms.  Is it /dev/sda? sdb? or what.   Figuring this out should be simple.  Boot the full flavour livecd, crank gparted and start flicking through the available drives in the drop down; don't change anything :)

Eventually you'll spot this devilish device.  Jot down the name of it and the partition number (counts from 1) so you'll end up with, hypothetically, /dev/sda2 on a bit of paper.

Reboot or just run the installer from that environment and when it comes up to the disk partitioning bit select Manual.  Aim for '/dev/sda2' and tell it to a) format to ext3 (just to be safe) and b) mount as '/' (aka root of the file system in Linux terms).  That's the simplest option without getting gparted out and fooling with the partition table.

Take a deep breath... and get annoyed as it moans about not allocating swap space :)  Ignore or go back, fiddle with this ext3 partition (delete it, remake it smaller, add another one for swap, yadda yadda).  Let the installer rip.  Or just tell it to bugger off and install, if you've got over a gig of RAM it shouldn't be a major issue unless you really hammer the machine... but you can add swap later anyhoo.

The next bit will be where the hell to put GRUB.  Personally, I'd slap it on hd(0) but I honestly couldn't tell from that screen shot what drive your system boots from.

I honestly wouldn't worry too much about making ikkle partitions for the various odds and ends; you can do this if you want (using the 'I want swap now' example) but for SOHO levels of use it becomes a faff if I'm honest.

---

### Post by mc4man on 2008-08-06
[U]I wouldn't do any thing till you've done what was suggested in post 2.
[/U]
Acronis is/was showing 2 active partitions (F, G )
Are you dual booting windows with F hidden from G and G hidden from F?

> What options should I choose under the installation in order to achieve the above layout?

Your not going to be very happy with that layout. What is your reasoning behind installing to individual ld's in the first place? 


What is the corsair? It's formatted like a usb flash drive but again is shown as an active partition. (and C )  ?

---

### Post by rpaskudniak on 2008-08-07
My thanks and apologies to all for failing to explain the F-weirdness.

When I bought the 200GB drive from Dell for my dinosaur box (whose BIOS recognized only 128GB) and installed XP, the drive stubbornly kept coming up as drive F.  Dell technicians were unable to figure out the problem so I finally gave up and accepted _**F: as my boot device**_. 

The C: drive y'all see in the screen shot is indeed a 2GB Corsair hanging off a USB port.  I should have removed it before taking that screen shot.

Disk 2, which contains partitions G:, H: and I:, is a MyBook-320GB drive hanging off another USB port.  My intention is to partition it for backups, media, database files & raw devices, and of course, Ubuntu.

Now, back on the subject of the /boot and /swap devices:

Since I cannot configure more than 4 physical partitions on my boot drive, I need to be economical about it.  If I have understood the concept correctly (a dubious proposition in any case :biggrin:) I can create & configure any number of logical partitions within a physical partition.  This is where I need the guidance.

I would want to configure the /swap right away.  Even more important, I _think_ (subject to correction by the family) there should be a /boot [logical] partition separate from the root, not embedded within the root.

Addressing Sarah's advice specifically now:

[LIST=1]
[*]Assuming the EXT3 partition will show up as /dev/sda2, please explain what you mean when you suggest I "run the installer from that environment".
[*]Since I *do* want the /swap space to start with (main memory capped at 640MB), would you suggest I create the separate *_physical_* partition for /swap in advance of the install step?  I could use gparted do this.  (Or I could use Acronis under Windows before booting the Ubuntu.  But that just feels SOOOoooo wrong! [-X )  I would still be within the 4-partition limit.
Or is that a logical /swap partition within the physical Ubuntu partition.
[*]Grub: Yes, that needs to be where Windows will look for it. This is still primarily a Windows box.
[/LIST]
Whew!  That was long-winded of me! :oops:  Still, I need to know all this before I create another debacle on my PC.

And I will post the output of "sudo fdisk -lu", as suggested by Pumalite, in a later posting.

Thanks much for all the ideas.

---

### Post by rpaskudniak on 2008-08-07
As suggested by Pumalite, I have booted from the Ubuntu CD and run the fdisk command.  Here is the output.  I have detached the Corsair to avoid confusion.
[FONT="Courier New"]ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hde: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xca96ca96

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *          63   204812684   102406311    7  HPFS/NTFS
/dev/hde2       204812685   263546324    29366820   83  Linux

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   356675129   178337533+   7  HPFS/NTFS
/dev/sda2       356675130   625137344   134231107+   5  Extended
/dev/sda5       356675193   566403704   104864256    7  HPFS/NTFS
/dev/sda6       566403768   625137344    29366788+   7  HPFS/NTFS[/FONT]


OK, so my boot drive, known in Windows as F:, is: /dev/hde
The primary partition, known as F: to Windows, is: /dev/hde1
The EXT3 partition I created with Acronis is:      /dev/hde2

At the moment, there is no EXT3 partition on the second disk, /dev/sda but, as a total aside, it is interesting that Sarah had expected /dev/sda*[SIZE="2"]n[/SIZE]*, which turned out to be on the non-boot disk.

So Sarah's advice is to format /dev/hde2 when I get that step in the installation.

But when do I get the chance to divide it into the logical partitions I described earlier?   (/boot, /swap, /, /usr/, /var)?

In any case, I am attaching the screen-shot from gparted when describing the boot disk (\F: ).  (.png?  I hope I can see the attachment when I reboot into Windows. :confused: )  The unallocated space you see there is the stuff that the BIOS cannot see.  (For now, I will avoid trying to extend any partition past that point until I have tested a theory about Windows and my BIOS.  Not part of the Ubuntu discussion.)

Thanks much for this help.  If it works, y'all may yet turn me into the Linux monster I yearn to be. :biggrin:

---

### Post by Pumalite on 2008-08-07
Install, go Manual, delete hde2. That will give you a larger free space. In that free space you can create the partitions you want. I'd create just 3 ('/'. /home and /swap), but if you insist go ahead, but put '/' first and /swap last

---

### Post by rpaskudniak on 2008-08-11
Greetings again.

Preliminary reminder: My boot drive is F:, not C:

I have confirmed the safety of extending the EXT3 [physical] partition past the 128GB range of my dinosaurian BIOS.  So the EXT3 partition, where I intend to install Ubuntu is now 91GB.  I have attached the new layout a a graphic. (Working in in Windows now.)  The second drive can probably be ignored until I have a successful installation in place.

If I have understood the advice from SarahKH and Pumalite, I should proceed as follows:

[LIST]
[*]Boot the Ubuntu disk (as normal)
[*]Click on Install (Icon on the desktop)
[*]When prompted, choose Manual Install
[*]In the course of the manual install, I will have the opportunity to create my file systems (and volume groups?) as desired.  I gotta trust y'all on this last item.
[/LIST]

The question was raised about where my GRUB will go.  The most logical place for this, I think, is on the Windows partition on the F: drive; that's where I would get to decide whether to boot Windows or Ubuntu.

Whichever way I do this, I will hold off until I have purchased, installed, and run Acronis TrueImage (to copy into my "Backup" H: partition), to shorten the duration of the possible repeate of the disaster I initially encountered.

Please critique my plans for logic and expeected results.  I realize I cannot plan every blessed [-o< detail at this stage.  I'm just trying to narrow the possibilities.

Thanks much.

---

### Post by Pumalite on 2008-08-11
Don't forget the 4 primary partitions per drive rule. You might have to make an extended partition first and inside that install Ubuntu.

---

