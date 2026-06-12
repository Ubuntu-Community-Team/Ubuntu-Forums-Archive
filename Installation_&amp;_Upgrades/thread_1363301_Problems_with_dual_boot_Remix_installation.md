---
title: "Problems with dual boot Remix installation"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by Drjim on 2009-12-24
I'm trying to install Remix on my netbook from a usb drive. Everything is fine until I get to the partitioning part. At that point I get a screen that says "there appears to be more than one operating system on your drive" and I'm given the choices of using the entire hard drive and wiping what's already there or doing a manual install. 

Windows 7 starter is the main OS but apparently there's a 15 gig partition that holds Vista. No idea why. 

Anyway, I didn't want to wipe my hard disc and chose "manual" even it also said "advanced", which I definitely am not. I was able to reduce the main windows partition, leaving about 80 gig free but can't proceed from there. 

Is there some way to get a guided partitioning without wiping windows? Failing that, are there instructions somewhere for a manual partitioning? All I was able to find were instructions for the guided partitioning which option it seems I'm not being offered.

Thanks,

Jim

---

### Post by mikewhatever on 2009-12-24
There is no guided partitioning in the Manual option, but since you've already resized the Windows partition and freed the space, guided wouldn't be a good choice. You can try going back to the first partitioning screen (where you get the selections) and look for a new option saying 'Use the largest continuous space...'. Select that, and the partitioner should do the rest automatically.

---

### Post by Drjim on 2009-12-24
> **mikewhatever said:**
> There is no guided partitioning in the Manual option, but since you've already resized the Windows partition and freed the space, guided wouldn't be a good choice. You can try going back to the first partitioning screen (where you get the selections) and look for a new option saying 'Use the largest continuous space...'. Select that, and the partitioner should do the rest automatically.


Unfortunately, the largest continuous space is the windows partition at about 100 gig. I made the partition for ubuntu about 83 gig.

---

### Post by raymondh on 2009-12-24
> **Drjim said:**
> Unfortunately, the largest continuous space is the windows partition at about 100 gig. I made the partition for ubuntu about 83 gig.

DrJim,

Happy Holidays :)

Want to do a manual install?  Simple (root and swap) or with a separate /home?

Go live session and access gparted to post back a screenshot of gparted ... or if you want (from terminal)  

```
sudo fdisk -l
```

and we'll try to make a mini-guide for you. The screenshot will help visualize the HD.

Regards,

---

### Post by mikewhatever on 2009-12-24
> **Drjim said:**
> Unfortunately, the largest continuous space is the windows partition at about 100 gig. I made the partition for ubuntu about 83 gig.

Well, the secret is to not make any partitions for Ubuntu. Leave the space unallocated, and the installer should detect that as the continuous space.

---

### Post by Drjim on 2009-12-24
> **mikewhatever said:**
> Well, the secret is to not make any partitions for Ubuntu. Leave the space unallocated, and the installer should detect that as the continuous space.

OK, it turns out that the I hadn't finalized the partitioning and was able to return to the original partitions that came on the computer. My problem is still that, when I get to the partitioning screen, the only guided option is "erase and use entire disc" I get a warning that this will delete my windows7 loader. I went a couple steps on that path, saw a brief "guided partitioning" message, got the "who are you" screen but was afraid to go farther  after I got to step 6 of 6 with this warning:

This will destroy all data on an partitions you have removed as well as on the partitions that are going to be formatted.

The following partitions are going to be formatted:
partition #1of SCS/1 (0,0,0) as ext 4
partition #5 of SCS/1 (0,0,0) as swap

I'm afraid that this is going to wipe my windows 7 OS if I hit the "install" button. I've gotten no screens that allow me to size the partitions. 

Would I be more likely to have a better guidance experience (eg guided partitioning without warnings of wiping my windows OS)if I tried installing 9.10 or 9.04 rather than remix?

Thanks for all your help,

Jim

---

### Post by Drjim on 2009-12-25
I hope everyone had a great holiday!

I've attached a screenshot ofthe partition page that illustrates my problem. I don't see an option to do guided partition without wiping the windows OS. 

Suggestions?

Thanks,

Jim

---

### Post by mikewhatever on 2009-12-25
You seem to have four primary partitions on that disk, and if that's the case, any further partitioning would not be possible before deleting one of the existing partitions. Could you post the output of <sudo fdisk -l>, without brackets, from Applications->Accessories->Terminal. The first two partitions. sda1 and sda2, are clearly labeled as Windows related. Do you know what's on the other two?
In any case, guided partitioning is not an option with such a layout, and you'll have to go with the manual.

---

### Post by raymondh on 2009-12-25
Jim,

Mikewhatever is right.  Remember the 4 partition rule.  Either:

- 4 primary partitions or;
- 3 primary + 1 EXTENDED

Logical partitions reside inside an extended and you can have as much as your system can take.

One of your existing primary partitions has to go (or converted to extended) to house Ubuntu.

---

### Post by Drjim on 2009-12-25
Well, I have the two windows OS partitions, one for Vista (don't know who I need that) one for windows 7. when I started my netbook, it set up a 41 gig partition to house the recovery and backup data. There also seems to bd a c and d drive partition. The D drive seems to have nothing on it. 

I could easilly get rid of the D or the vista partition.....if someone would tell me how to to that. 

Mike, I'm attaching a screenshot to the info you asked for.

Thanks,



Jim

---

### Post by Drjim on 2009-12-26
It worked! 

I deleted the D drive and now the ubuntu guided partitioning is working! 

Hopefully everything will go smoothly now.

Mike and everyone, thanks bunches for your help.

Jim

---

