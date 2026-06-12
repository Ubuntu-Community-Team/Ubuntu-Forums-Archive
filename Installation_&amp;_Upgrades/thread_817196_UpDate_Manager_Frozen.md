---
title: "UpDate Manager Frozen"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by concerto on 2008-06-03
I have recently upgraded to hardy from gusty.  I have over 100 updates pending.  when I click on update manager it freezes before the password prompt so I cant get any ware.  I haven't been able to do an update for weeks.  What can I do guys?

Thank you in advance.

---

### Post by lok on 2008-06-03
Try opening Synaptic ( System > Administration > Synaptic Package manager ) 
Click reload and then Mark all updates and then apply.
If synaptic doesn't work try try updating from a terminal.

Applications > Accessories > Terminal

Type in:
sudo aptitude update
sudo aptitude upgrade

Hope that helps

---

### Post by concerto on 2008-06-03
I did it and it updated for a long time.  then i restarted.  it still dosent work.  I don't know what to do.  i'm going to reboot again.

---

### Post by abn91c on 2008-06-03
try in a terminal sudo apt-get install -f

---

### Post by ironspeeder on 2008-06-03
I looked over the forums and this problems seems to be a little more serious.  I'm having the same issue.  I wonder if one of the main servers for the download is having an issue?  I maybe a newbie to this but that's my guess.

---

### Post by concerto on 2008-06-03
Ok abn91c

I tried what you asked but it doesn't seem to work.
this is what i got...

concerto@Beau's computer:~$ sudo apt-get install -f
sudo: unable to resolve host Beau's computer
[sudo] password for concerto: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
concerto@Beau's computer:~$ 
concerto@Beau's computer:~$ 
concerto@Beau's computer:~$

---

### Post by Bubba64 on 2008-06-03
> **ironspeeder said:**
> I looked over the forums and this problems seems to be a little more serious.  I'm having the same issue.  I wonder if one of the main servers for the download is having an issue?  I maybe a newbie to this but that's my guess.

If you go to software sources in system administration or synaptic there are over 200 servers to choose from if you choose other then hit I think find best your computer will ping all of them for the fastest response it may be one that is a couple of days behind the main server as far as upgrades but it will be faster.

---

### Post by concerto on 2008-06-03
Thanks bubba but this doesn't work either.  This is because the computer freezes right before you are supposed to enter your password.  I think the password program is the problem now that I think about it not the update manager.

What do you think ironspeeder?

---

### Post by Bubba64 on 2008-06-03
> **concerto said:**
> Thanks bubba but this doesn't work either.  This is because the computer freezes right before you are supposed to enter your password.  I think the password program is the problem now that I think about it not the update manager.

What do you think ironspeeder?

Have you restarted your computer during this time, sometimes it takes a couple of reboots to get things working.

---

### Post by concerto on 2008-06-04
I have rebooted and repeated the steps many times.  :(  still no luck.

---

### Post by patrickjett on 2008-06-04
I am also not able to do updates, it is not the password, when I get ready to update, before I do I run the update, I check it locks the update also, I will try a few things and post what worked.

---

### Post by patrickjett on 2008-06-04
sudo update-manager
[http://ubuntuforums.org/showthread.php?t=617331&highlight=administrative+locks](http://ubuntuforums.org/showthread.php?t=617331&highlight=administrative+locks)
this had the fix for me.

thanks

---

### Post by patrickjett on 2008-06-04
sudo update-manager

Sorry about the earlier post it linked to nothing

---

### Post by WackyCat on 2008-06-08
I am a complete newbie with regards to Linux (< 1 week). I started having multiple problems with the update manager, and Synaptic would not even open. (Other apps which would not open were hardware drivers, hardware testing, software sources, and startup-manager. All of these were solved immediately by following a post I read that said it was probably a network problem and to correct it I did the following...opened System, Administration, Network Tools and made sure that the Host name under the General tab was EXACTLY the same as the Alias of IP 127.0.1.1 under the Host tab. I hope this helps someone like it did me.

---

### Post by SteveF48 on 2008-06-10
I had the same problem, Update Manager showed me lots of updates, but just sat there after I clicked on Install Updates.
I tried changing the sources, but neither Software Sources, nor Synaptic Update Manager will run from the System Administration menu. The seem to start (an icon appears at the bottom of the screen) but die before displaying anything.
I think that I've managed to install the updates, by chosing Recovery Mode on the boot options, then repair broken packages. WackyCat's suggestion seems to have fixed access to the apps, thanks mate.

---

### Post by josuna on 2008-06-11
I am having the same problem on my two ubuntu machines...I hope someone finds a solution.

---

### Post by adad on 2008-06-13
I had the same problem. Somehow my /etc/hosts file got corrupted.

I replaced it with a fresh hosts file and it worked.

Just make sure your host name is the same as the one you use for your computer and that the file contains at least: 

127.0.0.1 localhost
127.0.1.1 the-name-of-your-host

:popcorn:

---

