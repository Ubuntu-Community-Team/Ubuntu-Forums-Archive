---
title: "Trying to install Ubuntu on brand new Win7 HP machine"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by StealthMode on 2011-07-15
Hey all, I'm trying to help a friend install Ubuntu on a laptop he just bought for his daughter. I have a disc with Ubuntu 8.04 that I used to install on my newly acquired laptop. The HP laptop will not boot from cd to start the installation process. What is it with Windows 7 that blocks this? (All the more reason to DUMP windows!) I will be installing a dual boot system for him, just in case his daughter can't adjust.

---

### Post by rreyes3713 on 2011-07-15
I'm guessing here ...

... look at your HP manual and see how to get to the BIOS setup. It's something like  F1, F2, DEL, ESC or F10 ... you press when you boot up the computer.

Then you should get a menu for selecting booting order. Make "CD" your first choice to boot up. 



Another way :
I had a HP laptop with Window 7. I did Wubi installation. Then I did a migration to an open partition. That's one way to get around the Window 7 thing.

---

### Post by dFlyer on 2011-07-15
Why are you installing 8.04. The current LTS is 10.04?

---

### Post by StealthMode on 2011-07-15
I have a working CD with 8.04 on it. I tried making a disc with 10.04 on it, and botched it. I just did an install with my 8.04 disc on my own computer and then ran the upgrade. I'll try hitting ESC when it's booting up. I just tried it, but maybe I didn't catch it in time.

---

### Post by StealthMode on 2011-07-15
I just moved CD rom to the top of the booting order and the damn thing STILL didn't do what I told it to do!
 
EDIT: ... OR it just means that I'm an idiot and can't read. I moved "USB cd/dvd rom" up instead of "internal cd/dvd rom"

---

### Post by smurphy_it on 2011-07-15
Try a newer distro.  8.04 is quite old.  You should be able to get 11.04 (or 10.04 LTS if you rather) onto a Live USB using unetbootin.

---

### Post by Blasphemist on 2011-07-15
Most pc's these days prompt you on 2 things when you turn them on. One is going into bios as previously posted. My guess is that you may not have seen how to save your change and therefore it still booted to the hard drive. You can check that by going back into bios and if the cd still isn't first in the boot order, make it so and be sure to save the changes.

The other option is to access the boot the menu and just choose the cd to boot from.

