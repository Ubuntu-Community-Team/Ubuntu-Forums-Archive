---
title: "[SOLVED] How to backup my system before doing something stupid"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by antiOST on 2008-07-16
Hi

I'm relative new linux/Ubuntu (gutsy) user and the last couple of months I've been changing my clients to Ubuntu and I must say I'm impressed so far, so impressed that I - too many times - have dared to mess around a quite deal, sometimes for the bad. 
When I try something and it goes bad I'm not comfortable rolling back the change, sometimes I don't even have a clue of how to rollback and I end up just leaving it be.

Actually right now my system is in a state where I can't update ubuntu and install new applications (I have another post going on [here]("http://ubuntuforums.org/showthread.php?t=858293") which unfortunately haven't got any solution yet).

Before I mess my system up totally, I would like to know if there's some kind of system restore (like windows) that I can use?

-Kim

---

### Post by chris_nava on 2008-07-16
At it's most basic you can backup the whole drive...
If you have a spare hard drive you can create a duplicate disk image by booting from the Ubuntu install disk and using the "dd" command.
    # dd -if /dev/sd0 -of /dev/sd1
    (Be sure to substitute your drive IDs)
You can later restore by swapping the input/output devices.
----
If the backup drive is big enough you can create a disk image as a FILE which you can later mount (making partial restores easier.)
    # dd -if /dev/sd0 -of /mnt/backups/sdo-2008-07-16.iso
----
For things like system settings the "tar" command is your friend.
    # sudo tar -cvf etc_2008-07-16.tar /etc
This creates a backup (like a .zip file) of your /etc folder.
You can later extract just the files you need to restore.

---

### Post by coffeecat on 2008-07-16
I'll second the use of tar. That's what I use. Only earlier this evening I tar.gz'd the whole of my Ubuntu root partition (it only took a few minutes - I do a regular archive) and then did an update. Something went wrong (not important what), so it was the work of a few more minutes to boot into another partition/distro, rm the contents of the Ubuntu root partition, untar the archive back into the now-empty partition and boot back into my restored Ubuntu. And then update again avoiding the issue that came up first time.

One caution. Never tar a partition from within a running system. That is - if you are running from the root partition sda1, don't archive sda1. I tar from another partition/distro or from a live CD.

---

### Post by antiOST on 2008-07-18
Thanks,

It sounds a little cumbersome, to have to boot up on a different system to make my backup and I'm a lazy guy :-) but guess it's gonna safe me a lot of trouble eventually so there's no way around.

Thanks for suggestions, I'll try 'em as soon as I get the time

-Kim

---

