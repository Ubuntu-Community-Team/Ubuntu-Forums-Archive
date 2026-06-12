---
title: "requesting dual-boot grub clean-up help"
date: 2005-09-01
forum: Installation &amp; Upgrades
---

### Post by AndrewStout on 2005-09-01
Hi folks--

First, an apology:  I know that proper forum/mailing list decorum is to make my best attempt to RTFM, and search the archives, and fix it myself before asking for help, and I haven't done that yet.  I'm in something of a hurry to get all set up before the school year starts, and moreover, I'm afraid of screwing something up and making things even worse.  So I wanted to post here before I go off to find the relevent parts of the relevant documentation--but I will be trying to figure things out for myself while I'm waiting (hopefully not long) for all you kind folks to help me.  =)

Now, to my problem.

I've just almost successfully installed Ubuntu on the new machine I built primarily for that purpose.  After much wrangling with a certain inferior operating system and a great deal of repartitioning and re-repartitioning, the actual ubuntu installation went almost flawlessly.

The machine in question has three hard drives, one IDE (hda) and two SATA (sda and sdb).  I have that uncooperative inferior operating system installed (and working) on the first partition of sdb, installed (and re-installed...) before ubuntu, as suggested.  I put /boot in a small partition at the beginning of sda, and have the rest of ubuntu (/, swap, /home, etc...) in an LVM occupying the rest of sda and much of the remaining space on sdb.  hda is to be used as backup storage.  before starting the ubuntu installation process, I set the boot order of the hard disks to be sda, sdb, hda in my BIOS. [1]

What I _wanted_ the installer to do was install GRUB into the master boot record of sda [2], and automagically configure itself to chainload Windows at my request.  What it actually _did_ was to install GRUB onto hda (I hope onto the MBR, 'cause the first partition is 110G...).  The situation now stands like this: using my BIOS to choose the boot disk, I can boot into GRUB by selecting hda.  If I select ubuntu in GRUB, ubuntu boots up and appears to be fine (although I haven't done much more than log in and restart).  If I select Windows in GRUB, it fails to boot--I didn't take note of the error message, but I can reproduce it if needed.  If I use the BIOS to boot sdb, it boots in to Windows just fine.  If I allow it to boot sda it fails to boot--again, I didn't take note of the error output, but it's something along the lines of "failure loading operating system" and I can get it if I need to.  

My sense is that this should be fixable by reconfiguring and reinstalling GRUB (from a terminal in my new ubuntu installation), but I don't know how to do that.  I'm going to research that asap, but I'm afraid if I screw it up I might not be able to boot into linux at all (although the live cd could probably help there...).  If some kindly person or two could tell me how to correctly configure and reinstall grub, I would be most grateful.  Pointers to the most relevant parts of documentation would also speed my clean-up.

The only other thing that might be worth mentioning is that Windows shows two drives I wasn't expecting, both listed as 0 bytes.  I don't know how to get more information about where it's finding those [3], but it'd be nice to set it straight.

Thanks in advance for your help,

Andrew Stout

