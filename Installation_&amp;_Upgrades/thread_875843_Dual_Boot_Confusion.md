---
title: "Dual Boot Confusion"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by SirNobody on 2008-07-31
So i decided to take the leap... I'm trying to install Hardy Heron on my laptop, dual booting with Vista Home Basic....however I seem to have hit a snag! I was following the step-by-step instructions over at [COLOR=Blue]http://www.psychocats.net/ubuntu/installing[/COLOR] , however the screen shots there indicate that during the 'Prepare disk space' phase there are supposed to be four  options 

1) Guided - resize
 2) Guided - Use Entire Disk 
3) Guided use the largest continuous free space 
4) Manual

However on the install screen here on my laptop I only see TWO options 

1) Guided - use entire disk
2) Manual

So what gives? I don't want to overwrite Vista and I have no clue as to how to go about a Manual setup!! :confused:

Any help?

---

### Post by SirNobody on 2008-07-31
What? No takers? Come on....i'm sure there's someone who can help me out! Guess i'll have to wait with the install for some time then! :(

Live CD it shall be for me till then!

---

### Post by logos34 on 2008-07-31
One possibility is that your ntfs volume is fragmented and/or has files scattered at the end of the partition, causing the ubuntu installer to conclude the space is nearly all taken up and thus unable to be resized.  

Follow the suggestions in [this link]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")--it was written for XP but is relevant for vista as well...defrag several times, and disable hibernation and paging files if necessary to take care of green 'unmovable files'.  Then **shrink the volume using Vista's own disk management tool**.  Run error checking too.

Reboot into ubuntu cd--hopefully the 'largest continuous free space' option will now show up.

---

### Post by SirNobody on 2008-07-31
Guess I'll give it a try as welll....i just dont want to go doing anything too drastic that messes up my Vista installation! But thanks for the heads up! I'll try it out when i get back home later! Thanks!

---

### Post by cprofitt on 2008-07-31
I would use Vista to resize your partition... it sounds like Vista has used the entire disk...

if you can resize it enough you should be able to install Ubuntu in the new 'free' space.

As always backup your important data before doing these things....

If you have Vista Ultimate let me know... there are some other really cool things you can do to make sure you are safe.

---

### Post by jeremy1138 on 2008-07-31
I dual boot xp and ubuntu and I believe the last time i did an install I chose "manual" and it let me format, resize and create whatever partitions I wanted.  Is this not the case?

---

### Post by loudnlownoma on 2008-07-31
> **jeremy1138 said:**
> I dual boot xp and ubuntu and I believe the last time i did an install I chose "manual" and it let me format, resize and create whatever partitions I wanted.  Is this not the case?

You definitely can with Vista, I did the same on my Vista machine without a problem on one of my installs.  But it sounds as though the OP may not be as comfortable with this option.  Also, IIRC, the first install I did on my Vista machine dual-booting from the same drive, it did limit my options for the installer regarding disk space.  I think this may be due to Vista file management being a little different or something.  I would also agree in using Vista's resizing options to free up space, then running the Ubuntu installer to install to the now free partition.  This would be the safest way to make sure the installer doesn't hose up anything in the Vista install, just in case.

---

### Post by SirNobody on 2008-08-01
@ PrivateVoid - As i see things thats the only way i'll have to do it. I do have Vista Ultimate, but thats on the desktop and I want to install Linux on the laptop before I'm comfortale enough to make a complete switch (guess that might never happen because off all the gaming and 3D design work I do). So stuck with Home Basic on the lappie.

> **loudnlownoma said:**
> You definitely can with Vista, I did the same on my Vista machine without a problem on one of my installs.  But it sounds as though the OP may not be as comfortable with this option.  Also, IIRC, the first install I did on my Vista machine dual-booting from the same drive, it did limit my options for the installer regarding disk space.  I think this may be due to Vista file management being a little different or something.  I would also agree in using Vista's resizing options to free up space, then running the Ubuntu installer to install to the now free partition.  This would be the safest way to make sure the installer doesn't hose up anything in the Vista install, just in case.

Exactly, I know it's possible to do the partitions manually, but I'm just not comfortable doint it.

OK so from what i understand, I use Vista's disk management to free up some space by using the Shrink Volume option, and once I have a chunk of free space I boot up with the Live CD and try running the installer to see if it detects the free space.

I have two drives, a C which is the main system drive and a D thats a really small one, its a disater recovery option to bring my system back to normal in case i mess up the Vista install or i need to reinstall vista and some bloatware!

Ok one little query, assuming Vista detects that free space on my harddisk, will it automatically create a new partition out of it...and will that partition be explorable through Windows Explorer. And if for some reason Ubuntu doesnt detect the free space...what can i do to merge it back with my C drive (I'll be shrinking C)?

---

### Post by Elfy on 2008-08-01
You don't want vista to create a partition as it will be a windows format :)

USe the vista to tool to free up some space - then when you boot the livecd you should be able to point at that free space and tell it to use it - can't remember the exact wording tbh as I only used the guided options once.

Windows won't see the new linux partitions when they are created unless you install software to allow it read them - there is some, I will come back later.

---

### Post by SirNobody on 2008-08-01
Oops....i meant Ubuntu..i accidently typed Vista....sry for the confusion! But if Ubuntu does install itself into that partition, on Vista will the partition be visible? And If yes, will it be explorable?

---

### Post by SirNobody on 2008-08-01
Thanks to all the people who helped me out here....thank you soo much! I got Ubuntu installed and even got my USB modem working thanks to help from some others on another thread....I havent yet tried running wireless I'll report it back later! I shrunk my C drive on Vista by 50 GB and the booted into Ubuntu....installed without a hitch!

Now ... off to play! 

THANK YOU!! :)

---

### Post by Elfy on 2008-08-01
To access linux partitions from windows - [http://www.fs-driver.org/](http://www.fs-driver.org/)

There are some issues with permissions I believe, but having never had to use the software I can't comment from experience - but it is documented in the fs-driver faq.

Have fun

---

