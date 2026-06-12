---
title: "Problem with package Manager - after update no more acces"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by elgatoconbotas on 2007-05-29
Hi There, 

i'm a very beginner and have installed ubuntu 7.04 a week ago. 
I have have installed the automatic update and ubuntu was updating the kernel yesterday. unfortunately it didn't complete it's taks and hang up. 

I restarted the system and wanted to access synaptic and got the message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repor


so I opend the  termnal and did what was askes for and got the message:

elgatoconbotas@elgatoconbotas:~$ sudo dpkg --configure -a
Password:
Richte linux-image-2.6.20-16-generic ein (2.6.20-16.28) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Running postinst hook script /usr/sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB grub.cfg file ...

Could not find /boot/grub/grub.cfg file. Would you like /boot/grub/grub.cfg generated for you? (y/N

and after that by pressing y or N - the system hang up again and I had to start again and I couldn' get acess to other processe in synaptic. 

Has anyone an Idea what I could do ??

Thank you !!!! for your help

---

### Post by weemikey on 2007-05-29
I'm screwed - I did the Feisty Upgrade and yesterday's update, then this morning I try to log on, Enter my username, password and  this is what I'm confronted with:

<User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved. File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.>

Come on Ubuntu!  I have absolutely NO idea what this means or what to do now to get everything back to normal.  I'm running this now off the Live CD vers. 6.06 LTS.  Thank God for small mercies.
I do NOT want to lose all of my work done since my last fatal crash a year ago.  HELP, HELP,
HELP please!!

weemikey

---

### Post by Junixx on 2007-05-31
Ok well a friend of mine had this problem and we just tried random things to get it working....it was pretty simple how to fix it though, just manually create a grub.cfg file:

```

sudo gedit /boot/grub/grub.cfg 
```

Now just leave it blank and save it, then run

```
sudo dpkg --configure -a
```

Hopefully that will work, it worked for him and he was very happy ;)

Sorry weemikey, I have not a clue where to start on that problem >.<

---