(footnotes:
[1] not strictly true.  I actually had it set to be sdb, sda, hda, and realized my mistake ('cause I thought it might matter) when the installer offered to install GRUB on the "first hard disk".  I aborted installation, went back and changed the boot order to the one I actually wanted, and began the installation process again from the beginning, reformatting partitions and everything.
[2] At least, I think that's what I want.  I'm still a little fuzzy on how hard drives are organized, but my understanding is that the MBR is a small bit at the beginning which is usually used for bootloaders, and that that's where GRUB typically likes to live.
[3] I'm a Mac person more than anything; experienced using Linux but not administering; in Windows I skate by on pure intuition, which isn't always enough.
)

---

### Post by AndrewStout on 2005-09-02
OK, I've R-ed part of TFM, and I've developed a plan for what I *think* I should do to fix this, but I'd sure like somebody who's done this before check this before I try it.

hypothesized menu.lst:

# set the default entry
default 0

# set the timeout
timeout 10

# potentially other stuff, but probably not

# the first (zeroth) entry is also the default: standard Ubuntu
# this is copied from my current menu.lst, 
# which looks automagically generated?
title Ubuntu, kernel 2.6.10-5-amd64-generic Default
# the next line works, currently, which tells me that the first SATA
# drive is hd1, despite being first in the boot sequence.
# something I read suggested that if the boot sequence of IDE and SCSI
# drives were switched, there would be problems.
# from that I infer that for some reason, IDE drives are considered to 
# come before SATA drives, and by declaring my IDE drive last in my
# boot sequence I've screwed things up
root (hd1,0)
# these lines taken from the current menu.lst
kernel /vmlinuz root=/dev/mapper/lvmvg0-rootlv ro console=tty0 quiet splash
initrd /initrd.img
savedefault
boot

# other entries for ubuntu, which are the same except for different options
# I might want an entry for recovery mode, but I don't think I want
# the duplicates (caused by automagic & symlink?)
# should I be concerned about the automagic stuff?  how's it work? what's it do?

# boot the evil empire
title Microsoft Windows XP Home Edition
# I think this is a problem: as Martin warned me, and also mentioned
# in the GRUB documentation if you look hard enough--MSW is retarded,
# so we have to make it think it's more important than it really is
# (i.e. on the first disk).  But I'm not sure whether I need to swap
# the disk with Windows with the drive specified to boot first, or with
# the IDE drive which GRUB numbers as 0.  I'm guessing the latter.
# next two lines new:
map (hd0) (hd2)
map (hd2) (hd0)
# I think if those bogus mystery drives still show up in Windows, I could
# use the hide command here to hide all the partitions Windows shouldn't
# see. i.e:
# hide (hd1,0)
# ...
# I think this part is right
root (hd2,0)
# these lines taken from current menu.lst
savedefault
makeactive
chainloader +1


# I've checked device.map and it looks right.
# to install GRUB in the right place--the MBR of the first SATA drive?, 
# I think the command I want is:
> sudo grub-install --root-directory=/boot /dev/sda


So, if I replace /boot/menu.lst with something incorporating the changes above, then run the command above, will I be able to boot (into the grub menu) from sda, and into Windows (and Linux!) from grub?  Someone please reassure me (or save me from myself)!

Cheers,
Andrew

---

### Post by AndrewStout on 2005-09-02
A quick report of what actually worked, for posterity (in case anyone's actually reading):

to get windows to boot, the windows menu.lst item had to be changed to:

title Microsoft Windows XP Home Edition
# trick windows into thinking it's on the first disk (sorry excuse for an OS...)
map (hd0) (hd2)
map (hd2) (hd0)
# hide the LVM partitions from Windows, 'cause it's dumb.
hide (hd0,1)
hide (hd2,2)
# don't verify
rootnoverify (hd2,0)
makeactive
chainloader +1

Windows won't boot if it doesn't think it's the only thing on the computer, so we have to use map to trick it into thinking it's actually on the first disk.  grub can't verify that partition, ('cause it's ntfs, maybe?).  Windows was trying to mount the LVM partitions and failing (of course), so I hid them.

The only change to the linux entry is
root (hd0,0)

instead of 
root (hd1,0)

...because if grub stage 1 is on sda, sda becomes hd0, the ide drive hd1, and the other SATA drive hd2.  It's like trying to hit a moving target: the device map was wrong (because I'm booting an SATA drive, but I've got and IDE drive, and evidently that's a problem), so the bootloader got loaded to the wrong place, which in turn made the device map look correct!

Lessons learned:
1. GRUB's interactive shell is your friend.
2. One can learn enough about GRUB to fix it in a (very long) evening
3. ...but it's not for the faint of heart.

I hope this thread will help someone else in the future...

--A.

---

### Post by j.hill on 2005-09-02
You seem to have had much better success than I have with the same problem, so let me tell you my tale of woe and beg for your wisdom.

I had W2K on my computer; I installed a second hard drive, made it the master, and put Ubuntu on it.  I put some mapping lines into menu.lst and it dual-booted perfectly.  It was a time of joy:  I had Ubuntu, but could use an inferior OS when circumstances required it.

Then Ubuntu melted down, for reasons that I still don't understand, and I had to reinstall.  I replicated the menu.lst setup, but I can't dual-boot any more.  When I try to boot into Windows, I get "Error 11:  unrecognized device string".

Several people have suggested reinstalling Grub.  After some research on this and other forums, I have tried the following repair procedures, with no success:

1.  reinstalling Grub with apt-get
2.  Reinstalling Grub from the Live CD
3.  Reinstalling Grub from the Install CD (looked like it was working, but I still can't get into Windows)
4.  Opening a root terminal and doing something complicated involving chroot (in this, as in all of these attempts, I was blindly following other people's instructions)
5.  Adding the "hide" and "rootnoverify" lines to my menu.lst, following your example

Everyone who has needed to solve a Grub problem swears by his or her method, but none of them seem to work for me.  I'm almost, but not quite, at the point of offering a sacrificial lamb or kid to Grub, just to appease the foul thing.  Come to think of it, Grub is part of GNU -- maybe if I make the offering to RMS, he'll intercede on my behalf.

Anyway, you have clearly had better luck both with the process of learning Grub and with bending it to your will.  Any thoughts on what I can do to lift its curse?

---

### Post by AndrewStout on 2005-09-02
I forgot to mention the most important part:

To actually get GRUB on sda (the hard drive I want to boot off of), I had to do
> sudo grub-install /dev/sda

The GRUB documentation suggested that I would need to use --root-directory=/boot, because I have a separate partition for /boot.  This did NOT WORK as intended: I wound up with a NEW boot directory at /boot/boot, with a new /boot/boot/grub inside it.  So I deleted that and tried without the root directory option, and that worked.  It's possible that I only got away with this because the grub directory was already in place in /boot .

--A.

---

### Post by AndrewStout on 2005-09-02
j.hill, I wish I could offer you more help, but the truth is I was mostly lucky--I tried something and after a few tweaks it worked.

"install GRUB" is a confusing directive, because that can mean two different things:
1. obtain GRUB and its utilities from some distribution source;
2. write the GRUB bootloader images to the right places on your disks.

Your post made clear that you'd done the first, but you didn't explicitly mention doing the second.  I used the grub-install utility and it worked for me (see my other post); the grub documentation on their web page lists a few other ways.  Getting the device map right is crucial, and to do that I had to shoot in the dark until I got the grub image on the device I wanted it on, and then used to grub shell to investigate which disks were called what in order to get my menu.lst to work.

The mapping bit to trick windows is also important--I assume you tried that.

The best advice I can offer you is this:
1. read the grub documentation up to the point where it talks about networking;
2. check your device map--important if you're mixing IDE and SATA as I was;
3. use grub-install to get the stage1 bootloader in place on the drive you want to boot from;
4. (figure out how to point it at the correct place for stage1.5 and stage2, which is probably your /boot directory.  I'm not really sure how I did this.)
5. use the grub interactive shell to try sequences of commands to get windows (and linux!) to boot--that is, the mapping trick, rootnoverify, etc.
6. once you figure out the magic sequence, put it in your menu.lst.

All I can say is that this worked for me--I'm really pretty new at this.

Good luck, and I hope this helps somehow,

--A.

---

### Post by ekravche on 2005-09-03
[QUOTE=AndrewStout]A quick report of what actually worked, for posterity (in case anyone's actually reading):

to get windows to boot, the windows menu.lst item had to be changed to:

title Microsoft Windows XP Home Edition
# trick windows into thinking it's on the first disk (sorry excuse for an OS...)
map (hd0) (hd2)
map (hd2) (hd0)
# hide the LVM partitions from Windows, 'cause it's dumb.
hide (hd0,1)
hide (hd2,2)
# don't verify
rootnoverify (hd2,0)
makeactive
chainloader +1

Windows won't boot if it doesn't think it's the only thing on the computer, so we have to use map to trick it into thinking it's actually on the first disk.  grub can't verify that partition, ('cause it's ntfs, maybe?).  Windows was trying to mount the LVM partitions and failing (of course), so I hid them.

The only change to the linux entry is
root (hd0,0)

instead of 
root (hd1,0)

...because if grub stage 1 is on sda, sda becomes hd0, the ide drive hd1, and the other SATA drive hd2.  It's like trying to hit a moving target: the device map was wrong (because I'm booting an SATA drive, but I've got and IDE drive, and evidently that's a problem), so the bootloader got loaded to the wrong place, which in turn made the device map look correct!

Lessons learned:
1. GRUB's interactive shell is your friend.
2. One can learn enough about GRUB to fix it in a (very long) evening
3. ...but it's not for the faint of heart.

I hope this thread will help someone else in the future...

--A.[/QUOTE]

This didn't work for me

---

