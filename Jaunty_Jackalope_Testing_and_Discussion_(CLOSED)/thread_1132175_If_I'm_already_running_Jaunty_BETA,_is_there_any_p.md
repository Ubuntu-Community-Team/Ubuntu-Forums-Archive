---
title: "If I'm already running Jaunty BETA, is there any point on dl'ing the final release?"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by smacattack on 2009-04-21
What I mean is...is an updated Beta just the same as the final version? So if i just do 'sudo-apt-get-update' I'll have the final release?

Sorry for such a noob question (and if it's been asked)...I've never used a Beta so long before (it's worked really well for me).

---

### Post by FuturePilot on 2009-04-21
> **smacattack said:**
> What I mean is...is an updated Beta just the same as the final version?

Yes. Just check Update Manager for updates. If there is none you have the final version come release day.

---

### Post by bennachie on 2009-04-21
Yes, but you might still want to download the final version after the rush has passed, just in case you need to do a fresh installation in the future. That will allow you to avoid repeating all the downloads for updates that have been issued since you downloaded the beta ...

---

### Post by durand on 2009-04-21
> **bennachie said:**
> Yes, but you might still want to download the final version after the rush has passed, just in case you need to do a fresh installation in the future. That will allow you to avoid repeating all the downloads for updates that have been issued since you downloaded the beta ...

Or while the rush is on. Bittorrent should be pretty fast then :)

---

### Post by joey-elijah on 2009-04-21
I'll just chip in that i upgraded to the final release of Intrepid from the beta and although it generally worked well, there were several conflicting issues that could only be sorted out by a fresh install of the final release. I don't know if this applies to Jaunty so much, but it saved a lot of wasted hours trying to get certain things to work.

---

### Post by Saint Angeles on 2009-04-21
> **joey-elijah said:**
> I'll just chip in that i upgraded to the final release of Intrepid from the beta and although it generally worked well, there were several conflicting issues that could only be sorted out by a fresh install of the final release. I don't know if this applies to Jaunty so much, but it saved a lot of wasted hours trying to get certain things to work.
also, if you do a fresh install of jaunty, you can use ext4... its fast!

---

### Post by FuturePilot on 2009-04-21
> **Saint Angeles said:**
> also, if you do a fresh install of jaunty, you can use ext4... its fast!

You can use Ext4 without doing a reinstall.

---

### Post by sports fan Matt on 2009-04-21
Id love to learn how...

---

### Post by alphacrucis2 on 2009-04-21
> **sox fan Matt said:**
> Id love to learn how...

You use tune2fs to convert an ext3 partition to ext4. You would need to boot off the live cd to run the command as you can't do it on a mounted partition.

**WARNING back up any important data before attempting this!**

From the liveCD terminal prompt:

```
tune2fs -O extents,uninit_bg,dir_index /dev/<dev name>
```

Make sure that <dev name> is the partition you want to change. The tune2fs will complete fast but the partition will be in an unusable state. The message it gives tells you what to do next. You must run efsck.


```
efsck -pf /dev/<dev name>
```

This can take a while. Make sure you let it finish.

You then need to modify the fstab. Assuming that the partition you just converted is the partition that has the fstab file you need to change in it. You need to mount that partition so you can do that:

```
mkdir /mnt/mypart
mount -t ext4 /dev/<dev name> /mnt/mypart
gksu gedit /mnt/mypart/etc/fstab
```

Change the fstab line for the partition you changed so that the ext3 bit reads ext4. Save the file and reboot normally.

---

### Post by joey-elijah on 2009-04-21
> **sox fan Matt said:**
> Id love to learn how...

So would i! AFAIK, you can only use EXT4 by doing a fresh install.

---

### Post by yosumi on 2009-04-21
someone please confirm the actual countdown of 9.04 final.

Is it right after 23h:59m:59s @ GMT +1?????????? 

I'm in Eastern time zone, so that means 8pm @ GMT -5????????? 

Thanks.

---

### Post by FuturePilot on 2009-04-21
> **yosumi said:**
> someone please confirm the actual countdown of 9.04 final.

Is it right after 23h:59m:59s @ GMT +1?????????? 

I'm in Eastern time zone, so that means 8pm @ GMT -5????????? 

Thanks.

There is no specific set time that it's released. It's released when everything is ready.

---

### Post by Enicko on 2009-04-21
I've been running the beta for a couple weeks now.  I had some help with the install and I'm not sure if I'm running ext4 or not. Where would I look to find out?

Also, has anyone ran the new ATI driver yet?  Any success?  The wait for 3d is klln me.

<warning Noob w/ strong IT support - still learning command line lingo>

---

### Post by Ravernomina on 2009-04-21
actually u can upgrade a EXT file system to a new one they were made for that wiki EXT3 and learn about it. Like i defrag my Ext3 by converting to to EXT2 then defrag then going back to EXT3 this is why Linux file system are the best :)

---

### Post by mikedep333 on 2009-04-22
Actually, I was under the impression that when you install the beta, RC, or any nightly version of a release and upgrade to the final, there are some leftover config settings from the those versions. I've run into some problems from installing a beta that I had to fix by reformatting with the final version.

---

### Post by joey-elijah on 2009-04-22
> **mikedep333 said:**
> Actually, I was under the impression that when you install the beta, RC, or any nightly version of a release and upgrade to the final, there are some leftover config settings from the those versions. I've run into some problems from installing a beta that I had to fix by reformatting with the final version.

As did i with the beloved Intrepid. Hence doing a clean install this time around!

---

### Post by novafluxx on 2009-04-23
> **mikedep333 said:**
> Actually, I was under the impression that when you install the beta, RC, or any nightly version of a release and upgrade to the final, there are some leftover config settings from the those versions. I've run into some problems from installing a beta that I had to fix by reformatting with the final version.

Thats why we can use the Janitor!! :guitar:

---

### Post by Zlatan on 2009-04-23
> **smacattack said:**
> What I mean is...is an updated Beta just the same as the final version? So if i just do 'sudo-apt-get-update' I'll have the final release?

Sorry for such a noob question (and if it's been asked)...I've never used a Beta so long before (it's worked really well for me).

Yes, in order to have an install CD plus you can keep your Ubuntu torrent seeded;)

---

