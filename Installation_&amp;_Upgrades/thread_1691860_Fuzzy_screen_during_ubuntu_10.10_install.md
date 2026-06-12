---
title: "Fuzzy screen during ubuntu 10.10 install"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by molm on 2011-02-20
Hello all,

Help! ok so i made a boot cd, checked it for errors and it came out clean. I then tried to install the ubuntu but every time i do,
a fuzzy distorted screen pops up. I pushed F9 to get into the install screen and it seems to load well. I press F12 to check the load process and after about a minute, after it gets to the "check sensor", it always pops up a fuzzy screen.  What should i do? I checked the install guide on the ubuntu site. - not much there thats any help.
Any help would be very much appreciated
Thanks

-molm

---

### Post by sikander3786 on 2011-02-20
Welcome to the forums :-)

What do you mean by a fuzzy screen? Some horizontal/vertical lines and unreadable screen? If so, add the nomodeset parameter. See here for more info.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Feel free to post back if you've got some queries.

---

### Post by molm on 2011-02-20
Hi sikander,

I have about 1.5terabyte hard drive and made a number of partitions on my pc. I have one for my windows xp, my data, and then windows server.  And for the rest, using the Easus partition master home edition, i partitioned about 90gb each for linux and unix. The linux and unix partitions are Fat32 formatted while my windows stuff and data are all nfts.  Could the initial formatting be the cause of the problems? does the ubuntu installer format the drives? Or do i do that seperately?

Oh and the fuzziness is like the whole screen goes hazy- not just horizontal and vertical bars but like hazy hazy and funky colors.  
Thank you

---

### Post by sikander3786 on 2011-02-20
For the screen problem, I would recommend 'nomodeset' boot parameter as per instruction in the page linked above.

Is Windows XP and Server installed there or you plan to install them later? If they are pre-installed, or even if not, in order to save your data I would recommend doing an advanced partitioning in the Ubuntu installer rather than choosing alongside option.

For a basic knowledge of manual partitioning see here.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

---

### Post by molm on 2011-02-20
Thank you very much sikander, 

ok. I installed with the "nomodeset" boot parameter and that got me through the installation process. But when i tried to restart, i tried going into the BIOS and hold "Shift" as per instruction ([http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)) but Grub would not load. I am not sure what is wrong now... 

Grub should have been installed right? 
I can't figure out how to load Grub so I can reach the desktop and try to download my graphics drivers. 



ok! i just found out how to access grub! thank you very much sikander for all your help :) :)
I'm lovin ubuntu now :)
Thanks,

-molm

---

### Post by sikander3786 on 2011-02-20
You are most Welcome :-)

Hope you will enjoy your stay with Ubuntu.

---

