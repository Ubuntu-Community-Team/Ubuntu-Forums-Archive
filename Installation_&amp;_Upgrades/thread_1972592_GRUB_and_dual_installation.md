---
title: "GRUB and dual installation"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by loseby on 2012-05-03
My setup at the moment is a SSD drive that has Windows on it and a 1TB Sata III drive that holds my docs/pics/music etc but still has plenty of room on it.

I have 2 options
                 .... install on the SSD along with Windows but as the SSD is only 240GB am hesitant

                 ..... install it on the Sata III drive, partition the drive into 2 500GB partitions and use one for Ubuntu

Questions :

What size foot print would 12.04 make on the SSD ?  Can you still have your home folder installed on a different hard drive ( in this case would still partition the sata III drive into 2 )? Basically will do what I do with Windows.....have the O/s on one drive and data on another ?

Will 12.04 take advantage of a SSD drive or even a 6Gbs hard drive ?

Any suggestions about the above welcomed?

As for GRUB, am just getting info before I start. Whatever option I select I want to edit GRUB so that Windows is the default bootable drive. How do you edit GRUB ? Is there a nice easy program  :-)  ?

---

### Post by darkod on 2012-05-03
The default desktop install takes around 4.5GB. But the recommended size for the root partition is 15-25GB, even more if you need to install many and large programs.

Yes, you can have /home as separate partition on the same or another disk. To install with separate /home you will need to use the manual install method (Something Else).

Ubuntu should make use of the SSD speed, even more than windows because in general it works better with the resources.

As for grub2, there are some GUI tools, but it's also easy to control the default OS in the grub2 config files. After all, how often do you change the default OS? I don't see a reason to start adding applications that you will use once or twice...

---

### Post by loseby on 2012-05-05
problem is I have no idea how to play with config files for GRUB  :-)

atm major problem is getting the BIOS to boot to an USB stick  .. getting used to these new BIOS in Gigabyte Z77 is confusing at times


[COLOR="RoyalBlue"]edit...not sure what has happened but when I booted from a DVD it told me it couldnt find any other o/s on this PC
                        ...so I decided to wipe out my 1TB drive and use that ( I had previously backed up the data top another drive just in case) , ANYWAY HAD TO CREATE A PARTION AND SELECT A FILE SYSTEM AND HAD TO DO SOMETHING WITH SWAP AND ROOT... no idea what I had to do[/COLOR]

 Well now its sit back and wait and see what I have done

---

