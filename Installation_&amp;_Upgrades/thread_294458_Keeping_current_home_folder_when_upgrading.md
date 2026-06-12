---
title: "Keeping current /home folder when upgrading"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by goofla on 2006-11-06
If I am using any other flavor of linux and I choose Ubuntu, can I migrate (keep) my /home folder when I switch to Ubuntu? Say for example I have the following:

/dev/hda1 / 10 GB
/dev/hda2 /home 20 GB


Can I install Ubuntu on /dev/hda1 and have it use my /dev/hda2 folder as /home?

---

### Post by Max_Might on 2006-11-06
You can install Ubuntu on /dev/hda1 and then mount /dev/hda2 :)
you just have to format /dev/hda1 before you install Ubuntu on it!

---

### Post by goofla on 2006-11-06
But wont Ubuntu install a home folder on /dev/hda1? How do I get it to use my exisiting so applications and etc... know it is there.

---

### Post by albertran on 2006-11-06
Can't you just rename the delete ubuntu's new /home folder, and then mount the new hardrive as /home?

---

### Post by taurus on 2006-11-06
Just tell the installer to mount /dev/hda2 to /home while /dev/hda1 to / but DO NOT format /dev/hda2.

---

### Post by KaeseEs on 2006-11-06
When installing Ubuntu and setting up partitions, mark /dev/hda2 to be untouched and set the mount point to /home.  Format /dev/hda1 to your filesystem of choice, set the partition as bootable, and set the mount point as / .  That should take care of things.

EDIT:  g'ah, taurus beat me to it

---

### Post by boyofford on 2008-01-14
confused! 
made a mess of my Ubuntu 7.10, was playing around with compiz settings and ended up with a black screen that was there on reboot!

so figured i could just reinstall keeping my original /home partition and not formating it (i created a home partition in original, first installation).

this didn't work first attempt, could see partition but did not have permission to view files (though I used same username and password, thought that would sort it?)

Then figured i had to set partition as home again so reinstalled telling installer to use partition as /home but not to format.... and now its vanished!!!! 

what am i doing wrong? have I lost the old home partition now?
not to much in there as only installed Ubuntu for first time a week ago but still would like to know were I went wrong?!

---

### Post by Digger78 on 2008-01-14
when you get to the partitioner highlight your "home" partition > edit partition

the only thing you need to do is set the mount point as **/home**

then save it

highlight the partition you want to use as your root partition, put an X in the box under the "format" column  > edit patition

set the file sytem as 'ext3'
set the mount point as '/'

save it and continue

if you still dont have permissions after the install, they can be changed.

---

### Post by boyofford on 2008-01-14
> **Digger78 said:**
> when you get to the partitioner highlight your "home" partition > edit partition

the only thing you need to do is set the mount point as **/home**

then save it

highlight the partition you want to use as your root partition, put an X in the box under the "format" column  > edit patition

set the file sytem as 'ext3'
set the mount point as '/'

save it and continue

if you still dont have permissions after the install, they can be changed.

erm.. I did all that the second time round but now if i go to 'computer' under places menu the partition does not even show up!

---

### Post by Digger78 on 2008-01-14
Have a look in  /media

---

### Post by boyofford on 2008-01-14
no, not there.
did i mention i've got comp as dual boot with vista, could that have anything to with it?
figure lost home partition then? just a hiccup in installation process?

No big deal!
Cheers for help though, think i did it the right way, even if computer didn't!

---

### Post by Digger78 on 2008-01-14
you don't even have a /home folder?

I had no idea that was possible

you can't open a terminal and

```
cd /home
```

---

