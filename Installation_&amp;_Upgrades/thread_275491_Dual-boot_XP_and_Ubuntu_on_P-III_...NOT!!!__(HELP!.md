---
title: "Dual-boot XP and Ubuntu on P-III ...NOT!!!  (HELP!!)"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by tananaBrian on 2006-10-11
Hi,

  I've never installed any version of Linux before and to be frank, I doubt Linux will seriously compete with Windows / MS until the install gets a bit more professional ..why?  Read on...

  I have an only P-III 500 Mhz machine with a newer Seagate ST-something 200 Gb drive and wish only to have Windows XP and Ubuntu on it in a dual-boot configuration.  I have tried many different methods of installing over the course of several long nights in a row ...none work, or only work partially:

- Windows XP install always works, Ubuntu always breaks things, either leaving itself running and not Windows or not running at all (Hangs at 'Grub' upon boot or fails with "Grub State 1.5" and an "Error 18")

- Partition info:  Windows XP given a 136 Gb NTFS partition and then installed successfully (prior to anything else); Linux given about a 62 Gb Ext3 partition and a 2 Gb swap partition, and the leftover turned into a FAT32 partition ...all made primary.

- Ubuntu Source:  A recently-purchased book on Ubunto w/CD (my computer has no DVD drive), v6.06 LTS I believe.

- My trial installations (Windows installed succesfully first as described):

a) Default options on everything, allowing Ubunto to use all remaining space AND allowing it to write the MBR as it (and the book suggests) ...result?  No Windows boot entry, but Ubunto starts fine, other than an annoying endless drum beat that starts at logon and continues forever ...probably an issue with old sound hardware (I have no problem with turning off the speakers BTW.)  I su'd to root and edited the menu.lst to add a rootnoverify (hd0,0) / makeactive / chainloader +1 but had no lucky.  Also tried just root (hd0,0) / chainloader +1 etc but no lucky.  Tried mounting the NTFS disk, but it failed ...probably, as I discovered later, because I have 4k clusters on the NTFS rather than the 512b clusters noted in the mounting example that I read.  Either way, GRUB couldn't kick start Windows with this install.

b) Used Seagate s/w to re-partition for Windows (slightly different size).  Installed Windows w/NTFS again, then tried manual partitioning during the Linux install, breaking up the non-NTFS partitions into 32Gb size ones and the remaining given to the swap ...otherwise just like option a) above.  Same results.

c) Same as b) but decided not to write the MBR during the Ubuntu installation ...but forgot to make the Ext3 partition bootable.  The system tries to start Windows then blue-screens and says it found a non-bootable partition.

d) Same as c) but made the Ext3 bootable this time, did the same manual partitioning as in b) above.  Now the system comes up and ignores Windows and hangs with 'Grub' on the screen... no 'Stage' anything, no errors.  I believe that it's wanting to finish the final stage of the installation but can't help tripping over itself.

I suspect that even though the last attempts were NOT writing the MBR that the Ubunto installation is still doing 'something' to the Windows partition.  I kind of expected that Windows would boot normally and that I'd have to set up NTLDR / boot.ini to add Ubuntu as a second boot option ...but I got 'Grub' and a hang instead!

Other than try some other outfit's Linux, I really don't know what to do next ...I've got about 18 hours into the effort so far and really wish that I knew what was wrong.  I suspect that the Ubuntu installation probably 'knows' what's wrong but isn't telling me ...and it seems odd that so much trouble arises from a simple dual-boot situation.  I'm not sold yet... but I'm trying (and trying and trying.)  Fedora anyone?  Sorry for not having better details...

Thanks,
Brian

---

### Post by John.Michael.Kane on 2006-10-11
v6.06 LTS was updated to 6.06.1,and had corrected some known issues.

Durring the install the ubuntu cd should have seen your windows partition,and offered you the option to add it to the grub menu. 

There are users who have had issues with the live cd and partition set up.

Is the ubuntu cd your using the live version?

Also can you download the alternate install cd?

---

### Post by tananaBrian on 2006-10-11
I might be able to d/l the latest version, but I have to check and see if my machine here at work has something that will burn an ISO file to a CD/R ...I have only dial-up at home and a noisy phone line.  If I don't have ISO burning s/w at work, then I'm out of luck since we are not allowed to install s/w on our machines (tightly controlled environment.)

What is the "alternate" version?  What is 'alternative' about it?


In answer to your questions however...

No, it's not a Live CD install.  It comes up expecting to install a normal desktop version, but at the 'boot:' prompt, you can enter 'server' if that's what you want ...as well as 'expert' and various other options to allow a bit more control over the installation process.

Yes, on the screen that offers you the opportunity to write the MBR, the text does mention that Windows XP Home was detected on the machine ...but on the trials where I allowed writing the MBR, the menu.lst (or boot screen) never mentioned Windows and I had to add it manually as described previously (which failed ..booting Windows looks like Windows tries to start but then the machine rebooted itself ...later, when not writing the MBR, it blue-screened instead.)  When not writing the MBR, I have not yet been able to get logged into any operating system ...so no obvious way of checking menu.lst or a boot menu.

Sooo ...your suggestion is to find the 'alternative' ISO, burn it to a CD, and try that?  Any other ideas?

Thanks,
Brian

---

### Post by gn2 on 2006-10-11
If it's possible for you to add an additional hard drive (doesn't have to be too big or expensive) you could try this:

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

You could create a Fat 32 partition on the existing large drive to store files for both OS's
.

---

