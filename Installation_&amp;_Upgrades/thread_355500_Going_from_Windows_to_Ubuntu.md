---
title: "Going from Windows to Ubuntu"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by bongadadu on 2007-02-07
Hey all,

I am a windows user and have never used an OS different to windows. I am experienced with computers and now am taking up computer science in university.

Ive been hearing a lot about Linux especially Ubuntu, Suse and Debian and after asking my self should I try it out or not, I have finally decided to give it a shot and do a dual boot.

I have read the wiki's and some documentation but can not find an answer to my question which is the following:

I have one hard drive of 160 GB partitioned into 4 different hard drives C(has Windows installed on to it), D, E and F each containing 40 GB and the formatting of each drive is NTFS.

Now I wish to install Ubuntu on my currently installed Windows but most of the tutorials I have read and watched do not tackle my situation, they all assume you have some free space left or just one partition.

I have freed up all of the F drive (not reformatted just took all the data off it) and want to install Ubuntu there. How would I go on about doing this....

Any help would be greatly appreciated

Thanks

UPDATE: 
Sorry for this thread, I can not believe how oblivious I was that all i need to do is delete the F drive partition in the bios and then use the install that Ubuntu comes with and choose the raw space. Must be due to exams hehe.
Again sorry for the trouble

However I do have one more question. Will Ubuntu be faster then windows in terms of light multi tasking, since windows gets some major slowdowns.
My specs are:

Intel P4 2.9 GHZ
Hyper threading enabled
ATI 9600 pro 256 mb
512 MB DDR RAM

---

### Post by Motoxrdude on 2007-02-07
Ubuntu comes with a built in partitioner. Wen you start ubuntu from the live cd and click the icon on the desktop that says "Install"
[IMG]http://img.photobucket.com/albums/v716/dragonwake13/Install.jpg[/IMG]


 When it comes time to partition your hard drive, select "Manually edit partition table"
[IMG]http://img.photobucket.com/albums/v716/dragonwake13/Partitioner.jpg[/IMG]

Just fine your windows partition and delete it. Now you need to create two new partitions for ubuntu, a ext3 and a swap.
To make a swap partition, right click on the "Unallocated disk space" and select "Create new partition" 
Create as: logical partition
Filesystem: Linux-swap
New size in MB: 512mb

Don't mess with the space preceding and following.
[IMG]http://img.photobucket.com/albums/v716/dragonwake13/Swappartition.jpg[/IMG]

You can make your ext3 partition the same way, just
Create as- Logical partition
Filesystem- Ext3
New size in MB: *However much space you have free*

When you are done, select "Forward"
You should now see 5 partitions, two linux partitions and 3 windows partitions. Make sure you uncheck the box that says "Reformat" next to your windows partition.
Mount Point:
"Swap" for your swap partition
"/" for your EXT3 partition

[IMG]http://img.photobucket.com/albums/v716/dragonwake13/MountPoints.jpg[/IMG]

Hope this helps.

