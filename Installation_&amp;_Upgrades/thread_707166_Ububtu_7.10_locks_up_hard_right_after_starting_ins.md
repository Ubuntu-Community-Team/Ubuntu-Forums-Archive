---
title: "Ububtu 7.10 locks up hard right after starting install"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by acidic on 2008-02-25
Hello,  btw i'm a noob to linix, so i dont know any tricks

when trying to install ubuntu 7.10 desktop 64 bit edition, i got off of [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download).  I get to the start up menu.  I go to install ubuntu / run live cd.  My computer then crashes hard right after.    I'm at a compete loss as to what the problem is.  I dont even think i get any other screens or txt line messages before it hangs.

From what i as able to find on the forums,  could be a video driver problem which then crashes it.  perhaps i could try a text based install?  Though were do i find this?

System spec's

Intel Conroe E6700
Abit IP35 Pro mobo
Corsair Twin2X2048-6400C4 memmory
Evga Nivida 8600 GTS 512mb

If you need more system specs let me know. 

I have a XP install, that works just fine.  I also have a vista install that works just fine, on this machine.  I would rather start using linix than use xp or visita, as i'm sick of windoze.

What are your guy's thoughts on this?

Should i try version 6.06?.  or a 32 bit edition?

---

### Post by jeffus_il on 2008-02-25
I would suggest from previous experience that you run the disk partitioner, gparted, before you run install, that is set up your disk partitioning scheme first. There is a thread where an unusual partition did cause the install to hang, let us know if you need help running gparted.

---

### Post by acidic on 2008-02-25
yeah i had saw something about that in a thread i read.  Though i think he had at least gotten to some screen at least before had his pc crash. 

Though i will give it a try.  

Am also going to see if the 32 bit version gets me anywhere as well, once i can get the dvd made. 

I do have 100g worth of unpartitioned space left over for my linix set up.  

I figured i would use grub2 for my boot loader.   or follow up on a site i found on getting xp./ vista and linix to multi boot alright together. 

I'll give gparted a try once i figure out what size partitions i need and so on.  I was hoping the live cd would do it all for me ;-)  So i wouldn't have to spend the time reading up on.

---

### Post by acidic on 2008-02-25
I used gparted, and created 2 partitions one ~80g in ext3 format for linix.  and a 4gb as linix swap.     I then tried the cd again. and it crashes after the kernal loads as normal.   i do see a little bit of text msg, though nothing i can read or write down before it then turns the moniter off.   if it is needed, i can attempt to catpure what i see and write it down in here.



I will try burning another cd at 4x, maybe that is part of the problem? Another note..  the 32 bit version will start up on my older machine just fine, so i dont think it's an issue with the cd i made.

I also downloaded and installed the 32bit version of 7.10  This time it goes a bit further.     what i see is this error msgs,  

initramfs [92.197297] ata 3.00: failed to set xfermode (err_mask = 0 x40)

then a few more msgs about initramfs [new numbers]......  ata 3.00: failed to set xfermode (err_mask = 0 x40)
after a few mins
then [279.396283] ata 3.01 : cmd a0/00:00:00:0020 /00 :00:00:00:00 /b0 tag 0 cdb 0x12 data 36 in

a few more msgs [ new number]   ata 3.01 : cmd a0/00:00:00:0020 /00 :00:00:00:00 /b0 tag 0 cdb 0x12 data 36 in


at which point i rebooted the computer. 


other notes.   is the hard drive is sata, and the dvd rom is sata.   
hard drive is Seagate Barracuda ST3750640AS-RK 750GB 
Optical is a Pioneer dv-rw  drv212d Sata

Perhaps the install is having problems writing to a Sata drive due to driver issues?

---

### Post by acidic on 2008-02-27
Look like it's a possible issue with my mother board.  have to set up into raid?   any idea's or tips?  on how to do this?

How do i do an alternative install?

---

### Post by tommcd on 2008-02-27
You should not have to set up raid to get Ubuntu to install. In fact, leave raid out of the picture for now. If you have raid set up in your BIOS try turning it off just to see if it makes a difference.
To get an alternate install (text based) install CD, just go here and choose a mirror near you:
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)
Then go to the releases for Ubuntu 7.10 and select the alternate install CD:
[http://mirrors.gigenet.com/ubuntu/7.10/](http://mirrors.gigenet.com/ubuntu/7.10/)
Also check the md5sum of the .iso download, and the CD you burned if you can:
[https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29)

---

### Post by acidic on 2008-02-27
Thanks for the links.   I'll give the alternative set up a try and see where it leads me.  [http://forum.uabit.com/showthread.php?t=134673](http://forum.uabit.com/showthread.php?t=134673) is the thread i found with some people having issues with my mobo, and linux

---

### Post by tommcd on 2008-02-27
I think the only problems the alternate CD might fix is if the live CD has trouble with your video card, then the text based install can avoid that.
Try tweaking your BIOS settings as suggested in the Abit forums thread. Good luck.
Do a search for <abit ip35> on these forums. There are a nuber of threads about your board. Here are 2 that may help:
[http://ubuntuforums.org/showthread.php?t=698912&highlight=abit+ip35](http://ubuntuforums.org/showthread.php?t=698912&highlight=abit+ip35)
[http://ubuntuforums.org/showthread.php?t=637721&highlight=abit+ip35](http://ubuntuforums.org/showthread.php?t=637721&highlight=abit+ip35)

---

