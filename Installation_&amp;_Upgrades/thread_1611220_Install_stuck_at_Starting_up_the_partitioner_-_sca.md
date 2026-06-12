---
title: "Install stuck at Starting up the partitioner - scanning disks 47%"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by celub on 2010-11-01
Hi all thanks for viewing my post. Hope you might be able to help.

Dell Inspiron 4100 laptop
1GB RAM
1Ghz processor

Have Oracle Enterprise Linux installed (basically red hat). I resized this to make room for a new partition for Xubuntu on hard drive. Want to have a dual boot.

Tried earlier today with ubuntu-10.10-desktop-i386.iso and gave up as my laptop must be too slow as this just crawled along. After 4 long hours decided to look at Xubuntu.

Downloaded xubuntu-10.10-alternate-i386.iso and created disc.

Booted from cd ok. 

Chose Expert Mode under options F6 so I could see more of what happened.

Got to stage 'Partition Disks' and it just gets stuck. As if the laptop hangs after less than a minute and the CD stops going round.

Left this for 30 minutes and still no go. Tried 6 times and the same each time exactly.

So install stuck at:

'Starting up the partitioner' 
47%
Scanning Disks...

I have installed unix and linux a fair few times but not able to see what is wrong here.

Any ideas really appreciated.

Have tried F6 options at start with no apci etc and no difference.

Cheers Cel

---

### Post by celub on 2010-11-01
An update: Still same issue.

Double checked the iso I downloaded using check sum etc and all looked ok. Hash values matched that at:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Re-burnt to a new CD and re-ran install booting from new CD.

Still same problem. Ejected CD and turned laptop off forcing it by holding down the power button.

Ran check from install menu to check the CD integrity. All files on CD ok.

Be great if someone can tell what command is being run at this stage where I am getting stuck. I could then try to duplicate the issue from the command line and get an error message back etc so I can try to resolve.

11 hours gone into the ether so far. I wonder how many hours we all waste on things like this?

Cheers Cel

---

### Post by celub on 2010-11-01
Well I have tried again and no luck. Still gets stuck scanning disks.

Appreciate any help as needed to have this working for 19:00 today so already behind.

Cheers Cel

---

### Post by celub on 2010-11-02
Hi All.

After issue with hanging at scanning disks, decided to try something else and downloaded the Xubuntu mini iso.

mini.iso

Created CD and booted from it. Install ran to completion. At the scanning disks stage it found the single hard drive and existing paritions from Oracle Enterprise Linux 5.4 (OEL) without an issue.

Now just modifying my grub environment on OEL so I can see Xubuntu at bootup in the list of OS's to boot into.

Will update once this complete and tested.

I logged a question on Launchpad against Xubuntu:

[https://answers.launchpad.net/ubuntu/+question/132159](https://answers.launchpad.net/ubuntu/+question/132159)

and will update this too once complete as I need to carry out a couple of tests for that.

Cheers Cel

---

