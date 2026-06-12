---
title: "Out with Windows, in with Ubuntu"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by NBFlyacker on 2011-06-21
Hey all,

Im new to ubuntu but used red hat many years ago.  I've been a windows user most of my life and really only played around with red had.  I'm finally taking the step and completely migrating all 3 of my home pc/laptops to ubuntu.

I have one questin.  On the two laptops I'm going to do a clean install and completely repartion the drives on them so that will be a pretty straight foward install.

However, on my main desktop, I have a 150GB hard drive that is devided into two seperate NTFS partions.  the first partision (50GB) is the root partion that windows resides on.  This is also the partion that all of the my windows apps are stored on.  This is hte partion that I want to reformat and install Ubuntu onto.  The seconday partion is 100GB and it is used only for storing files and such.  I have all of my mp3's, movies, etc on this drive.  I don't want to touch that one.  I want to use it hte same way in Ubuntu as I did in Windows.

When I got to hte partioning part of the installation, I got nervous.  Is it possible to format the first 50GB partion and leave the other partion alone and still have Ubuntu recognize it?  I was concerned that since it is NTFS, that I wouldn't be able to mount it or see it once Ubuntu gets installed on the first partion.

If worse comes to worse, I'll just back everything up on DVDs, but there is over 45GB of data on there.

Any help or guidence would be greatly apprciated.

thanks,

RB

---

### Post by jerome1232 on 2011-06-21
> **NBFlyacker said:**
> 

When I got to hte partioning part of the installation, I got nervous.  Is it possible to format the first 50GB partion and leave the other partion alone and still have Ubuntu recognize it?  I was concerned that since it is NTFS, that I wouldn't be able to mount it or see it once Ubuntu gets installed on the first partion.



Ubuntu works with NTFS great out of the box, during the partitioning phase be sure to select a mount point (such as /data or something) for your ntfs partition and [COLOR="Red"]ensure that it's not set to be formated.[/COLOR]


It would be a good idea to always have a backup, I would strongly recommend getting an external drive and **always** keep an upto date backup on their. You never know when you'll need it.

---

### Post by NBFlyacker on 2011-06-21
Thank you so much for you quick reply.  I know I need go get an external drive.  They're cheap these days anyway.  I just wanted to get ubuntu installed tonight.

thanks again.  I look fowarwd to learning.

---

### Post by Bucky Ball on 2011-06-21
S'easy. Choose to manual partition when you get to partitioning. You will see your NTFS drives there. Kill the Windows one and just don't touch the other one with your data on it. 

/
/home
/swap

