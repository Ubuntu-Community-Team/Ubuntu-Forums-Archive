---
title: "E: Internal Error, Could not perform immediate configuration (2) on mountall"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Wilford Grimley on 2010-04-29
[FONT=Arial]Hello All, 

[/FONT]
[FONT=Arial]Total linux n00b here, anyway on with the show. I recently installed ubuntu as the default os on my laptop due to various reasons and now am wanting to install kubuntu. I am not in the mood for making a live cd so i did what any sensible person would do and found a way around it. I open terminal and type```
 sudo apt-get install kubuntu-desktop
```. A series of lines of text pop up and then one that asks whether or not I would like to continue, I of course press yes and then a recieve this error: [/FONT]E: Internal Error, Could not perform immediate configuration (2) on mountall.
I did some googling and got many supposed results suck as simply typing: ```
sudo apt-get clean 
sudo apt-get update
``` but, alas, no dice. I am hoping someone knows a no-brainer quick fix for my n00bish ways. 
[RIGHT]Thanks,
Grimley
[/RIGHT]

---

### Post by sumo2010 on 2010-05-05
Just wanted to say that I'm getting this error too. I'm running kubuntu as well. And I booted up in LiveCD, mounted it, then chroot into it. when i run sudo apt-get -f install (or remove), I get the same error.

Mine came from an incomplete upgrade from 9.10 to 10.04.

---

### Post by troyski on 2010-11-01
Hi you guys,

I was trying to avoid having to buy a Linux Mag to get the latest CD to upgrade, so I tried the more organic way and just did it through the OS itself, and now I get the same error message when the upgrade failed.  Worse than that, now I have a new CD and the upgrade won't even work because of the problem.

[INDENT][COLOR="blue"]E: Internal Error, Could not perform immediate configuration (2) on mountall[/COLOR][/INDENT]

**Running mountall from the prompt, I got the following error msg:** 

[INDENT][COLOR="Blue"]"This is normally a bug in some application using the Dbus Library Process 1593: arguments to dbus_pending_call_set_notify() were incorrect, assertion "pending != NULL"failed in file dbus-pending-call.c line 596"
[/COLOR][/INDENT]

Any advice on how to reverse this problem would be greatly appreciated. The machine runs fine, but you can't upgrade at all as long as this problem's there.

---

### Post by michael24sny on 2010-11-01
I also found this error while installing kubuntu.Can you tell me how will i remove this error.

---

### Post by troyski on 2010-11-03
I was able to resolve this by using [[COLOR="Blue"]the "fuser" command [/COLOR]]("http://manpages.ubuntu.com/manpages/gutsy/man1/fuser.1.html")(can tell you which programs have a lock on which processes) to remove all locks on the mountall and/or dbus processes and then doing a partial upgrade thereafter.  

I found [this site]("http://manpages.ubuntu.com/") and [this link]("http://manpages.ubuntu.com/manpages/gutsy/man1/fuser.1.html") to be very helpful in doing so.

---

### Post by Dfairlite on 2010-11-29
^^Could you expand on this? I am not familiar with fuser (i'm pretty novice at all things linux :)) how exactly did you locate the processes?

---

### Post by dark_horse on 2011-05-06
Hi,

I am using Ubuntu 9.10 Karmic Koala and I really wanted to try amarok. I looked for the solution for amarok not being able to play the files and I found your site, Thanks a lot for the tip.

For those who encounter the error 
**E: Internal Error, Could not perform immediate configuration (2) on mountall**

Solution is the version of Ubuntu might be mentioned differently than what the sources.lst file is drawing updating from. To solve it type

*prompt> sudo vi /etc/apt/sources.lst*

in that change all the instances of lucid to karmic, to do that press ESC key and type
*:%s/lucid/karmic/*
save the file by typing ESC key followed by command
:wq 

after returning to prompt ,type 

[I]prompt> apt-get clean
prompt>ant-get update

[/I]if you get an error like
**E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)**

then become root for a while by typing 
*prompt> su* 
and then enter root password (to set root password type *prompt>su passwd*)

Proceed executing the above command ..
*prompt> sudo apt-get install kubuntu-restricted-extras*

I am typing this with amarok playing its first song..

HTH, Cheers!!! :P
Srini

---

