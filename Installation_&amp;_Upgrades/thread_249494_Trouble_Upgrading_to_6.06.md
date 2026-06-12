---
title: "Trouble Upgrading to 6.06"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by James_Nostack on 2006-09-02
I want to complete my upgrade from 5.10 to 6.06, but I am not sure how to do so.
  
* The computer no longer recognizes my CD-ROM drive.

* The computer does not recognize USB memory sticks.  (It does recognize my USB mouse, for some reason.)

* My update manager and package managers appear to be messed up (details below).

* The Applications menu doesn't open, which is how I get to terminals.

I am not sure how to upgrade if I don't have a CD, USB memory, the built-in upgrade utilities, or a terminal.

===Background===
As detailed in the ["autistic" laptop thread](http://www.ubuntuforums.org/showthread.php?t=248885), I was using 5.10 fine.  Then I tried to upgrade to 6.06, but each time, the computer crashed mid-way through.  Eventually it gave me strange Segmentation Faults during boot, and couldn't detect /dev/hda1.

I got around this problem by using the 2.6.12-9.386 kernel on GRUB, which at least gets me to my desktop.  But, as mentioned, the machine has problems.

==="Red Circle" Problems===
When I click the "red circle" (by the clock, in the upper right of my screen....
```
The following problems were found on your system.

E: dpkg was interrupted, you must mannual run 'dpkg --configure -a' to correct the problem
```

and I click "Ok," which gives...

```
Could not upgrade the system!  Fix broken packages first.
```

===Synaptic Problems===
When I click on Synpatic Package Manager...
```
Enter password for default keyring to unlock

The applicaiton 'gksu' (/usr/bin/gksu) wants access to the default keyring, but it is locked
```

My usual password doesn't do anything.  So, after a little while, I click "Deny."  Then I get a usual Synpatic password request, but it then asks for this 'gksu' keyring thing again.  After I deny it again...

```
Error - failed to run /usr/sbin/synaptic: Wrong password.
```

I'm not sure what any of this means.  All I want, really, is to finish this 6.06 upgrade, but I'm not sure how.

---

### Post by John.Michael.Kane on 2006-09-02
It looks like your dist-upgrade/system install is corrupt,and most likely your going to have to reinstall.
when upgrading to dapper  it makes many significant changes ie:kernel changes. you can't be downgrade back to breezy. your best bet reinstall your Os of choice.

---

### Post by James_Nostack on 2006-09-03
I seem to have fixed the system, so I'm including this as a "how-to" for any other newbies who run into a similar problem:

My first install to 6.06 took place Monday morning; it crashed midway through.  I rebooted and tried the install again; it crashed again.  Rebooted, tried again, crashed again.

After this mess, I got thousands of Segmentation Faults, and "ALERT!  /dev/hda1 does not exist.  Dropping to a shell!" ...and from there, I had no clue what to do.

I tried putting a CD-ROM in the drive and telling the computer to boot from the CD, but the computer didn't recognize the CD.  (This may be an unrelated problem.)

So, during GRUB 1.5, I pressed Esc.  This put me into a menu where I could choose which kernel I was using.  Apparently, I was using 2.6.12-10.386, which gave me those error messages (I suspect with all the crashes, it either never completed installation, or got corrupted somehow).  But Ubuntu kernel 2.6.12-9.386 managed to work, and got me to the desktop!

Using 2.6.12-9.386, I identified all of my valuable files, and moved them into archives.  (Select a file folder, alternate-click, and choose "Create Archive...").  I then moved the archives to a storage media--e-mailed them to my Gmail account, actually.

With my files protected, I clicked on the "red circle" near the clock, for updates.  (Hoping it would update my system.)  The "red circle" said that dpkg was messed up, and I would have to go to terminal to fix it (it gave me the command to use).

My Applications folder would not open to give me a terminal, so I pressed Alt-F2 and chose Terminal.  I ran the command to fix dpkg.  I ran the "red circle" again, and it gave me some minor upgrades.

Then I looked on the Ubuntu website, and found this--[Upgrade Instructions](https://help.ubuntu.com/community/DapperUpgrades).  I chose to install from a CD, since it seemed the least risky.  Since my CD-ROM drive still didn't work, I downloaded the Alternate CD ISO file, and obeyed the instructions given:

>    1.

      Make sure that you have the package "ubuntu-desktop" or "kubuntu-desktop" or "edubuntu-desktop" installed (depending on the distribution you are using).
   2.

      Edit your /etc/apt/sources.list as root:
          *

            For Ubuntu/Xubuntu:

               gksudo "gedit /etc/apt/sources.list" 

            or for Kubuntu:

               kdesu kate /etc/apt/sources.list 

            and change every occurrence of "breezy" to "dapper".
   3.

      either
          *

            Download the ISO image for the "Alternate Install CD", (not the "Desktop CD", which from my experience today 9th June and that of others in the [WWW] web forum is defective anyway, giving [WWW] all sorts of problems, nor the "Server install CD"), eg from [WWW] here or from [WWW] Torrents and burn it to CD, or,
          *

            Order the (3) CDs to be posted out to you via [WWW] Shippit, and use the "Alternate Install CD".
   4.

      To install from a physical CD
         1.

            Run:
                *

                       sudo apt-cdrom add 

                  Insert the CD, and press enter.
         2.

            Run:
                *

                       sudo apt-get update && sudo apt-get dist-upgrade 

   5.

      To install directly from the ISO image
         1.

            Mount the ISO to /cdrom:
                *

                       sudo mount -t iso9660 ubuntu-6.06-alternate-i386.iso /cdrom -o loop 

                  Using the full path and proper name for the ISO image
         2.

            Run:
                *

                       sudo apt-cdrom -m add 

         3. 

            Run:
                *

                       sudo apt-get update && sudo apt-get dist-upgrade 

         4.

            Unmount the ISO
                *

                       sudo umount /cdrom 

Which worked great!  I had to put the computer on several ice packs, to keep it from overheating, but now it seems to work just fine.  I'll continue troubleshooting to see if there are any other problems.

---

