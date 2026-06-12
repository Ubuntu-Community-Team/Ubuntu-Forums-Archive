---
title: "Lost Ubuntu session"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by Oxlo on 2011-01-26
I had an Ubuntu session with two users with a lot of applications and games installed within. I tried to delete unused applications from Synaptic to make the computer run faster, but I did something wrong. When restarting my computer, I had a Dos-like display where I can log in and can see my files there but I was not able to copy them to a disk drive.
I tried also to repeair the session but it was in vain. It was all the time the same Dos-like interface coming. I installed after a new Ubuntu session in the aim to repair the original session or at least access the files and recover them.
 
Now I am stuck. Is there a way to access the old session from the new one or any tools to repair my lost session?
 
Many thanks.

---

### Post by cipherboy_loc on 2011-01-26
Log in as a regular user and try this:

```

cp ~/.xinitrc ~/.xinitrc.bak
echo "xterm" > ~/.xinitrc
startx

```If that works, then it is an issue with GDM. If it does not work than you need to run (making sure you are plugged into an ethernet cable):

```

sudo apt-get install gdm

```You will also have to install Xorg again, but I do not know the package for that (xorg-server is what it is on Gentoo). I will try and post back once this emerge completes from my Ubuntu system...



Cipherboy

---

### Post by Oxlo on 2011-01-26
Thanks for the tips.

First I am not that good in Linux, but I tried to follow your instructions.


I got the following error message after running the startx command:

[B]Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log[/B]

I tried after that installing the gdm, but got the following:

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 239 not upgraded.[/B]

I still have the problem. Please I need help to recover my session, I have important work there.

---

### Post by cipherboy_loc on 2011-01-26
Okay, so first of all I would update the system (239 packages will take a while to update...)
```

sudo apt-get update
sudo apt-get upgrade 

```

Then I would reboot and upon the system load, shortcut Ctrl+Alt+F7 (AKA do the shortcut CTRL+ALT+F7).  This should bring you to GDM.


Cipherboy

---

### Post by Oxlo on 2011-01-27
Hi again,
 
I updated and upgraded my system, but I am still confused.
 
I will explain again my problem.
 
