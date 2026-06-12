---
title: "Cant install ubuntu on pen drive."
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by Zundap on 2010-09-29
Hi, i am having a problem installing ubuntu on to a pendrive, i have clicked on, system, then on administration, then on USB start up disc. 

The **make USB start up disc tab** comes up ok and my pen drive was showing in the box headed, **USB disc to use **then it disappeared and it was replaced by this code **/dev/sdb **Then it changed to showing the pen drive again and now it keeps chainging every couple of minutes, from showing the pen drive, to showing the code  **/dev/sdb**

Also the button that says **make start up disc** is ghosted so i cant proceed any further, the only other button options is the **quit**  button, which obviously leaves me right where i stated. 

If any one could advise me of how to sort this problem i would be very grateful, Thanks in advance, Zundap.

---

### Post by sreevbg108 on 2010-09-29
I think it would be better if you just used the installation disc and install it onto the usb. Haven't tried the start up disc in administration. How much space do you have on the usb?

---

### Post by PRC09 on 2010-09-29
Do you have any other usb drives or devices plugged in when you try?

---

### Post by Zundap on 2010-09-29
Thanks for taking the time to reply, I do not have any other pen drives connected to this computer and the pen drive i am using is a 4 Gig one. 

I have tried to install it on to a CD also, but still the **make start-up button** is ghosted, the only other option is the **quit** button, which does work.

---

### Post by msakms on 2010-09-29
Try formatting the pen drive using gparted. The partition table might be missed up

---

### Post by Zundap on 2010-09-29
Thank, msakms, but could you tell me how to do that?

---

### Post by msakms on 2010-09-29
Open up "ubuntu Software center" from the Applications tab and search for gparted and install it. After opening up the gparted window 
"System----> Administration--->GParted", type in your root password, choose your pen drive from the drop down list on the upper most right corner of the window. Then choose 
Device---->Create partition table and finally click on APPLY. Use FAT32 as your file system. Lastly open up Start-up disk creator and give it a shot.
I hope this works out for you.

---

### Post by C.S.Cameron on 2010-09-29
Have you pointed SDC to a Live CD or ISO?

---

### Post by Zundap on 2010-09-29
Thanks for the reply msakms, but there is no **ubuntu software centre** on the on the Application drop down list.

GParted is also not on System - Administrator drop down list either. 

There is no drop down list in the top right hand corner either. 

I think the ubuntu version i am using is 9.04, does that make any difference to your instructions?

> 
Have you pointed SDC to a Live CD or ISO? 	

Thanks C.S.Cameron, but i do not know what SDC is, i am just about a total newcomer to ubuntu. 

Could you explain what SDC is and how to use it?

---

### Post by Zundap on 2010-09-30
I think this will apply to all others who are running ubuntu 9.04, unless other updates alter this procedure, and i don't know if it will apply to other  versions, some how i very much doubt it.
.
Thanks every one for you help, but i have sorted it, purely by luck, i managed to get the **ubuntu 10.04.1-desktop-****desktop-i386.iso** that i downloaded from the ubuntu website burnt to CD.

What i did was, i right clicked on the **ubuntu 10.04.1****-desktop-i386.iso** icon on the desktop and picked the first option **"open with disk burner"**

The burner program opened, then i just clicked on the **"BURN"** button at the bottom right hand corner and away it went, it burnt ubuntu in no time at all, as easy as that.

I then shut down the computer, leaving the ubuntu disk in the CD ROM/writer, then booted it back up, entered the BIOS by tapping delete every few seconds from start up till I entered the BIOS, set the BIOS to boot up from the CD ROM/writer first.

I rebooted and it picked up the new ubuntu 10.04.1 disk no problem, it was rather slow at booting from the disk, but it worked flawlessly and i was then working from the ubuntu 10.04.1 **-desktop-i386.iso** disk that i had just burnt and therefore i was in to the new ubuntu 10.04.1.  interface, which i reckon is way better looking than than the old 9.04 one, that's if you if you like a nice pale plum colour, which i do. 

I then went to** system,** then **Administration**, then **USB disk  start up creator**, which is the second option up from the bottom of the drop down list.

The **USB disk  start up creator **opened and there were two long oblong white strips going just about the full width of the dialogue box,  one towards the top of the dialogue box and the other about halfway down. The one half way down already my pen drive entered in there, in my case it said **Kingston Dater traveller 2.0**  then the capacity of the drive and then the amount of free space on the drive.

The white strip at the top has **CD-drive **written just above it and a button underneath on the right with **Other** written on it. I clicked on **other** and another dialogue box opened, with 2 windows or boxes in it, in the left hand pain headed **Places**, that box had a list going down the left hand side, which was as below.
> 
Searched 
recently used
------------------
root
file system
disk
floppy0
cdrom0
------------
Desktop
The other bigger window also had a list in it going downwards, but take no notice of that at this point. 

I then clicked on the Desktop option in the left hand window, which then gave a new list in the larger right hand pain, which were all the items on the desktop. In the right hand window I then clicked on the **ubuntu 10.04.1-desktop-i386.iso **icon so that it was selected and then clicked the open button in the bottom right hand corner. 

That then put** /home/me/ubuntu- 10.04.1-desktop-i386.iso** in the top white oblong strip. The **make start up disk** button in the bottom right hand corner became live, i then just clicked on that button and away it went and wrote that O/S to the pen drive a couple of minutes later, a message came up saying that the job was complete.

Just one more thing, this new 10.04.1 ubuntu, does not have Gimp included with it, or at least the disk i have burned does not have it, that's a big draw back for me, so it may be an issue for others. 


I hope this detailed account will help someone else who is a learner just like me, if it does,  would you please be kind enough to answer the post so that i will know about it, or send me a PM. I am an old guy who has entered the young man's game, if i have helped someone, then i have returned some of the great help that i have been given here by you guys and i will then be buzzing my **** off  off for a month of Sundays, because then i have become a contributor to the fantastic achievement that is linux ubuntu.Thanks again to all who responded to my post,  Zundap.

---

### Post by C.S.Cameron on 2010-09-30
SDC = Startup Disk Creator.


You did not need to burn a CD, you could have just pointed Startup Disk Creator to the location of the iso image.

---

### Post by Phezz on 2010-09-30
I've never gotten the startup disk creator to do anything productive, but unetbootin works quickly and easily, and not just for ubuntu disks but also for windows installs and hiren's boot cd.

sudo apt-get install unetbootin

---

### Post by Zundap on 2010-10-15
Thanks for the advice guys, i am learning slowly.

---

