---
title: "Feisty upgrade breaks GTKPod"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by mseeba on 2007-04-14
My recent upgrade to 704 on my Dell XPS M1210 has left me without the ability to update my iPod from GTKPod. It can't find  the directory structure and asks if I want to create it, to which I answer Yes. Then it errors out with: Error initialising iPod: Problem creating iPod directory or file: '/media/ipod/iPod_Control'.

GTKPod has been entirely stable for me from Breezy, through Dapper and Edgy until now.

Any advice on how to fix would be GREAT!

Enjoy.

---

### Post by vanmeir on 2007-04-18
I'm having the same problem.

---

### Post by vanmeir on 2007-04-18
I managed to fix the problem.  I'm not sure why, but the upgrade to feisty caused the ipod to no longer mount at /media/ipod, which is where GTKPod expects to find it.

I added a line to /etc/fstab that causes the ipod to once again mount at /media/ipod.  My entry looks like this:

> UUID=2C24-FB9E    /media/ipod vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

I got the UUID using "sudo vol_id -u /dev/[whatever the ipod is]".  The mount options are copied from what the system did automatically when the ipod was automounted; just enter the "mount" command without any arguments to see what options the ipod is mounted with.  I'm not sure if those are the "right" options, but they worked for me.

Hope this helps.

Edit:  There shouldn't be a space in "umask" above; I don't know what it formats like that.

---

### Post by ALIENDUDE5300 on 2007-04-19
try removing and reinstalling GTKPod

---

### Post by cicio on 2007-04-19
hi , i have the same problem with gtkpod in feisty
i don't understand why i have now this  "Error initialising iPod"... gtkpod worked very fine in edgy...
i tried uninstalling and installing one more time gtkpo-aac but i have the same problem..
any suggestions?

thankks

---

### Post by jnovek on 2007-04-21
Like the previous poster said, for whatever reason the iPod mountpoint has changed in Feisty --

In Edgy it was "/mnt/ipod" ...
In Feisty it is "/mnt/IPOD".

For those of you who are Linux newbies, Linux filesystems are typically case sensetive, so "/mnt/ipod" and "/mnt/IPOD" are two different things as far as GTKPod is concerned.

Solution (in GTKPod 0.99.8, anyway):
Edit -> Edit Preferences
Go to the "General" tab
At the top of this tab, click the "Set mountpoint or edit repository options"
Change the "iPod mountpoint" field from "/mnt/ipod" to "/mnt/IPOD".
Click all the OKs and load your iPod normally

Jason

---

### Post by redevil34 on 2007-04-23
Okay, I'm basically running into the same problem.  I got an iPOD Video 30 GB (gift just after going to Feisty) so it never touched Mac or Windows.  I'm seeing the IPOD in media, but nothing in mnt.  If I browse the computer it shows the iPOD and if I try to open it, I get a message "Unable to mount media. There is probably no media in the drive."  I'm guessing this just means that there's nothing on the iPOD which would be true.  

So being an noob when it comes to Linux...and command lines, I'm guessing I need to know what to do to make it mount in the first place.

---

### Post by Houman on 2007-04-26
hi everyone;

mine doesnt mount the ipod anywhere at all! I installed feisty 2 days ago and havnt been able to use my ipod since then, i also looked under /mnt and /media, there was nothing, for some reason ipod is not automounting;


regards
Houman

---

### Post by supafly_stud on 2007-04-27
**Quick fix for GTKPOD in FF:**

*plug in your ipod
*open up GTKPOD
*go to this on the menubar: "edit">"edit repository/ipod options"
*look on the top field that says "IPOD MOUNTPOINT"

>browse around the / filesystem to see where your Ipod was mounted, it should probably be in /media/*[ipodname]*

>FOR EXAMPLE: my Ipod was called "ZACH JOHNSON" (I changed my name for privacy) in windows
>in ubuntu, it loaded it under the media directory as "/media/ZACH JOHNSO"  (that's right, no N)

>now go back to that GTKPOD "edit repository/ipod options" and type ```
/media/ZACH JOHNSO
``` in that same field

It should work like a dream after that!!

If anybody got any questions let me know, I'm no expert but I got my Ipod to work this way.

ALSO: remember that you always have to format your Ipod in Itunes before you can edit it in a 3rd party program like GTKPOD, well as of the best to my knowledge anyways....

---

### Post by kditty on 2007-04-28
> **jnovek said:**
> Like the previous poster said, for whatever reason the iPod mountpoint has changed in Feisty --

In Edgy it was "/mnt/ipod" ...
In Feisty it is "/mnt/IPOD".

For those of you who are Linux newbies, Linux filesystems are typically case sensetive, so "/mnt/ipod" and "/mnt/IPOD" are two different things as far as GTKPod is concerned.

Solution (in GTKPod 0.99.8, anyway):
Edit -> Edit Preferences
Go to the "General" tab
At the top of this tab, click the "Set mountpoint or edit repository options"
Change the "iPod mountpoint" field from "/mnt/ipod" to "/mnt/IPOD".
Click all the OKs and load your iPod normally

Jason

thanks, this worked fine for me. i had a feeling it had to do with the letter case but wasnt sure what to do without messing stuff up. thanks a lot.

---

