---
title: "Installing Ubuntu with Wubi."
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by Leestons on 2012-01-06
Hi all, new to the forum and also Ubuntu, I apologise if this is in the wrong place, I was stuck between this and General Help, I figured this would be the better place.

I will be getting a new netbook around Tuesday, and thought it would be a good idea to have a play around on Ubuntu before I install it on my netbook so I have a rough idea how everything works.

However, I have downloaded and ran wubi on my Vista desktop, and received the error IOError: [Errno 13] Permission denied: 'I:\\wubildr' After looking it up on Google I found out it was simply because of my card reader (and nothing being in the slot) and Ubuntu will have installed correctly. Fantastic!

I shut down my computer, and then turn it on again to boot into Ubuntu, straight away Ubuntu trys to load, without me even getting an option to choose between Vista and itself. After a few seconds I get this message

[http://pastebin.com/index/SKs7v2Bp](http://pastebin.com/index/SKs7v2Bp)

I force shutdown as there was nothing I could do, and reboot, this time I get the option to launch Ubuntu, along with Vista, but receive the same error if I try.

I've tried reinstalling via wubi multiple times and the same process happens each time, I've done chkdsk with no dice. I've also read so many threads on here about the initramfs problem i've lost count!

Any help?

---

### Post by shrnh on 2012-01-07
yup, were in the same boat :(. And I'll post useful responses as well! I actually tried installing with a CD AND USB, same thing.

---

### Post by raja.genupula on 2012-01-07
[LEFT]As the idea what i have on BusyBox , there are many reasons for busy box .
the common solution for Busy box is doing fsck to that partition by inserting a live CD.

But if initramfs have problem then also BusyBox will get a invitation at booting .

try these things 
1. increase your boot delay time for 60 or 90 sec

for this help follow this link

[http://askubuntu.com/questions/85929/drops-to-busybox-but-can-continue-upon-exiting](http://askubuntu.com/questions/85929/drops-to-busybox-but-can-continue-upon-exiting)

all the best
[/LEFT]

---

### Post by Rubi1200 on 2012-01-07
Before trying anything, I suggest giving us the results of the boot info script as this may help us determine what is happening.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by shrnh on 2012-01-07
I'm very sorry..I've read the instructions and downloaded the boot info script but I don't know how to get the results file. I'm using windows so theres no sudo command. I'm not exactly getting how to enter the su bash into the command prompt. Forgive me, I'm a complete noob at this :(

---

### Post by mastablasta on 2012-01-07
you need to boot into linux using the liveCD or liveUSB and then selecting try it., this won't do any changes to your computer, but you will be able to run the script and it will give informaiton what is wrong...

---

### Post by shrnh on 2012-01-07
Yeah see, thats the thing, I can't even access linux from the liveCD using 'try it'. I still get a busybox message telling me to do a chkdsk /r and I did. I still get the same message

---

### Post by Leestons on 2012-01-08
Okay, I've made some progress but I'm at the verge of giving up.

I uninstalled Ubuntu and tried fresh, this time downloading the iso and putting it in the same folder as Wubi, everything went brilliantly, not a single problem until I go to boot into Ubuntu. 

"Cannot find Installation.iso /ubuntu/install/installation.iso This happens when Windows etc etc"

I did chkdsk /r (which took 2 hours :( ) and then tried again, same message. I don't even know what to do anymore, the iso is there, I've ran chkdsk, i've spent ages looking on the internet for a solution. 

Ubuntu is just seeming like more effort than it's worth. I'll try it on my netbook when it arrives in the next few days, if I run into the same problems I just wont bother and will stick to windows.

---

### Post by shrnh on 2012-01-09
OMG I did the same thing! That's exactly what happened with me, I got the same message too.

---

### Post by mastablasta on 2012-01-09
> **shrnh said:**
> Yeah see, thats the thing, I can't even access linux from the liveCD using 'try it'. I still get a busybox message telling me to do a chkdsk /r and I did. I still get the same message
 
 
it means you are not booting from a CD. chkdsk is a windows programme so what it happens you boot from hard disk and of course you get the same error.

---

### Post by mastablasta on 2012-01-09
> **Leestons said:**
> Okay, I've made some progress but I'm at the verge of giving up.
 
I uninstalled Ubuntu and tried fresh, this time downloading the iso and putting it in the same folder as Wubi, everything went brilliantly, not a single problem until I go to boot into Ubuntu. 
 
"Cannot find Installation.iso /ubuntu/install/installation.iso This happens when Windows etc etc"
 
I did chkdsk /r (which took 2 hours :( ) and then tried again, same message. I don't even know what to do anymore, the iso is there, I've ran chkdsk, i've spent ages looking on the internet for a solution. 
 
Ubuntu is just seeming like more effort than it's worth. I'll try it on my netbook when it arrives in the next few days, if I run into the same problems I just wont bother and will stick to windows.
 
 
is installation.iso there where it is searching for it? chkdsk /r won't do anything. it repairs the disk and files if there are any erros.
 
use botoinfoscript so we can see what happens on boot that prevents the start of the OS.
 
wubi is ment as a demo. linux is ment to be installed directly on hard disk. you could try creating some free space on your disk and then doing a dual boot. make sure you defrag the disk a couple of times first if you decide to go this way. 
 
if however you just want to try the OS it owuld be better to use a liveCD (burn the iso as image file on CD) or liveUSB to do it ([http://www.linuxliveusb.com/](http://www.linuxliveusb.com/))- you need an empty 1GB usb key for that.
 
you can ofcourse always just use Windows Vista for your needs. there is nothing wrong with that.
 
i usually try them out on USB, to see if it all works as it should and if it does i install it. if user wants to keep windows i do a dualboot:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Mark Phelps on 2012-01-09
> **Leestons said:**
> I'll try it on my netbook when it arrives in the next few days

Just, do NOT use the installer side-by-side option to SHRINK your Win7 partition on your netbook.  Doing that risks filesystem corruption, and if you don't have a bootable Win7 Repair USB stick (I'm presuming your netbook doesn't boot from optical drive), it may be very difficult to repair Win7 to get it booting again.

---

### Post by Leestons on 2012-01-09
Do you recommend I simply create a new partition specifically for Ubuntu? 

My netbook comes with 3 partitions, C:, D: and a recovery partition. 

The reason I have been using wubi on my desktop is because it would be only short term, and didn't fancy all the work.

---