EDIT:
Yes, ubuntu is a lot better for multitasking. Linux doesn't get bogged down with a ton of spyware and viruses, and doesn't even need ann anti-virus. It is a lot more lean then windows (doesn't have useless crap running" so it is faster then windows.

---

### Post by bongadadu on 2007-02-07
Cheers dude

That reply was fast and rich with useful information, love the screens.
Going to download the dvd iso now and install later on tonight.

Again thanks

---

### Post by Motoxrdude on 2007-02-07
Heh, no problem.
I was already going to make tutorial for it so that's why i had all the screenshots already. Tell me how it goes. Good luck!

---

### Post by bongadadu on 2007-02-07
> **Motoxrdude said:**
> Heh, no problem.
I was already going to make tutorial for it so that's why i had all the screenshots already. Tell me how it goes. Good luck!

Hey

The install went smoothly and both operating systems are working just fine.

Although im completely lost in ubuntu..how to install stuff, but reading tutorials and going slowly i have managed to install vlc player lol how pathetic.
Ah well il get used to it soon enough

thanks anyway man

---

### Post by sloggerkhan on 2007-02-07
The easiest way for someone new to install things is Applications>Add/Remove
but you should start learning System>Admin>Synaptic

---

### Post by bongadadu on 2007-02-07
> **sloggerkhan said:**
> The easiest way for someone new to install things is Applications>Add/Remove
but you should start learning System>Admin>Synaptic


synaptic is how i installed vlc...but the picture quality didn't look too great, maybe gfx card drivers.

Also is there a good codec pack for linux, like k-lite on windows

i wanted to install azureus too but their linux installation instructions are only 5 lines long and assume that you have some knowledge about how linux works i guess. In short they were not very noob friendly.

---

### Post by Motoxrdude on 2007-02-07
Hey, glad you got it working. Goto [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")
It shows you how to install TONS of various programs. I would recommend getting Automatix2 and EasyUbuntu.
Good luck:) 
Ps- Post back if you have any questions about getting started.

---

### Post by sloggerkhan on 2007-02-07
there are codec packages in ADD/REMOVE and synaptic for different media players. VLC is unique as so far as I know it is a standalone player using it's own codecs. There are preferences you can use for better appearance. 

I recommend that you have VLC, xine, mplayer, and the default player and then decide which one you like.

---

### Post by bongadadu on 2007-02-08
hey,

I ran into a problem, after installing ubuntu using 11gigs for ext3 and 1gig for swap it all worked fine and i had 14 gig left, so i partitioned the 14 gig and didnt touch the linux partitions at all using the windows installer and exited the installer. 

Then i went into windows and formated the new F drive into ntfs within windows...after doing this i wanted to go back into ubuntu  but the grub bootloader didnt appear and just launched straight into windows.

So i put the live dvd back in and deleted the linux partitions and started all over again. Everything worked fine but my screen resolution was at 800x600 and i couldnot see any other resolution other than that in the screen resolution settings so i looked for some help since my resolution is 1024 x 768 @ 85Hz, this was the one linux was using before the re-install.

On the wiki i tried to install the ati driver, followed the steps and it all seemed to have worked so i restarted linux and when i go back into it my monitor displayes error saying frequency out of range...so the only thing i can acces now through grub boot loader is windows, linux mem test and ubuntu safe mode.

I know linux is a cool system and fun to use once you know how to, but im finding changing a resolution to be frustrating so im going to simply remove linux after one last try to getting it to work.

I will definately give it a shot later on but right now  if my attempt to fix the resolution doesnt work i will stick to windows

Thanks for all your help on getting me to install it really appriciate it, you guys have one of the best community support i have ever seen
Once again thanks

---

### Post by Motoxrdude on 2007-02-08
That's a shame to here.
You can change it, here is how:
(this will put in you in text mode, so right all of this down first.
```
sudo /etc/init.d/gdm stop
``` 
```
  sudo dpkg-reconfigure xserver-xorg
```
When done, start Gdm again (if you don't know what that is, it is ok)
```
sudo /etc/init.d/gdm start 
```
And that is it! You can select your resolution and refresh rates when you run dpkg-reconfigure xserver-xorg as shown above.
Hope this helps.

---

### Post by bongadadu on 2007-02-08
> **Motoxrdude said:**
> That's a shame to here.
You can change it, here is how:
(this will put in you in text mode, so right all of this down first.
```
sudo /etc/init.d/gdm stop
``` 
```
  sudo dpkg-reconfigure xserver-xorg
```
When done, start Gdm again (if you don't know what that is, it is ok)
```
sudo /etc/init.d/gdm start 
```
And that is it! You can select your resolution and refresh rates when you run dpkg-reconfigure xserver-xorg as shown above.
Hope this helps.

hehe gdm is the gnome desktop enviroment i bet
thats what i tried before but when i reconfigure xserver it asks a lot of other stuff too, should i let that stay as it  and only change resolutoin when it comes up ?

---

### Post by Motoxrdude on 2007-02-09
You should be safe with the default values, just change the resolution when it asks.

---

