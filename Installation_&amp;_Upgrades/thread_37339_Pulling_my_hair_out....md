---
title: "Pulling my hair out..."
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by fattyh on 2005-05-26
Right OK, I am new to ubuntu so go easy on me, but I have read loads of threads before I ask a stupid question.

Like many others, my gnome doesn't log in properly, I get the unable to look up host name error, and also no chance of using sudo to fix it, because it can't authenticate.

So I downloaded the the Live version, like a good boy, booted into live, sudo gedit - loaded etc\hosts edited it to include my host name in the first line, saved it successfully to \etc\hosts - reboot, take the live disk out, and ........... same problem, only when I go and look at \etc\hosts, it is not changed, and the date on it is still at the OS install date.

I checked that it is saving during the live session, and the date changes, but when I reboot it dissapears.

Am I looking at the right \etc folder (I only have 1 instance of Linux on my Laptop, and no MS Windows). Do I need to mount another volume?

Am I doing something totally newbie like?
Help would be appreciated.

Ian

---

### Post by ltmon on 2005-05-26
From the sounds of it you might actually be editing the hosts file on the live CD (forgive me if I'm pointing out something you've already checked).  Try make sure you are editing a hosts file from your hard drive partition that "/" is mounted on.

L.

---

### Post by fattyh on 2005-05-26
Thanks

I am definately editing the wrong file, the time/date on it is stamped at the boot time from the live CD. However, I don't seem able to mount my file system.  hda1 and hda2 and hda5 are crossed out in /dev

does this mean I cannot mount them? I tried, it just says that they do not exist in etc/fstabs.

I can see the volumes  in the device manager as hda1 hda2 hda5
I tried adding them to etc/fstabs, but to be quite honest I am not sure what I am doing, and no joy yet.

I must say, this seems to be quite a common problem. I hope I fix it soon as I really like the look and feel of ubuntu. I hate being a newbie.

Any one who answers will forever be my hero.....

---

### Post by fattyh on 2005-05-26
I FIXED IT (4 Hrs 17 Minutes)

I have no network card fitted at the moment, which probably confused the install.

Had to boot with live CD
Add mount point for hda1 /mnt/hda1
Edit /etc/fstab to allow mounting of hda1
Mount hda1 (used mount -a)
navigate to /mtn/hda1/etc (this is the mounted location of /etc)
sudo gedit hosts

1st line edited to read:

127.0.0.1 localhost.localdomain localhost ubuntu

where ubuntu is my hostname, depends what you named it during install.

/etc/hostname reads:

ubuntu

where ubuntu is my hostname, depends what you named it during install.

One comment, while things like this keep happening, less persistent newbies will be returning to Windows in a flash.
Thanks to Itmon for confirming that I was trying to update the Live CD virtual files.

Ian
 O:)

---

### Post by ltmon on 2005-05-26
No probs.

Good on you for being persistent anyway.  Ubunutu seems to be at the point right now that > 75% of users have a fantastic experience and the rest still have to muck around a bit to get it going.  Hopefully future releases will slowly improve this number.

---

