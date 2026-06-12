---
title: "Help! Cant activate nvidia driver or get wireless after reinstall of 10.10"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by JohnnyBlaze on 2010-10-25
Hey everybody! I was hoping some folks a little more informed than  myself can help me out with a problem i'm having. These forums seem to  be an incredible resource so I'm hoping this is an easy fix for someone  out there!

ok, down to the embarrassing part.. so i got myself in way over my head  too soon with Ubuntu but i really like the OS.. I installed 10.10 on my  HP laptop according to the directions on [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)  . Everything went well and I had no problems until I came across a  thread about aircrack-ng.. I decided to test how vulnerable my own  connection was after getting scared by looking up some how-to videos on  youtube that made it look a little to easy. I was having a ton of  problems with the injections tests and couldnt get it to work. I was  trying to patch my ath5k driver according to some threads i found on  this forum and couldn't get it to work. I finally found a thread  somewhere about editing the base.c file to fix the driver. Well, being a  noob i have no idea what i did but it wasn't good... yep, shake your  head.. i deserve it haha.. anyway....

When i rebooted the comp after finishing the editing process it came up  with all kinds of errors and brought me to a grub rescue prompt..  Yikes!! luckily i had Ubuntu 10.10 on a usb so i restarted, tried to  delete the partition it was on with gparted and then tried to reinstall  it.. The installation worked and now I can boot into windows again from  the grub loader with no problems, but Ubuntu is all screwy.. 

Windows connects to the internet and doesn't seem to be phased in the  slightest bit but ubuntu won't let me stay connected to any wireless  networks and I also get a failed message when i try to activate the  nvidia driver in Ubuntu.. Man, did i learn a lesson about getting ahead  of myself and trying to bite off more than I can chew! I really love  Ubuntu and the open source ideal so I don't want to let this sour me.. 

At the partition select prompt when I reinstalled ubuntu I selected  "partition my drive manually" or something to that effect. Should I have  installed it along side windows via the other option? I have a feeling  my problem was compounded when i tried to erase the partition Ubuntu was  on but now I'm totally lost and I  really don't want to screw up my comp any more! I figured it's time to  ask for help instead of shooting in the dark searching random threads  for a similar experience which may not be similar at all.

Is there a way to repartition everything from windows without losing my  data and reinstalling Ubuntu? I didn't have anything worth saving on  Ubuntu but i have about 100gb worth of stuff on my windows partition i  don't wanna lose! Can anybody help?
 

If I forgot to add any necessary information let me know and i'll be  happy to provide any info I can. Thanks a ton in advance and I can't  wait to get Ubuntu back up and running! it's really pretty impressive! I  think i'm just gonna stick to what i know this time around and leave  the rest to the professionals though! haha

Thanks again!

Johnny Blaze

---

### Post by JohnnyBlaze on 2010-10-26
nothing so far? i did some googling and found some pages talking about restoring windows mbr but i'm slightly confused about the available bootdisks and recovery cds. I'm kinda lost at this point and would really like to get every thing to normal and leave it there. can anyone help or point me in the right direction? i had it working before so it's not the same error as a lot of other folks on here have with nvidia. I get an error that it cant find a file as soon as i click activate. i'm afraid i erased something important and it didn't reinstall properly. Should i try to wipe the drive and reinstall ubuntu again or try something different? help!?

Thanks everyone!

---

### Post by efflandt on 2010-10-26
If you want to completely reinstall Ubuntu, assuming you know which partition(s) it was on, just chose advanced or manual partitioning when the install gets to that, select the specific partition(s), including one for / (and whatever else if you have any others for Linux) and check the box to format those the ones for Linux.  You don't have to worry about swap, because Ubuntu will automatically use any existing swap partitions.

Then you should (hopefully) end up with a fresh Ubuntu system that works, unless updates do something strange to your system.

---

### Post by JohnnyBlaze on 2010-10-26
Excellent! thank you very much! I'm gonna try that right now and see how it  goes. I appreciate the help!

---

### Post by JohnnyBlaze on 2010-10-26
Well, I figured out my mistake after following your advice. The last time I attempted to install Ubuntu I had just highlighted the drive to be used but did'nt reformat it according to the installer by clicking change and setting up the options. It probably got confused somehow and thats how I ended up with the errors. My wireless works again and I was able to set the graphics to the highest settings with no visible problems yet. Thanks again! sometimes all you need is that one little detail haha

Cheers!

Johnny Blaze

---