I have now an Ubuntu session that is hidden (I can't access it now) and a new session where I can log in. 
 
I want to use the new session to be able to access my old (original) session containing important files or at least recover the files I have in my old session.
 
Now everytime I reboot my computer, I am only invited to the new session (I can see anymore the old session). Please help, I am sinking :(.
 
Does it solve the problem to delete the new session and try to repair the old one if it comes on Dos-like screen? If this is possible, then how to delete the new session?
 
Another question, what can the ALT+CTRL+F7 combination help in?
 
My advance thank for help.

---

### Post by cipherboy_loc on 2011-01-27
Okay, so let me get this straight:

When you start up your computer, all you get is something like:
> 
ubuntu login: 

Where ubuntu is your host name, right?

In your PM, you said:
[QUOTE=Oxlo]
I had an original session where I can access all my data, but I removed  some files, by error, to make my PC run faster. By starting up my PC, I  was able only to log in in a Dos-like screen where I can still see all  my files.
[/QUOTE]

By session, do you mean an install of Ubuntu? If so, then when you boot into it, you should log in, and try:

```

sudo killall X
sudo /etc/init.d/gdm

```

Wait a bit and then try CONTROL+ALT+F7 or CONTORL+ALT+F8. These change "virtual" terminals to the ones that X/X11/Xorg usually resides on. 


Also you said:
[QUOTE=Oxlo]
I didn't find anyway to repair this except by installing a new ubuntu  session (with a different username) along with the previous session. My  aim was to use the new session to access my old session or in the worst  case recover my files in the old session.
[/QUOTE]

If this means that you installed Ubuntu again from the LiveCD, along side your existing install, and the above steps don't work on your first install, then you can do this from your new install:

```

sudo mount -t [FS_TYPE] /dev/sda[DRIVE_NUMBER] /mnt
mkdir /home/[username on new install]/old_home
cp /mnt/home/[username on old install]/* /home/[username on new install]/old_home/ -prv
cp /mnt/home/[username on old install]/.* /home/[username on new install]/old_home/ -prv

```

and then copy over (you can use nautilus) anything that was NOT In your /home folder that you would like to keep. 

That works if you didn't specify to create a /home partition when you first installed Ubuntu.



If you have any more questions, post back here,
Cipherboy

---

### Post by Oxlo on 2011-01-28
> 
By session, do you mean an install of Ubuntu? 

 
Yes, I mean by session an install of Ubuntu. I had two usernames, "christian" for my original session (containing all my data) and "chris" for my new session.
 
> 
If this means that you installed Ubuntu again from the LiveCD, along side your existing install, and the above steps don't work on your first install, then you can do this from your new install:
 
Yes, my problem arises in this situation. When I reboot I got invited only to enter password for "chris" (new session) and can't have any option to log into my old session via username "christian".
 
[QUOTE]
```

sudo mount -t [FS_TYPE] /dev/sda[DRIVE_NUMBER] /mnt
mkdir /home/[username on new install]/old_home
cp /mnt/home/[username on old install]/* /home/[username on new install]/old_home/ -prv
cp /mnt/home/[username on old install]/.* /home/[username on new install]/old_home/ -prv

```

 
Can you explain more here?, I am not that good in Linux. 
What to use as a filesystem instead of [FS_TYPE] and for [DRIVE_NUMBER]?
 
Should I create a subdirectory "christian" in my home directory "/home/chris/" in my new session?
 
Thanks for answering.
Oxlo
 
[/QUOTE]

---

### Post by cipherboy_loc on 2011-01-28
Did that help you any? Please report back with what you have tried, etc.


Cipherboy

---

### Post by Oxlo on 2011-01-28
> **cipherboy_loc said:**
> Did that help you any? Please report back with what you have tried, etc.
 
 
Cipherboy
 
What should I use for FS_TYPE and DRIVE_NUMBER?
 
The top commands can't work because I can't access my old ubuntu session.
 
Oxlo

---

### Post by cipherboy_loc on 2011-01-28
Sorry about that, I didn't read the stuff in the (QUOTE) tags. 
 
To find DRIVE_NUMBER, run:

sudo fdisk -l

and it should give you something like:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x146f146e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3898    31310653+   7  HPFS/NTFS
/dev/sda2            3899        9092    41720774+   5  Extended
/dev/sda3            9093        9730     5118976   82  Linux swap / Solaris
/dev/sda5            3899        6047    17261811   83  Linux
/dev/sda6            6048        8672    21085281   83  Linux
/dev/sda7            8673        9092     3373618+  82  Linux swap / Solaris



```

You will see one or two Linux partitions, right? Your first one (in my case /dev/sda5) will be your original install, while your second one (/dev/sda6 in my case) will be your new install. So the revised commands would be (for me):

```

mount -t ext4 /dev/sda5 /mnt
mkdir /home/chris/christian
cp /mnt/home/christian/* -prv /home/chris/christian/
cp /mnt/home/christian/.* -prv /home/chris/christian/

```


Cipherboy

---

### Post by Oxlo on 2011-01-29
Hi CipherBoy,

This is what I got by running fdisk -l command:

255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000c8ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29637   238053376   83  Linux
/dev/sda2           29637       30402     6142977    5  Extended
/dev/sda5           29637       30402     6142976   82  Linux swap / Solaris


It seems that I have a single Linux session. I tried to mount /dev/sda1, but I couldn't find any directories or files stored at /mnt/home/christian.

Does thios mean that I have lost my original session?

I wish to thank you a lot for your continuous support.

Regards,
Christian

---

### Post by cipherboy_loc on 2011-01-29
I think you have lost your old session, but to be sure, boot the LiveCD and try running the boot script in my signature. 


Cipherboy

---