Those are default mount points in the manual partitioner. Put all of them in the space where you have just killed the Windows partition. It shows you in the bottom panel what you are about to do (doesn't start deleting partitions and reformatting immediately) so you can check, double-check, triple-check you have it right before hitting 'Go'! 

Good luck. It really is a piece of cake.

(PS: it will not automatically reformat anything NTFS from memory, only previously exisiting ***Linux*** mount points of which you have none, unless you tell it not to.)

---

### Post by NBFlyacker on 2011-06-21
I deleted the 50GB partition and only created a / and /swap.  The swap partition was only 2049MB since I have 2 GB of memory.  The rest went to /.  Should I have broken that up?  I only mounted the 100GB partition as /data and then left it alone.  

It's installing now.  If I should have broken the root partition into a / and a /home, can I make that change after the installation?

Thanks again for all your help.

---

### Post by Bucky Ball on 2011-06-22
What 100Gb partition did you make as /data? The one with your data on it??? Hoping not as that didn't need to be touched at all.

Yes, you can create /home later but you need to run off the LiveCD so all partitions you want to work with are unmounted. Then simply shrink / (this can take awhile) and create /home in the free space using Gparted (that's the partition editor you just used during installation which is a standalone application).

Next time you do a clean install, if there is a next time, you can just hit / and leave the rest untouched (don't format /home). Much cleaner and safer. ;)

---

### Post by NBFlyacker on 2011-06-22
Everything is up and running and I'm in Ubuntu now.  I didn't touch my data drive.  I only mounted it.  However, it doesn't show up in computer like it used to in Windows.  It shows up as a directory in "file system"  Is that normal?  Not that big of a deal though.  Everything is safe and I have already began to transfer some of the backups.

I guess I shouldn't have mounted the 100GB drive as data, based on what you're saying.  Is there any way to fix that sow that it shows up as a "drive" in computer?

If I boot from a live CD, what size do I need to make /?  I'm assuming the rest should go to /home?

Sorry for the newbie questions.  I'll get it farily quickly, I think.

rb

---

### Post by dFlyer on 2011-06-22
Back up your data regardless of what you decide to do. You do not have to reformat your NTFS partitions as ubuntu can read that file system. I would recommend that you download the live desktop cd and test all your hardware before installing to make sure everything works. Once you decide to install ubuntu remember to go slow, have fun and as questions providing as much information as possible. Just remember that ubuntu is now windows.

---

### Post by nzjethro on 2011-06-22
I mount my data partition, but I edited fstab, rather than doing it during install. I'm sure that it has the same effect though, and I've had no issues with it. I've created shortcuts to folders on that drive in my /home folder (e.g. to videos and pictures).

What do you mean by:
> If I boot from a live CD, what size do I need to make /? I'm assuming the rest should go to /home?

If you are installing Ubuntu, I would recommend at least 5-6GB for /, and then the rest to /home. I hope this answers your questions.

---

### Post by Bucky Ball on 2011-06-22
> **NBFlyacker said:**
> ... it doesn't show up in computer like it used to in Windows.  It shows up as a directory in "file system"  Is that normal?  

Pretty much. All good. There is a way to get it mounted at boot time if you want it on the desktop and mounted then.

> I guess I shouldn't have mounted the 100GB drive as data, based on what you're saying.  Is there any way to fix that sow that it shows up as a "drive" in computer?No, no need to mount the NTFS partition during install as Ubuntu can detect and mount them fine. What directory is it mounting in? /mnt or /media? When you open /data does it show on the desktop?

Anyway, go to Synaptic Package Manager, search for and install ntfs-3g and ntfs-config. The latter will detect and auto-mount any/all ntfs partitions at boot. The choice is yours. You will now find the NTFS Configuration Tool in System>Administration or Preferences, can't remember which. 

> If I boot from a live CD, what size do I need to make /?  I'm assuming the rest should go to /home?/ needs 20Gb at the most (if you look in Gparted you will see how much of / is currently being used by the install). Rest to /home, yes, and /swap at the end; size of your RAM or double that for hibernation (although this is a point of debate on these forums!),

> Sorry for the newbie questions.  I'll get it farily quickly, I think.

rbFine, that's what it's all about. Enjoy the learning curve. It has been worth it for me and plenty of others, hope the same result for you.

---

### Post by Bucky Ball on 2011-06-22
> **nzjethro said:**
> I mount my data partition, but I edited fstab ...

No need for editing fstab in this case as NTFS partition. ntfs-3g and ntfs-config will do the editing for you. ;)

Also, you want more than 5 - 6 Gb for / unless you are running a minimal/barebones install. Once you begin installing stuff that will fill fast. You also want a safe amount of headroom. Also keep in mind, if you leave it too small and intend to upgrade using the Update Manager to a newer release you will run out of headroom and be forced to do a manual install.

---

### Post by dFlyer on 2011-06-22
I'd make it 10 - 12 gig for home depending on what program you want to install and make the rest home. Another choice is to leave it as all /. The only problem with all root is when you do a cd install it wipes your home directory.

---

### Post by Bucky Ball on 2011-06-22
> **dFlyer said:**
> I'd make it 10 - 12 gig for home depending on what program you want to install and make the rest home. Another choice is to leave it as all /. The only problem with all root is when you do a cd install it wipes your home directory.

You mean:

> I'd make it 10 - 12 gig for home ...

You mean / I presume ...

Last point correct; better to have a separate /home for many reasons. ;)

---

### Post by jerome1232 on 2011-06-22
Yes that was normal for it to just show up as a folder, all partitions are mounted like that in linux.

If you want an icon for your data drive, mount it somewhere in /media, I guess I should've thought about that ;)


ie /media/data would've made it show up as "data" on your desktop. It doesn't really matter if you specify the mount point during installation or use some utility after the install to do it, I just find it easier to do as part of the install.


While I agree a separate /home has it's advantages for some users, it can just be confusing to newer users and so I don't usually recommend it to someone who is just getting used to Ubuntu.

---

### Post by NBFlyacker on 2011-06-23
Quick question.  I'm getting the hang of things and I've reinstalled with the latest version.  I did my boot partition like you guys suggested and now have a /, /home, and a swap on the 50 gig partition.  I didn't mount the ntfs partition.  When I got into ubuntu, the 100 gig showed up in my "places" and I see that it is in /media as well.  All is great.  It is mounted as /media/media center. "Media Center" was the drive label I named it in Windows.

However, when I created an account for my wife, she can't see it.  When I navigate to /media/media center, it says she doesn't have permissions to get into it.  How do I make it so that she can see it in her "places" and access it just like I can.  

I even tried making her account as an administrator.  My unbuntu book does not cover this at all.  I just shows me how to mount a drive if it isn't mounted, for some reason.

thanks,

rb

---

### Post by Bucky Ball on 2011-06-24
You might find something digging through here:

[http://www.google.com.au/#hl=en&source=hp&q=change+user+permissions+ubuntu&oq=change+user+permissions+ubuntu&aq=f&aqi=g1g-b1&aql=undefined&gs_sm=e&gs_upl=2149l9687l0l32l28l1l8l8l0l341l2788l8.4.6.1l19&bav=on.2,or.r_gc.r_pw.&fp=e32681dc5aaedc19&biw=1366&bih=596](http://www.google.com.au/#hl=en&source=hp&q=change+user+permissions+ubuntu&oq=change+user+permissions+ubuntu&aq=f&aqi=g1g-b1&aql=undefined&gs_sm=e&gs_upl=2149l9687l0l32l28l1l8l8l0l341l2788l8.4.6.1l19&bav=on.2,or.r_gc.r_pw.&fp=e32681dc5aaedc19&biw=1366&bih=596)

The first link, even if it doesn't help in this situation, will be instructive. ;)

---