If these things don't work, it's likely that the cd has an error and isn't being seen as bootable. If that is the case you'd need to burn a new one or create a boot usb. You could use this to create a live usb. [http://www.pendrivelinux.com/liveusb-install-live-usb-creator/](http://www.pendrivelinux.com/liveusb-install-live-usb-creator/)

When you do get past this, often HP's come with all 4 primary partitions created and used. If that is the case, you'd need to delete one. You could create the windows recovery disks and delete the recovery partition or delete the HP Tools partition if you can ensure that you could download them should they ever be needed (I don't think I've ever heard of anyone actually using them).

Lastly, this is a great site on installing dual boot. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by StealthMode on 2011-07-15
Ok thanks, I'm trying the USB route with 10.04.

---

### Post by StealthMode on 2011-07-15
Ok USB drive has been created, I moved USB disk up in the boot order on the bios, it ran the USB just fine. It is now at the start-up menu for Ubuntu. The options are to "boot from this usb" etc. When I selected that option and pressed Enter, it just blinked the menu but didn't run anything. Tried it a few times, no change. I selected the option to run a memory test.

---

### Post by Blasphemist on 2011-07-15
Check out this post and tell me what if any differences you see from what this shows (other than maybe usb instead of cd) please. You may be having a video caused issue. If so this thread will help you but if not this post describes troubleshooting the boot process to some extent.
[http://ubuntuforums.org/showpost.php?p=10740097&postcount=3](http://ubuntuforums.org/showpost.php?p=10740097&postcount=3)

---

### Post by rreyes3713 on 2011-07-15
What is the capacity of USB flash drive?

I don't know if this is significant but I used to have 10.04 on a CD (700 MB). For some reason, I had trouble installing Ubuntu from this CD.

So I burned 10.04 on a 4 gig USB flash drive. It worked fine. 

Not sure if this is helpful (taking the Microsoft approach giving you info that totally useless).



If I recall, you should get a menu selection of Live (run off the flash drive), or complete installation. You select installation.

If you get this far, remember when it comes to the partition step, check mark the radio button that you will create the dual partition.

Then you will move the line graph square button how much partition you want for each OS. I don't like typing in the amount of space for partition. Rather use the line graph. 

Too me, this was a "gotch you" step that I kept messing up. 

Hope you have better luck than me.

---

### Post by StealthMode on 2011-07-15
The flash drive I used was 2GB. The computer will start up from the USB, pressing Enter to boot will not yield ANYTHING. It just sits there. I could go into the help menu, read whats written in there, but any time I tried to boot, it wouldn't. It tells me "Could not find kernel image: /casper/vmlinuz"

---

### Post by 99jetta on 2011-07-15
Your problem is (almost certainly) that your laptop has a UEFI BIOS.  It's not a standard BIOS at all.  And Windows 7 (64-bit, right?) has been installed with a GPT (GUID Partition Table), which has little in common with the MBR partitioning you're used to working with.  Look on Wikipedia for UEFI and GPT to get a basic description of what's going on.  I don't have any suggestions at present.

---

### Post by rreyes3713 on 2011-07-15
> **99jetta said:**
> Your problem is (almost certainly) that your laptop has a UEFI BIOS.  It's not a standard BIOS at all.  And Windows 7 (64-bit, right?) has been installed with a GPT (GUID Partition Table), which has little in common with the MBR partitioning you're used to working with.  Look on Wikipedia for UEFI and GPT to get a basic description of what's going on.  I don't have any suggestions at present.Well that kind of sucks. 

I'm thinking about getting a ASUS laptop 64-bit ... (... don't get me started on my HP laptop that lasted 1 year and 2 weeks).

What about a WUBI installation then migrate?

Didn't I read some post on this forum about HP laptops having multi-partition that needs to be consolidate or something?

---

### Post by StealthMode on 2011-07-15
Ok I ended up doing two USBs, one with 10.04 and the other with 11.04. The 11.04 one worked! So I want to go ahead with it. How do I partition the drives to keep Win7 on there, just in case my friend's daughter can't adjust to Ubuntu?

---

### Post by Blasphemist on 2011-07-15
So you do want to do dual boot of Ubuntu and win 7 right? If so, you'll shrink the windows partition and use the unused space that results to create an extended partition. In that extended partition you'll create a logical partition for Ubuntu and a logical partition for the swap. The swap should be a bit bigger than your amount of memory. The Ubuntu partition should be the rest of the extended partition. The Ubuntu partition must be about 5GB minimum but exactly how big depends. It depends on how much the windows partition can be shrunk and how much space you need. I originally let Ubuntu just do the partitioning itself and when I ended up using Ubuntu almost exclusively it was too small for all of my pictures and music. Therefore I recommend you do the partitioning manually following this sites documentation. It's a real good site on doing this but do follow it closely including planning well. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by rreyes3713 on 2011-07-15
Here's I go again giving you information that might be totally useless ... [ kidding you ]


... I'm not familiar with 11.04 installation but for 10.04 I recall during the partition step you will be asked how do you want Ubuntu install. 

One recommendation is side-by-side with the other OS (Window 7). You select this one. 

Then below that it should asks how do you want to partition the hard drive. If I recall there's a radio button that is preset set to default giving you already set partitions. I would select "manual" radio instead so you could set the partitions instead.

If I recall there's two ways to partitions the hard drive, manually put number of MBs in the text boxes of each OS system or

use the graph line with square button. You could move this square button left or right on the line graph. On the left is your Window 7 partition size, on your right is your Ubuntu partition side. As you move this square button on this line graph, you'll notice how the number increases (or decrease) on the partition of each OS.

e.g. my (dinosaur) Dell has only 40 gigs. So I put the line graph button so each OS has 20 gig each (XP and Ubuntu).

So adjust this line graph accordingly.

Why I know this partition step pretty well? 'Cause I messed up too many times at this step.

I might have gave you more info that's needed which may intimidate you but once you get to the partition step, familiar yourself, even if you have to select "go back" arrow.

Good luck!

---

### Post by rreyes3713 on 2011-07-15
Did you defrag Window 7 first?

Depending how much space has been used up, its good practice to defrag Window 7 before installing Ubuntu to dual boot.

By the way. my method mentioned is allowing Ubuntu do the partition. Some partition the hard drive through Window 7 like the above method.

---

### Post by StealthMode on 2011-07-15
Ok I'm following the link that Blasphemist shared. I have a similar question about doing a manual upgrade on my own laptop. The installer crashed. Does that mean I made a faulty cd? It got about 2/3 of the way through the installation process and crapped out.

---

### Post by Blasphemist on 2011-07-15
It's hard for us to say what happened for it crap out without knowing more. Could you tell what it was doing at the time? If my cd burns without errors, it's always been good. That doesn't mean yours is though. It seems more likely to be something else. I'd restart the install and pay it close attention.

---

### Post by StealthMode on 2011-07-15
It happened while copying files. If it does it again, I'll post up what it was telling me. I tried to boot again from cd. 
 
While doing the install on my friend's daughter's laptop, the computer froze while following the partitioning guide that you posted. I was partitioning the main chunk and it froze. I let it sit that way for upwards of an hour, but restarted.

---

### Post by Blasphemist on 2011-07-15
The length of time that step takes is dependent on how much data there is to move and how fragmented the drive is. I had my windows running a defrag every night prior to my first install and still ran it a bunch of times manually before I started. Still, an hour is a long time. Was there much free space?

---

### Post by StealthMode on 2011-07-15
"The installer encountered an error copying filed to the hard disk: [Errno 5] Input/output error. This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the cd/dvd, to burn the cd/dvd at a lower speed, to clean the cd/dvd drive lens (cleaning kits are often available from electronics suppliers), to check wether the hard disk is old and in need of replacement, or to move the system to a cooler environment." 
 
I clicked "ok". Then another window popped up.
 
"Installer Crashed. We're sorry, the installer crashed. Please file a new bug report at..... attached the files /var/log/syslog and /var/log/partman:"

---

### Post by Blasphemist on 2011-07-15
If it seems like this is the same place it failed earlier, it might be the cd. Do try burning another, from another pc if one is available. It is also possible the machine is getting to hot. Try and ensure better airflow just in case. I have the windows open all the time here and it gets dusty. I have to blow into the air intake and output periodically, after I brush away the crud at the intake.

The files referred to may also help but I'm not sure I'd see the problem for sure in them. I could try though. You could try opening them and looking for an error we could try to interpret.

---

### Post by StealthMode on 2011-07-18
Ok I FINALLY got it to work! I burned a new CD and installed 10.04. The system is working great. Only problem now is that I can't get the wireless to connect here at work! (I have another thread on this right now, too. So I have 2 Ubuntu laptops that aren't connecting to the wireless network at my place of employment.) I did connect an ethernet cable to MY laptop, and it's connected just fine, but it would still be nice to get this bug fixed about wireless connection.

---

### Post by rewyllys on 2011-07-18
> **Blasphemist said:**
> . . . . You could create the windows recovery disks and delete the recovery partition or delete the HP Tools partition if you can ensure that you could download them should they ever be needed (I don't think I've ever heard of anyone actually using them). . . . 
Over the years I've owned several HP machines, and have NEVER used any of the HP Tools.  Hence, unless you have a favorite or favorites among the Tools, I'd recommend using the HP Tools partition for something useful, such as Ubuntu.:)

---

