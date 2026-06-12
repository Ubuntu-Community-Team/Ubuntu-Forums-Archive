---
title: "Computer wont boot after misuing gdisk or Windows Boot Repair"
date: 2018-12-08
forum: Installation &amp; Upgrades
---

### Post by kilolima2 on 2018-12-08
Hi!

After recieving an error in Gparted that "The backup GPT table is corrupt, but the primary appears OK, so that will be used" I thought there was an issue with the main disk (/dev/sda). I think that Gparted was actually just referring to a USB drive.

Following a sketchy guide on the 'Net, I ran 'gdisk -f' and selected Y in order to restore the partition table or something (doh!). After that on reboot the system failed to start, showing only a blinking underscore cursor in the upper left corner of the screen.

It may also be possible that Windows Boot Restore did something to the drive, for the first time in years I had the Ubuntu SSD in the same machine as a broken Windows desktop trying to diagnose Windows 7 startup issues on a 2nd drive. (I swear I don't use Windows normally!)

I ran the live-USB for Boot-Repair and it posted this to pastebin: [report]("http://pastebin.ubuntu.com/p/HF5yPCSX4j/") but did not fix the issue.

Any ideas how to proceed next? The drive is mostly backed up but of course there's some unbacked-up Postgresql databases...

Please note that /dev/sda is also using full-disk encryption.

Cheers!

kilolima

---

### Post by oldfred on 2018-12-08
It looks like you converted from MBR(msdos) to gpt.
But /boot partition has same UUID, so that is ok, but grub in gpt's protective MBR cannot find core.img. 
The gpt partition table is right after MBR where grub normally puts core.img. 
With gpt and BIOS boot you need a 1 or 2 MB unformatted partition with the bios_grub flag. Use gparted & shrink your /boot slightly.

Then reinstall grub in BIOS mode.
You can use Boot-Repair's advanced option, but be sure to mount your encrypted file system first and use advanced mode to do a full reinstall of grub, so it resets menu entries and everything else.

       Converting to or from GPT - probably what you did, may be a little late to read instructions.  :)
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

