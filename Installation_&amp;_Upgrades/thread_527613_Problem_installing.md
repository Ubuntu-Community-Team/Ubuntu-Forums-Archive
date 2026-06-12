---
title: "Problem installing"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by aggierandy on 2007-08-16
I am attempting to install Ubuntu on my HP Pavillion xt963 computer. I have added ram and a new hard drive. The original problem with the computer was hard drive failure. I attempted to install using an old copy of 6.06 that I had to no avail. I then downloaded and burned a copy of 7.04 live CD again no luck. I am currently using the alternate CD and it seems close. I install using text mode and get through with partitioning. When the install of the base system begins I get the following message:

[B]Warning:
file://cdrom/pool/main/popt/libpopt0_1.10-3build1_i386.deb was corrupt
[/B]
I hit continue and get the following message:

[B]Warning:
file://cdrom/pool/main/r/readline5/lebreadline5_5.2-2ubuntu1_i386.deb was corrupt
[/B]
I hit continue again and get message:

[B]Debootstrap Warning
Warning: couldn't download package libreadline5
[/B]
I hit continue get message
[B]
file://cdrom/pool/main/n/net-tools/net-tools_1.60-17ubuntu1_i386.deb was corrupt
[/B]
I hit continue

[B]Warning:
 couldn't download package net-tools
[/B]
this continues and gives more errors
[B]
file://cdrom/pool/main/u/util-linux/mount_2.12r-17ubuntu2_i386.deb was corrupt

Warning failure to run: chroot /target mount -t proc proc /proc

The debootstrap program exited with an error (return value 1)
Check /var/log/syslog ot see virtual console 4 for details

Base system installation into /target/ failed
Check /var/log/syslog or see virtual console 4 for details

An installation step failed you can try to tun the failing item again from the menu, or skip it and choose something else. The failing step is: Installing the base system[/B]

Then I am taken to the Ubuntu installer main menu

I burned the disc at the slowest speed on my burner and everything seemed ok. Any suggestions. TIA

---

### Post by aggierandy on 2007-08-16
I just ran the check for CD defects and it notified me of the problem. Probably should have done that before the install. How do i fix this then!!

---

### Post by merlinus on 2007-08-16
Your downloaded .iso file may be corrupt.  You can do a checksum.

Info here:

[http://www.psychocats.net/ubuntu/iso#checksum](http://www.psychocats.net/ubuntu/iso#checksum)

-merlin

---

### Post by aggierandy on 2007-08-16
Both files checksum fine

I have burned both the live cd version of 7.04 and the alternate. I burned them the first time at 4x and the second time at 2x. All times the burns resulted in problems. Does this mean that there is a problem with my burning drive or do i have an issue with my installation computer's drive. 

Any help? Thanks again

---

### Post by merlinus on 2007-08-16
Anything is possible.  Did you perform the checksum on the downloaded .iso file to make sure it is not corrupted?

-merlin

---

### Post by aggierandy on 2007-08-17
Yes i preformed a checksum on both .iso files and they both were ok. I am lost on this one. Can I try an install from a usb drive if there is a burning problem? How can I do that and is my comp capable of it?

---

### Post by merlinus on 2007-08-17
Perhaps you can copy the .iso to an external drive and burn it on a friend's computer.

-merlin

---

### Post by NdJ on 2007-08-18
I can confirm I'm having very similar problems installing 7.04 Server.

Summary of my situation:-

** Downloading from -- [http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso)
** Confirmed downloaded iso has correct checksum -- 8a1099f5fa8eaf4ee295bf0087c8b03a
** Created 3 different CDs from this .iso file on three different machines/burners/software

The install appears to break on the same file each time, in my case:-
** dpkg_1.13.24ubuntu6_amd64.deb (claimed to be corrupt)

From the install CD in the md5sum.txt file at /cdrom/md5sum.txt this file is supposed to have an md5sum of -- f5e6f8ee1cafab0b89ab351855cbcb4b

Jumping to another screen and getting the busybox shell I'd like to be able to check the md5sum of the file however the md5sum implementation that comes with busybox exists immediately without computing it -- md5sum will however calculate the md5sum for other files this immediately feels fishy...  If I manually check the md5sum of the file from a different machine it calculates and matches correctly.

Reviewing /var/log/syslog shows that I'm getting loads of "Buffer I/O error on device sr0" -- my suspicion is that the CDROM drive is somehow faulty -- planning to swap the drive out and re-test.

This is on a new Dell 2950.

N

---

### Post by NdJ on 2007-08-18
After swapping out the CDROM drive (and associated Dell subassembly with cable) my issue has resolved -- it would appear this is a hardware problem with the CDROM itself.

N

---

### Post by super carrot on 2007-08-18
Well I have been having a real nightmare and I just hope someone can help me out! Every ISO I download, no matter what method, bittorrent, wget, http, ssh ( download it on another computer then transfer it to this one.) It always seems to be corrupt. I have never seen anything like this before. Its as though the moment it hits my file system it corrupts. I have tried it with Feisty 64 bit, then I decided to mess around with Gutsy 64 bit. Well of course this didn't solve my problem, but that is what I am running now. I md5 check iso's and sure enough they are corrupt. I even tried using jigdo so that it will build the ISO locally. I did, it took a really long time, then was corrupt. Please help, what could it be? The corruption is not to do with how I burn it because I usually use the images for vmware of qemu.

---

### Post by super carrot on 2007-08-18
I think that I might have found a way around my problem. I mount a ramdisk and copy or unpack my file on to that. It seems to be ok when I do that.

There seems to be a problem with copying ISO's on to my disk, anyone heard of this sort of thing before?

---

### Post by barnabear on 2008-03-20
Hmm ... I ran into similar problems while trying to install a minimal command line system using both Gutsy and Feisty alternate CD's. It was a real puzzle, and no matter what I tried for a long time I couldn't crack the problem.

The CD's would pass the "check CD for defects" test, but would always fail with a corrupt file message in Debootstrap (whatever that is).

Eventually I found that it did work with a Samsung CD-RW drive, but not with an LG multi-format DVD writer, or a DVD-ROM drive.

I reasoned that this seemed to be some sort of incompatibility between media and individual drives that showed up only under the stresses of the Debootstrap program.

It occurred to me that the drives I had supported DVD's, and that DVD+R is arguably the most compatible optical format. Therefore I [COLOR="Blue"]burnt the ISO onto DVD+R[/COLOR] instead of CD-R.

That seemed to fix the problem, so you might find the same works for you. Won't work if your drive doesn't support DVD's though.

So, from now on, I intend to use DVD+R media in preference to CD-R.

---

