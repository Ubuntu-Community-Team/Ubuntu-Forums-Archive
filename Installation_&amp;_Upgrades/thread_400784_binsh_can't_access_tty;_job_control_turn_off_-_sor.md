---
title: "/bin/sh: can't access tty; job control turn off - sorry"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by bitphire on 2007-04-03
I know this has been talked about quite a bit already but almost everything I read is for people with Ubuntu already installed or at least able to get into the LiveCD. I used this LiveCD to install on my Laptop and it worked with out an issue. After, playin around for a couple week's decided I wanted to add it to my PC. I have Vista already installed but it's ready to be deleted and reinstalled. So I was going to put Ubuntu on the PC and just play with it for a while before actually setting it up for Dual-Boot. I put the CD in the drive and it boot's fine. I tell it to start the LiveCD and it try's but then it die's at the

/bin/sh: can't access tty; job control turned off
(initramfs)

It's trying to boot the LiveCD so don't know what I could change to fix the issue. I am using and IDE CD-Rom drive and an SATA Harddrive. I do have an adapter to force IDE to SATA and might try that. Maybe it's confusing the 2 drive since most people with this issue say there menu.lst is wrong. If anyone has an idea on how to get more info on the error or a fix I would be very appreciated. I would love to work on becoming a full time Linux guru. Again, only been using Linux for about 2 week's tops, so I am very n00bish. So if you give a suggestion, try to give newbie friendly step-by-step instructions.

Thx

Installing 6.10
Intel motherboard (can't think of name)
Asus nvidia 7900gs
e6300

---

### Post by SishGupta on 2007-04-03
When i had this problem it was because my menu.lst was wrong and grub couldn't find the kernel so it dropped me to the line you are talking about.

Your situation sounds like a bug, I would try the feisty beta live cd and see if you still have the problem.

---

### Post by bitphire on 2007-04-03
Not sure I could mess with the menu.lst since I am just trying to boot into the LiveCD. I know the CD works because it worked fine with my laptop so I don't see how it would be the kernel unless I have a hardware issue that is causing it issues. I could be way off but this is what I am guessing.

About to use my adapter to get them both my CD-Rom and HD on SATA. Will post back in a few min on any changes that may or may not happen.

EDIT:
The only CD-Rom drive I have available doesn't fit with the adapter I have. :( The power cable is pushing up against it and pushing the adapter off the pin's so it's not getting a good connection. Gonna try a different LiveCD when I get the chance but have to download one and then burn.

---

### Post by Pseudo-Morph on 2007-04-07
I have this same issue attempting to install Kubuntu from the Fiesty beta release. This disc does work as I was having HDD problems a week ago and used the live CD until I replaced the SATA cable that had gone haywire.

A small amount of testing has shown that the live CD will run while my SATA drive is unplugged however it will give the tty error when the drive is plugged in, this drive already has Ubuntu Edgy installed so it could well be a Grub error.

Might just wait until the final release to see if there is a change as I really should be writting essays (damnit).

---

### Post by bitphire on 2007-04-08
Well, the motherboard I have only has 1 IDE port which is what my cd-rom is hooked into. I then have my 80GB SATA drive and a 300GB IDE with a SATA adapter because 1, the IDE cable doesn't fit with my case, and 2 because one of the pins is a little messed up so I leave the adapter on so it doesn't get moved or knocked around. I tried unplugging the 300GB drive and leaving only the cd-rom and 80GB drive but that didn't work either. Really wish I could figure it out.


EDIT:
I tried some more googling and I found the "more casper.log" and it gives me some info but mostly error's. I think they all occur because of the first one. Here are the first couple of lines:

mount: Mounting /cdrom on /root/cdrom failed: Invalid argument
chroot: cannot execute debconf-communicate: No such file or directory
chroot: cannot execute /usr/lib/user-setup/user-setup-apply: No such file or directory
chroot: cannot execute debconf-communicate: No such file or directory
/scripts/casper-bottom/10adduser: /scripts/casper-bottom/10adduser: 48: cannot create /root/etc/environment: Directory nonexistent

Hope that is enough because that's a lot of typing :P


EDIT EDIT:
Also read some one had the error because of an unsupported cd-rom drive. I just swapped the one I had with a different one but it still failed to mount it (casper.log said so). They are both DVD-ROM's only no burner. My original is quite old but the second one came from my GF's PC and it is newer I believe but it's all I have at my disposal at the moment. :/ Will keep the search going.


EDITx3:
This pretty much is my output with the casper.log and when I run:
 set -x
 . /scripts/casper
 mountroot
 
The output is the same as in the post:
[https://launchpad.net/ubuntu/+source/casper/+bug/62679](https://launchpad.net/ubuntu/+source/casper/+bug/62679)

They said that acpi=off worked for them but does not seem to be working for me.

---

### Post by bitphire on 2007-04-08
I turned the quiet option thing off and I am seeing sdc: sdc1 and it talks about scsi disk sdc but I don't use scsi so I assume this is also for SATA and then I see:

cp: unable to open '/root/var/log/': no such file or directory
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or directory
Done.
mount: mounting /sys on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init


Then I get my BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [ 123.567271] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection



Any idea's of getting more information that might be useful would be appreciated :)

---

### Post by bitphire on 2007-04-08
Well, downloaded 7.04 and it booted into the LiveCD on the first try no special anything. Not sure why 6.10 wouldn't do it. Would still like to figure it out.


EDIT:
This edit is from my PC with 7.04 installed on it. Seem's to be working fine so far so I might just use this over 6.10. Feel free to post some solution for my above issue just in case it might help some one else. :)

---

