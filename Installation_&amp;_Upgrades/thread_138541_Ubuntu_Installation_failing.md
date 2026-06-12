---
title: "Ubuntu Installation failing"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by nevyndweomer on 2006-03-02
Hi I am installing breezy on an old AMD duron machine 
it is a 900Mhz with 512 RAM and 10 Gig disk 

It has failed a few times at different stages of the installation 

first at the install of additional packages I got a message to re-burn my CD on a lower speed so I did so 

Then it failed on kernal install and the again on the first CD at kernal install 
Then I managed to get a server version to install by waiting for the kernal to fail and run it again, this time it gives me the option to choose a different kernal image 
after choosing this it worked  so i tried to install again with the desktop version which i want and it went all the way through "Woohoo"   but when it finnished it had an error that somethiing was re-spawning to rapidly and was stopped for 5 minutes in an endless loop  

When trying to re-boot it had not worked because it asks for a floppy so that was wrong too 

I would really like to install Ubuntu but am beginning to wonder if I should go to a different dist for this machine to confirm if it is the OS or the hardware  

does anyone have any similar experiences, is this a Duron problem or could my ISO be corrupt ?   

Regards 
Nevyn 

PS I am downloading the ISO again to try that beofre going to Fedora

---

### Post by swamytk on 2006-03-02
Hi,

I too faced this issue for long time. Recently I came to understand that DMA is disabled for IDE devices by default in Ubuntu distributions (Any one??? Pl. correct me if I am wrong). My Samsung DVD-R device was not able to read Ubuntu CDs (sent by canonical also). You have to enable DMA to solve this issue.

Here is how to enable DMA while installing Ubuntu:
1. Choose "expert" install at boot prompt of boot cd
2. Select default values for prompts if you don't want to fiddle with them.
3. In "tune drive parameters" screen type '-d 1 /dev/hdc'. This is to enable DMA on CD-Drive (hdc - sec.master in this example. You select your conf.)
4. Then proceed as usual with installation.

The above setting is for installation time setup only. For day to day operation with DMA support, follow the link below which gives exact picture.
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

All the best!

Refer the successful attempt link here: [http://ubuntuforums.org/showthread.php?t=137489](http://ubuntuforums.org/showthread.php?t=137489)

---

### Post by nerval on 2006-03-02
For Kernal ( [http://en.wikipedia.org/wiki/Kernal](http://en.wikipedia.org/wiki/Kernal) ) operating Commodore is quite hard in today's conditions. So, I don't have a clue even though my first computer was a commodore-64.

Iso burning becomes a huge trouble nowadays, it is a problem for me too... I would say order CDs from Ubuntu; use it yourself and give it to all of your friends. (Except that, the previous reply told almost everything I had to say)

---

### Post by nevyndweomer on 2006-03-03
Hi all 

thanks for the replies 
I have tried what was suggested and the installation seemed to work as in it did not fail part way through anymore 

however I now have a new problem in that after the installation has finished and ejected my cd the system restarts and then will not boot ! 

I am told to insert a floppy which suggests that the HDD is not seen as bootable  

Please help I really have heard good things about Ubuntu but am getting a little frustrated I have now installed multiple times with different variations in the partitioner thinking this was causing the problem and have even tried using the options to download stuff from the mirror site  

I have run a verification on my CD and all is ok 
has anyone else seen this ? 

does anyone else have Ubuntu running on an AMD Duron machine with success ?

---

### Post by nevyndweomer on 2006-03-03
I have been reading some other threads in this forum and wonder if it is GRUB causing the problem 

Most people seem to run this in relation to having multiple installations on their system but I will nevr do this so is there a way  I can do away with grub altogether as Ubuntu will be the ony OS on this machine 

I do remember an option on the expert installation to run without a bootloader  but since GRUB has been installed in the MBR I guess it will remain iin its broken form and continue to cause problems  

How do I get rid of it ? 
can I Low level format the drive or erase the MBR  
I do not have a live disk so I need to do this without 
What if I shove a Microsoftinstall disk in and start an installation of that ? 

Nevyn

---

### Post by swamytk on 2006-03-03
You I might have mislead by the expert level installation screen. The boot option you have to select should be "GRUB at MBR". Have you done it? What you selected on that screen?

---

### Post by nevyndweomer on 2006-03-04
Hi 


I HAVE SUCCESS !!!!!!

I read some other comments and decided that my disk might be flakey 
so I low level formatted it and started again and it worked 

Thanks everyone for the comments in my various threads  I will only report my success here   

Now I need to get SMB working right 
I can see mine and my girlfriends 'doze machines but they cannot log on to me  

I will find the right place to post a thread on this  

Thanks again 

Nevyn

---

