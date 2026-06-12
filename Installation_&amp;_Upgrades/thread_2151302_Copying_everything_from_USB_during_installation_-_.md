---
title: "Copying everything from USB during installation - including programs"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by eagleestar on 2013-06-04
In short I used the usb for 5 months, need everything back in installation, skip after the stars if you want. 

Okay the story (long version): 
I Bought a new relatively cheap computer for media and didn't check specs properly since it was an optiplex 755 of which there are 4 models (I didn't know this fact). In the mail I got the 2/4 better one (SSF model) which allows only one 3.5" hard drive. 

 Since I never run the OS on the same drive (works better for me in case either fails/corrupts), I installed my 3TB drive as slave as it already had all my media and ran ubuntu 12.10 for 5 months from the usb 2.0 port which was really plenty and it ran almost perfect with the odd slowdown here and there, the only defect was that it was only 8gb and as you might expect it got full relatively quick with programs and updates. 

 After looking into the specs and my options properly I realized I could just buy a SATA 22pin female to ODD slimline SATA 13 pin male adapter ($5!) and use an old 40gb sata laptop drive that I had laying around, take out the DVD drive from the optiplex(which I hardly use, plus have an external usb one) and this way the space problem would be gone for good. 

 After waiting for 45 days in the mail... yes 45 days (Honk Kong mail, cheap but not always reliable) I finally got it today and it worked as expected, formatted the drive created 2gb swap space installed ubuntu and... all my programs and tweaks are gone. As you might expect this is a lot of work to put it all back together, which I am doing since i doubt someone will explain this faster than the few hours it will take me to re-do all the setup. 


***************************************************************************************************************************************'


I know I am not the only person with this problem, so if you know how to install all the programs and tweaks from the USB ubuntu to the new installation on the hard drive post the answer. Otherwise ubuntu team, perhaps include the option in the installation (if its not there already and I just didn't see it). 

I would appreciate if you keep this clean and don't post to tell me you have the same problem, just wait for the answer (haven't see that much in Ubuntu forums but there is always the odd guy/girl).

---

### Post by sudodus on 2013-06-04
Welcome to the Ubuntu Forums :-)

1. In this case I think you can clone the 8GB USB drive to the  40gb sata laptop drive. It will give you an 8 GB system at start, but you can edit the partitions with gparted to take advantage of the whole 40 GB drive.

 2. Another alternative is to make a /home partition on the  40gb sata laptop drive and copy the content of your current /home folder from the 8GB USB drive. And then install Ubuntu. This will preserve the tweaks, but of course, you can to add whatever extra packages and PPAs manually.

Come back to discuss more details!

---

### Post by eagleestar on 2013-06-07
> **sudodus said:**
> you can clone the 8GB USB drive to the  40gb sata laptop drive

Hey thanks for the reply, I didn't know you could clone a drive from size "a" to size "b" and then repartition to recover the extra hard drive space to make it a larger sized partition. 

Sounds like I have some learning to do but I'll try this for sure next time.

---

### Post by sudodus on 2013-06-08
You can clone from smaller to bigger, but not the opposite.

There are so many things you can do in linux. I think the biggest mistake is to assume it is not possible. So ask!

Welcome to climb the learning curve :-)

---

