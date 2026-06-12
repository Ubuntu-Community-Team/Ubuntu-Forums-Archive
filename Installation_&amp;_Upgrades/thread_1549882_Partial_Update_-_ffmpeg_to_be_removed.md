---
title: "Partial Update - ffmpeg to be removed"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2010-08-10
Just wondering if anyone else has this partial upgrade being offered to them:
**ffmpeg, libavdevice52, libpostproc51, libswscale0** are held back (grayed out) in Update Manager.

I only use Update Manager manager to see if there are any updates and then use 
**sudo apt-get update**, **sudo apt-get-upgrade** and **sudo apt-get dist-upgrade **
to actually examine the updates as it shows if anything will be removed without anything to replace it.

And I know to _never do a partial upgrade_.

Update Manager displays "Partial Upgrade" with the files listed above grayed out.

I did use **sudo apt-get-upgrade **to install a few packages earlier that were safe to install and now - 

**sudo apt-get-upgrade** currently gives this output:
```
The following packages have been kept back:
  ffmpeg libavdevice52 libpostproc51 libswscale0
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded
```.

**sudo apt-get dist-upgrade** gives this output: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
[COLOR=Red]The following packages will be REMOVED:
  ffmpeg[/COLOR]
The following NEW packages will be installed:
  libavutil50 libva1
The following packages have been kept back:
  libavdevice52
The following packages will be upgraded:
  libpostproc51 libswscale0
2 upgraded, 2 newly installed, 1 to remove and 1 not upgraded.
Need to get 362kB of archives.
After this operation, 569kB disk space will be freed.
Do you want to continue [Y/n]? 

```I certainly am not going to allow ffmpeg to be removed. So, I guess the normal protocol is just to wait until all of these are available right?
This is the first time I have noticed seeing this since Lucid final was released, so that is why I am asking.
Thanks in advance!

---

### Post by XyCO on 2010-08-10
I have also got this message from update manager, I have searched google but have not yet found anything.

I have not tried to update, but it may be safe to update anyway, but I will probably wait a couple of days before I do a update to be on the safe side.

I have not done any real lookup on what the new packages exactly does but they have something to do with ffmpeg atleast.

But someone who know more should check into it, to see if it atleast is safe to do :)

---

### Post by Cavsfan on 2010-08-10
I know one thing for sure, if Update Manager says it will do a partial update, you should not do it.
You could be removing things that may mess your system up. And you will probably wind up 
starting a thread on here about what it did asking how to fix it. And possibly wind up doing a clean install.

I am reasonably sure that waiting it the right thing to do, but I just wanted someone with more knowledge about this issue to say so.

Thanks for your response though. :)

---

### Post by Cavsfan on 2010-08-10
> **XyCO said:**
> I have also got this message from update manager, I have searched google but have not yet found anything.

I have not tried to update, but it may be safe to update anyway, but I will probably wait a couple of days before I do a update to be on the safe side.

I have not done any real lookup on what the new packages exactly does but they have something to do with ffmpeg atleast.

But someone who know more should check into it, to see if it atleast is safe to do :)

Update Manager is not the best way to get your updates. a friend calls it Update Mangler! LOL!
These 3 command are the best way:
[B]sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade[/B]
They will accomplish the same as Update Manager, but will tell you more info.
I just use Update Manager to see if there are any updates to be gotten and then close it.
(No offense intended to any Update Manager programmers out there!)

As I said. I was able to get some updates from **sudo apt-get upgrade** but, the updates that 
**sudo apt-get dist-upgrade** wanted to perform is where the problems showed up.

---

### Post by Lucky75 on 2010-08-10
Yup, I'm getting the same thing, but it's also telling me to remove zoneminder.

When I sudo apt-get upgrade, I get

```

The following packages have been kept back:
  ffmpeg libavdevice52 libavformat52 libpostproc51 libswscale0
The following packages will be upgraded:
  acpi-support
1 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

---

### Post by Cavsfan on 2010-08-10
I'm thinking we just leave it until it fixes itself and the correct updates are available.

I went ahead and upgraded acpi-support a while ago and a few other things this morning as that didn't hurt anything, 
it's just the other command I will not enter "y" to - **sudo apt-get dist-upgrade** as removing stuff w/o replacing it is bad...

---

### Post by Cavsfan on 2010-08-11
I am guessing the answer was to just wait as today updates were w/o asking about a partial install...

I will just wait in the future...

---

