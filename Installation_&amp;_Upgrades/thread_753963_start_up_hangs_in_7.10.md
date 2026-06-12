---
title: "start up hangs in 7.10"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by linux_challenged on 2008-04-13
I posted this question some time back and didn't receive any responses so I am posting it again.

I am trying to install Ubuntu on an older Dell Inspiron 8100 laptop with 512 Mb of RAM. I already run XP pro on this laptop and have no problems with it. I have tried Ubuntu 7.10, Xubuntu 7.10 and 7.04. I have also tried 7.10 Alternate but didn't understand the methodology with the alternate version.

Basically, the issue I am having is , on startup, the system stalls at the point in the initialization where it is trying to load the common unix printing system. It will start once or twice okay, but after that it starts hanging up.

There were no indications during the install that there were any problems. I ran the md5checksums against the ISO file when I downloaded it and the comparison matched. I also ran the integrity check at installation and there were no issues there. The livdCD starts up and runs okay. I am at a loss how to resolve this.

Does anyone have any ideas about what would cause this? I am kinda new to linux but have Mandriva running in dual boot on another laptop with no issues. I would ultimately like to install Xubuntu on the i8100 since it is kind of getting old but runs perfectly.

thanx in advance for any help...

---

### Post by Pumalite on 2008-04-13
Your problem is that you are still trying to install with the Live CD. Alternate CD is the way to go for you.

---

### Post by linux_challenged on 2008-04-13
okay, I am using the alternated cd method...

when I get to the partitioning section, I get an error message - something about due to an unknown reason, the existing partition cannot be resized...

what does that mean? this is a 60G hard drive with xp pro using around 7G total including files, etc

---

### Post by Pumalite on 2008-04-13
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP, choose 'resize' from the menu.

---

### Post by linux_challenged on 2008-04-13
okay - got the gparted live cd...

when I resize the windows partition, will I then be able to reformat the freed up space to ext3 (is that the correct partition type) for the ubuntu installation?

also, I am assuming that when I start the installation, I will be able to indicate that I want to use the ext3 partition for the installation - am I  correct in this assumption?

---

### Post by Pumalite on 2008-04-13
In the free space make 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.
Install Ubuntu, go Manual and use already prepared partitions.
Ext3 is fine. Swap has it's own format.

---

### Post by linux_challenged on 2008-04-13
I am not sure what this means but I used partition magic to explore the existing partitions and there are 2 primary partitions: the first one is formatted NTFS, is about 58G is size - this is the xp partition; the second one is a little over 7G in size but that is all I can find out about it other than it is "unallocated".

I am wondering if that second partition is some hidden windows junk.

At any rate, I think I can only have 4 primary partitions - is that correct? If so, should I create a third primary partition, and further define that into logical partitions and set up as you described?

---

### Post by Pumalite on 2008-04-14
The third should be an extended partition and within that you can stick as many logicals as you want.

---

### Post by linux_challenged on 2008-04-15
I have been playing around with the Gparted LiveCD to familiarize myself with it and noticed it absorbs the  small 7.8 MB primary partition at the end of the disk during the resize operation.

Is that okay or is this a partition I should leave alone? If so, how do I get around the absorbtion thing?

 I can't find out if something is stored on it or not or even if it has a purpose,  but one never knows what kind of sneaky stuff M$ does

---

### Post by Pumalite on 2008-04-15
That might be a 'recovery' partition, so be careful.

---

