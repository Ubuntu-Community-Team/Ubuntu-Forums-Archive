---
title: "Installing with XP and recieve storage device error"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by veblen on 2008-06-18
I am attempting to install ubuntu on my sony desktop vaio as a dual boot with XP.  After following all of the prep steps all goes well until the partition screen.  

I select the first option that has a partition break-out of:

85%-191.1gb
15%-34.9gb     

But in the process of resizing I receive a message stating that an error occurred while writing to the storage device and that the resizing was aborted.

Then I am taken to a partition screen showing:

/dev/sda1-ntfs-7.00 
/dev/sda2-ntfs-189.13

Please let me know if more info is required since I have plenty to pass on when/if needed.    

I have tried this many different ways all with the same results.

Any help would be very much appreciated.

THANKS!!!

---

### Post by veblen on 2008-06-19
after doing some research it appears that the two partitions that I have are 1) windows XP and 2) diagnostics and system restore.  This leads to the error since the install is trying to resize/change #2 the diagnostics and system restore partition.

With this in mind, is the solution partioning the disc into 4:

-windows xp
-ubuntu
-swap
-dianostics and system restore?

Any input would be appreciated, since I would like to get this completed ASAP.

THANKS!!!

---

### Post by logos34 on 2008-06-19
> **veblen said:**
> With this in mind, is the solution partioning the disc into 4:

-windows xp
-ubuntu
-swap
-dianostics and system restore?


yes.

Or 

> -dianostics and system restore
-windows xp
-ubuntu
-swap

because according to what you posted above
> 
/dev/sda1-ntfs-7.00
**/dev/sda2-ntfs-189.13**

windows really is sda2 (this big one), and the recovery partition is in first position (the usual place). 

What does fdisk show?

-in a terminal:

**sudo fdisk -l **

---

### Post by waspbr on 2008-06-19
just complementing the post above

you can open terminal in the live CD , at Aplications>Accessories>terminal

there u apply the code mentioned above, this should list the harddrives partitions you already have

---

### Post by logos34 on 2008-06-19
> **veblen said:**
> 
But in the process of resizing I receive a message stating that an error occurred while writing to the storage device and that the resizing was aborted.


did you thoroughly defrag and run error checking on ntfs partition beforehand?

---

### Post by waspbr on 2008-06-19
I think I remember having an error like that... it was solved once I ran windows and it ran its File system check, usually does that on boot up. defrag is not a bad idea...

---

### Post by veblen on 2008-06-19
sorry about the mislabeling...so this where I am at currently...I went in to try to muanaully partiton the /dev/sda2 but I still end up recieving the storage device error.  

-I defragmeanted earlier today...no file changes outside of working with the install...do I need to do it again?

Currently I am checking the disk within windows and then I am going to cycle through one reboot of windows itself prior to trying the install again.

Any other ideas?

AND THANKS for both of your assistance!!! 

y

---

### Post by logos34 on 2008-06-19
> **veblen said:**
> Any other ideas?

Maybe temporarily disable windows system restore, hibernation, and virtual mem/paging file.

Check this out:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)
(-->'Windows disk prep')

Or try Gparted on the livecd desktop before selecting 'Install' (icon):

>system>admin>partitioner

see if it will allow you to shrink windows where the ubuntu partitioner fails

---

### Post by veblen on 2008-06-19
thanks logos34 the tips in the artcle might help and I can also try the gparted on the live cd prior to the install.

As an update:  I deframented again and then checked the dis, however during the manual resizing I ended up with the same error message.  At least it is consistent.

I shall update the thread after trying these options...

---

### Post by ramadan on 2008-06-20
cos am not Linux pro I'll suggest you to use partition magic ver 8 (windows) to resize your partitions and to create 2 partition and you can format them as ext3 and swab partition then while trying to install linux just choose the  partitions as root and swab.
am new to linux but i do can handle windows, this way is working with me and you can also use partition magic to check your hard disk for errors.

---

### Post by veblen on 2008-06-20
Thanks ramadan

Yesterday, I tried about six or seven windows disk partition tools all with the same result of not be able to complete the resizing and or shrinking.  

When at home I will check to see if partition magic was one of them and if not give it a try.  It just seems like something is controlling and preventing the resizing to take place.  

I defragment and check disk each time though just in case but still no go.

I even tried using the ubuntu installation option of installing it within windows, though I am aware of the performance problems, but that provided an warning/error that I had no swap partition.  

I should not that I seemed to have more luck with the gparted tool running as a tandalone rather than embedded ubunutu version.  But in the end that failed as well.  

The next attempt includes the changes that logos34 mentioned regarding turning off hibernation, etc., etc...  I meant to do that first but I got going down the other paths.

Suffice it to say if anyone needs info on windows partition tools just let me know since I have reviewed/tested a bunch.

Also I am going to check with sony regarding this issue....I forgot that their customer support is A-1 and free...providing some of the best service that I have recieved from any computer or software firm...so they just have some insight...

It is a nice little learning experience but I would like it to be over... 

Any additional ideas would be appreciated?

---

### Post by waspbr on 2008-06-21
I think logos covered the remainder of it, removing system restore and page files... I had a similar problem at the begining when I was trying out ubuntu in my HP laptop that ran vista. I was afraid of using gparted at that point, so I got somewhat frustrated with vista, so I backup all my important files and made a fresh vista install.

After that I got the courage to use gparted and that worked really well, the only time it didn't work like I mentioned was fixed when vista booted and made a disk check. But all in all I am actually surprised to see that gparted has failed you...

hope you get better luck from the sony support

gl

---

### Post by veblen on 2008-06-21
thanks gl!!!

yes, based on my research I agree that the right path appears to be removal of the unmovable files, at least for the install if not remeoved completely.  I have also disabled hibernation will ensure that those associated files are removed as well.   

So I have done some cleaning and I am now defragmenting and will give it another go in the AM.

These unmovable files do seem to be an issue in disk resizing in both XP and vista since I have more than a few desciptions that match my stated problem almost word for word.    

regarding sony:  this secondary machine required a plug-in for sony chat which I now have installed and will run the issues past them prior to my next attempt.  Though today I went via e-mail and received only some prelimenary general info due to the set question length.  Even though their response time/service was excellant and I probably could have pumped them for the needed info, I just felt I was going to get more going back-and-forth via chat.  

All I can say is that I am sure glad that I have this secondary machine since we have all been in the situation where you are stuck working on a downed machine with no net availability.  This is a life saver...

---

### Post by ramadan on 2008-06-21
start the partition magic ( from windows) you will see all of your partitions including linux partitions try to resize the partition that contains windows( i.e. don't touch the recovery partition) and to create new extra partition or more simply using partition magic tasks(menu) >> install another operating system>> choose linux>> few questions and almost done
hope you good luck

---

