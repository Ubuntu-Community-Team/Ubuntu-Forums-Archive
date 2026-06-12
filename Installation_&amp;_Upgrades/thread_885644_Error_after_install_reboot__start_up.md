---
title: "Error after install reboot / start up"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Tarsys on 2008-08-10
I keep getting this error after I install:

GRUB Loading stage 1.5

GRUB loading, please wait...
Error 18.

I installed from clean / boot disk.  Install whent well, no problems.  After this, it asks for reboot and when it does I get this error message.

I've followed other posts on formating manualy the ./ , /home, and page file...  all whent ok until i reboot...  what is up with this.?

I used to have the previous ver. and all was fine.

I installed to a 250 Gigs hard drive, and set up the ./ for 15 gigs., the /home for 20 gigs., and the paging file to 700 megs.

Any suggestions?

:confused:

---

### Post by Pumalite on 2008-08-10
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
You might need to make small /boot partition

---

### Post by Tarsys on 2008-08-10
Man O man that is one complicated thing you refered me to...

I am trying reinstalling and creating a /boot part. along with a /home and standard ./ part...  will see then.

---

### Post by Tarsys on 2008-08-10
well, I've gotten nowhere with that...  it still give me an error 18 after I reboot from install.. which whent very well, until reboot..  so CMOS is not recogniZing my 250 Gig drive, ok..  I created a ./ partition, a ./boot part, and a ./home partition... plus the page file...  I made sure to tell Gpart to set my ./boot partition at the start of the drive... I think that's what I was supposed to do ???  right??  

Hey guys, help me out here...  just a crazy Canuk trying to get laid..  loops..  I mean get installed here...
:popcorn:

---

### Post by Pumalite on 2008-08-10
Did you try updating your BIOS?

---

### Post by john test on 2008-08-10
Sounds like HD is erroring out.  Should be a Memory test and a HDD test/Format on the LIve CD.  I would format the HDD and if it flies, then go back and do the partitioning.

---

### Post by Tarsys on 2008-08-10
So what you are suggesting is :

-boot from CD, load up partitioner and wipe all existing partitions, then format as one large drive first, then do as I did before?  IE: create ./, ./boot, ./home, ./page file???

How big should each be??

Can you be a little more specific..?

Thanks.  :confused:

---

### Post by Tarsys on 2008-08-10
I have the newest up date for this board's bios..  from 2002.  the board is originaly from Y2000.  It used to have Win2000pro and worked fine.  I am using it as a mail, and Legend of the Green dragon server...  I just wanted to try this xubuntu system as Win2000 is getting old and problematic.

---

### Post by Tarsys on 2008-08-10
i am losing patience here..

ok, i've wiped everything from the drive and reformated..

made the /boot partition, /home part., / partition, and a swap.

installed clean ok, asked to reboot... as before...

now when I start up for the first time, i get an error 22 instead of error 18..

it says on screen:

GRUB loading stage 1.5

GRUB loading, please wait...
Error 22

... and hangs.

The Cd image was tested and is good..  

I have a 750 Mhz proc.
256 meg. ram
250 Gig drive (one)
nothing special other than the CD rom.

Please help!!  Or else, I'll revert to Windows!  (and I'd prefer not to!)

:lolflag:

---

### Post by Pumalite on 2008-08-11
I'd say use Xubuntu Alternate CD. (256 of RAM):
[http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)

---

