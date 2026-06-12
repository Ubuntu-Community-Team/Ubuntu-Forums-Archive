---
title: "First time installing Linux - ubuntu-5.10-rc-install-i386.iso"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by snteran on 2005-10-07
This is my first install of Linux and I got stuck off the bat.  I have a Dell GX-240 with 512RAM, 40GB HD.

I downloaded and burned the CD, thanks to a posting I realized there is a certain way to burn an .iso file, and began my install. I get to the prompt if I want to install the Default or the Server and I choose Default and then I get the following error:

boot: isolinux: Disk Error 01, AX =4200, drive 82

I searched for and error with drive 82 and found nothing, I did see another posting that recommended using Opensuse but I was hoping to try Ubuntu since it was recommended by someone I know.

Thanks,

Serge

---

### Post by Dennis Laumen on 2005-10-07
It looks like a bad CD/burning error! Did you try the MD5 checksum to see if you downloaded the file correctly (Internet Explorer for instance tends to screw up big downloaded files)?

---

### Post by darkmatter on 2005-10-07
snteran, as Dennis Laumen stated, that appears to be a bad burn. 

First, I would recommend checking the md5sum of the iso. Download the md5sum file, and use a  checking utility such as [MD5summer](http://www.md5summer.org/) to check the iso. if the check fails, the iso is corrupt, and will need to be redownloaded.

If everything checks out, it could just be bad media, or you could have burnt the image at to great a speed.

Try burning the iso again, I recommend not burning at any speed over 8x (4x is good), as some media does not respond well to greater speeds.

---

### Post by snteran on 2005-10-07
thanks for the suggestions, I'll download the md5sum and check the .iso.  I'll report back with any findings.

Regards,

Serge

---

### Post by snteran on 2005-10-07
Well I downloaded md5summer, thanks for the suggestion, and it checked out OK.
So I rebooted and went through Setup and verified boot order to disk and also checked date and time and then tried again and it made it through.
Now during the install, I get to a prompt and select - Finish partitioning and write changes to disk.
After about 30 minutes I get a error "debootstrap program exited with an error (return value 1).
log/bootstrap.log for the details.

Not sure what my next step should be.

Thanks for the help,

Serge

---

### Post by darkmatter on 2005-10-07
snteran. Try again. 

Next time you get the error, check Virtual Console 3 (Ctrl+Alt+3) for messages.

You can tell us what is listed there. If it has any errors regarding the filesystem or blocks, the CD is most likely buggered.

---

### Post by snteran on 2005-10-10
I tried the install again and got the same error, when I tried to "check Virtual Console 3 (Ctrl+Alt+3) for messages", nothing appears.  I then tried (Ctrl+Alt+F3) and I get a command line error - chroot: cannot execute mount...
Not sure what the issue is since I have no Linux background or experience.  I don't want to stop, so I hope you don't mind all my problems and questions.

Thanks,

Serge

---

### Post by darkmatter on 2005-10-10
[QUOTE=snteran]I tried the install again and got the same error, when I tried to "check Virtual Console 3 (Ctrl+Alt+3) for messages", nothing appears.  I then tried (Ctrl+Alt+F3) and I get a command line error - chroot: cannot execute mount...
Not sure what the issue is since I have no Linux background or experience.  I don't want to stop, so I hope you don't mind all my problems and questions.

Thanks,

Serge[/QUOTE]

Sorry about the '3'. I meant F3.

Hmmm...Bootstrap error. That's not good. Hang in there, I'll have a look into it

---

### Post by darkmatter on 2005-10-10
snteran. That sounds like it could possibly be a physical problem with the hardware. How old is the PC you are trying to install on? System specs?

---

### Post by snteran on 2005-10-10
The system is not that old, I just got it off of the Dell Auction site.  

It's a Dell optiplex gx-240 P4, 40GB Maxtor, 24x CD-rom.  I would only guess that the system should be fine.  I have not tried to install any other type of O/S on this system before.  Also, I have a silly question - Usually when I get a system from Dell, I fdisk to partition and format the C drive.  Any special ways I should prep the drive?

Thanks,

Serge

---

### Post by snteran on 2005-10-11
Well I wanted to verify that the HD was OK so I found a document on installing a Dual boot, throwing caution to the wind here, and was able to successfully install.  According to the steps, I should make 3 partitions, first - less than 8gb for windows, then second - linux partition and then third - swap partition.  I go to install Ubuntu and set the install to use ext 3 and use the third partition for swap.  Install appears to be going fine, then I get an error - no root file system is defined.
Help - I really want to use Ubuntu.  I want to learn Linux.  Any adice would be greatly appreciated.

Thanks,

Serge

---

### Post by Dennis Laumen on 2005-10-12
Did you mount the "linux partition" to / (root) in the partitioner?

More installation info can be found here:

[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)

Scroll down to "Partition your disks" and read that bit.

Let us know if you need any more help.

---

### Post by Evandenerley on 2005-10-12
I also have just installed breezy badger for the first time. When i finished install everything seemed fine but when it loads the desktop it looks like a nintendo game when it crashes(lights flashing everywhere). if i type my screen name and then password the desktop definantly boots making a log in noise and the screen changes slightly. I thought this to be a version error so re partition and installed hoary and the same thing happens. Any thoughts on what to do?

---

