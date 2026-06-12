---
title: "grub errors on reboot (15/17/18)"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by oldsoundguy on 2007-12-18
I am using the same 7.10 disk that I used on two other machines in an attempt to get a third machine up and running.  (other machines loaded just FINE!)
This is an OLDER machine.  Have re-set the bios on the drives  to everything imaginable .. no go.
SINGLE install .. no Windex on the box.
used the second option on the loader (full disk)
used the advanced tab when partitioning and loaded the bootloader (supposedly).
still get the errors and it stops when I try to get into the install.

NOT A CLUE as to what is going on here, but surmise I have to set partitions manually.  Now as to HOW to do that .. again, most of the answers here are in geek speak with no actual entry samples.

I am NOT a newbie to Linux nor to Ubuntu .. just can't figure out WHY this will not load on a totally empty 80gb hard drive properly.

---

### Post by Pumalite on 2007-12-18
Need to know memory and graphics. Post them.

---

### Post by oldsoundguy on 2007-12-18
running 1 gb of 133 on a p III 733

ATI 9800 graphics card.

---

### Post by Pumalite on 2007-12-18
Download the Alternate CD from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'
Install

---

### Post by oldsoundguy on 2007-12-18
Thanks for the try, but the alternative disk is LOADED with errors.  Any idea of where I can get one that WORKS?

---

### Post by confused57 on 2007-12-18
Grub error 18 may be the main culprit, especially with an older bios, and depending on the size of your hard drive:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

You could try a smaller root partition(approx 10 Gb), and the rest for /home & swap...first you might want to use Gnome Partition Editor on the Ubuntu live cd to delete your current partitions...install Ubuntu, selecting "Manual" partitioning.

Here's an excellent link for installing with the alternate cd(you can ignore the dualboot Windows reference), the screenshots are excellent for what you need to do:
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

Ubuntu desktop live cd guide:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by oldsoundguy on 2007-12-18
> **confused57 said:**
> Grub error 18 may be the main culprit, especially with an older bios, and depending on the size of your hard drive:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

If you would note above .. PIII 733 with 1gb 133 ram and an 80gbhd .. so the above is not the problem as far as I can see it.

You could try a smaller root partition(approx 10 Gb), and the rest for /home & swap...first you might want to use Gnome Partition Editor on the Ubuntu live cd to delete your current partitions...install Ubuntu, selecting "Manual" partitioning.

and what next?

Here's an excellent link for installing with the alternate cd(you can ignore the dualboot Windows reference), the screenshots are excellent for what you need to do:
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

finally got a copy with matching checksums .. will try again with it.

Ubuntu desktop live cd guide:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

If you will read above, I have used this same exact disk to install the system on two other computers.
The problem is in grub on this particular box
I installed Fedora 8 Live and it installed and re-booted without a problem .. just that the Fedora system is weak at best when it comes to hardware and to installing additional software.  Ubuntu is the preferred system.
Tried installing Mint also .. same grub results.

---

### Post by oldsoundguy on 2007-12-19
well, the fully tested special disk took an inordinate amount of time to install and I still have the same grub error 18.  

so ... what next?  (in steps I can understand and assume that I have NOT done the function that I should do.)  step by step and in terms understandable by most, PLEASE!

---

### Post by confused57 on 2007-12-19
> **oldsoundguy said:**
> well, the fully tested special disk took an inordinate amount of time to install and I still have the same grub error 18.  

so ... what next?  (in steps I can understand and assume that I have NOT done the function that I should do.)  step by step and in terms understandable by most, PLEASE!

For now, rather than reinstalling, you might try resizing your Ubuntu root partition to something like 15 Gb...you can use gparted in the Ubuntu desktop live cd(System---Administration---Gnome Partition Editor).  Resize your root partition to approximately 15 Gb...see the screenshots here:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

If you used the "Use entire disk" when you installed, your partitions should look something like:
/dev/sda1  large primary partition for root(your Ubuntu install)
/dev/sda2  extended partition (contains the logical partition /dev/sda5)
/dev/sda5  logical partition for swap(/dev/sda5 is actually a logical partition within the sda2 extended)

See the screenshots, but what you would want to do is left-click on your /dev/sda1(or possibly /dev/hda1) to select it, then click on Partition in the menu at the top, then select resize.  You can then move the slider by clicking & holding down the left mouse button, until the new partition is 15 Gb.  Then click on Apply to execute the resizing.

This will leave a large chunk of unallocated space, but don't worry about this now...when you're finished resizing, then try to boot your computer.  If your computer boots, then there is a bios limitation for booting an OS.  Don't worry, your unallocated space can be used as a /home partition when you reinstall or you could set it up as an ext3 data partition.  The important thing is to see if your computer will boot now.

---

### Post by oldsoundguy on 2007-12-19
THAT GOT IT!!  Partition size reduction ... hmmmm must be the bios as you noted.

THANKS!

---

### Post by oldsoundguy on 2007-12-19
well, that DIDN'T get it for long .. after doing the updating, I re-booted and this time got the GRUB  Error 18 "selected cylinder exceeds maximum supported by bios"  So I took the partition  down to just under 6mb and still have the same message .. drives set for auto.   Got ME snowed .. and re-installing .. AGAIN???  

I do NOT know how to create the separate boot partition during an install, but maybe some kind soul can point me in the right direction and we can try again.

This is REALLY frustrating as the other two boxes I installed went flawlessly! (and work GREAT!)

---

### Post by Pumalite on 2007-12-19
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by oldsoundguy on 2007-12-19
did a re-install on a less than 6gb partition and now I get error 17 in Grub.  This is NUTS! 
Will try again tomorrow.  

Since I am not the ONLY one having this issue, is there an off chance that it MIGHT get addressed in an update or in the next build?

---

### Post by oldsoundguy on 2007-12-19
OK ... MY BAD!!  Thought that just the detection in bios was supposed to be set to auto .. but NOOOOOO  All HD detection is to be auto (including what is normally user!)  NOW it works!
(so the bios screen shows drives as auto AND auto in the changeable columns!)

Sorry I wasted so much time and effort.  Maybe someone else will benefit from this merry-go-round.

Thanks to those that offered their assistance .. it was a learning experience to say the least!

---

### Post by psusi on 2007-12-19
Sounds like your bios can't see beyond 8 gigs, so just make a 100-150 mb partition at the start of the disk and mount it as /boot.

---

