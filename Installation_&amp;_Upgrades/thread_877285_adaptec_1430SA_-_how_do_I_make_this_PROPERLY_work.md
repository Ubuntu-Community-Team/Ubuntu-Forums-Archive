---
title: "adaptec 1430SA - how do I make this PROPERLY work"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by b_i_g_g_s on 2008-08-01
Hello,

I am trying to install 8.04 onto a raid10 volume I have created on an adaptec 1430SA.

currently I don't understand much about linux, so please be don't be offended if I get frustrated (I assure you it is with my own ineptness and nothing else) or don't understand what your trying to say.

currently when I am in the installer it sees the each disk and not the raid volumes.

I was given the impression that I should be able to load a driver to make linux BLIND to the disks so that it will only see the raid volume. 

dmraid and software raid are not the answers I am looking for. and are the only answers I am finding.

I am looking for either a step by step way to get this 1430SA to work properly by getting the driver installed or getting a new raid card that will do what I want.

I don't want to have to do anything in ubuntu w/ any sort of raid managing util. I just want to setup the raid volume on a raid cards bios and when it boots have the ubuntu installer just see that volume.

a) can this be done w/ this card
b) if not -a- do I need a 3ware to do this?
c) is this a pipe dream ? and am I doomed to not beingable to do this? (this being just having a driver that JUST works). is there a card that works how I want it to? or do all cards need dmraid or some other management util to make them work no matter how "good" a card they are?


I won't mind spending the ~340 for a 3ware card if it means it will just work. I have other things I would rather be doing with my time then batteling with getting hardware to work properly in an OS I am not comfortable with.

ideally I want to setup the volume in the bios, reboot, run the install for ubutnu have it see the raid volume (not every disk attached to the raid card), use the guided partition, have that work, finish the install and get on with my life.

---

### Post by b_i_g_g_s on 2008-08-03
ok,


so no one knows how to pass boot prarmaters to make it so I can acutally load a driver for the install..... anyone? anyone? anyone?



someone one what to break down how this card is SUPPOSED to work in linux?


is ubuntu supposed to see it as a single scsi device? or am I supposed to have to fakeraid or software raid w/ this card?





ANYONE shed some light on this for me?

---

### Post by method_ on 2010-08-02
Hi everybody.
I'm totally new to Linux. I've got the same problem. Is anything changed since 2008 with 1430SA and Ubuntu?
I have 4 500GB hard disks with RAID 5 and Windows installed. Also I made a different partition under Windows. But screenshots show what I get when trying to install Ubuntu 10.04 amd64 (alternate or not) on it.
The error message says:
```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=808117309440, size=-308009447424, type=
Entering MS-DOS parser (offset=0, size=500107862016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 808117277184, type 0x07)
new part entry
looking at part 1 (offset 808117309440, size 191805304320, type 0x83)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
Error: Can't have a partition outside the disk!
ped_disk_new() failed
```
So the question is, what I need to do to install Ubuntu on separate partition, keeping current Win installation alive?
Thanks in advance.

---

