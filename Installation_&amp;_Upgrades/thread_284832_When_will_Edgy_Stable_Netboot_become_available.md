---
title: "When will Edgy Stable Netboot become available?"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by UberKnight on 2006-10-26
Hi Everyone

I've been reading the forums for a while but this is my first post:D .

I've been eagerly awaiting Edgy to do a netboot install on my old laptop (dvd-rom broken, doesn't boot from usb).

Now before someone goes denting my armour, I've read all the threads about how to do this.  All I'd like to know is if anyone has a link to download the netboot files for Edgy stable (i.e. today's version -- 26 Oct 2006).  I can find the release candidates, but am eager to get my hands on "final" and begin the slow process of installation over the net (on a 384kb line).

You'll be seeing more of me clanging around from time to time ;) 
UberKnight

---

### Post by UberKnight on 2006-10-26
erm... I'm pretty eager to get going on this.  Anyone have any idea when the netboot images will be posted?

---

### Post by Kallewoof on 2006-10-26
Why not just install e.g. Dapper and then dist-upgrade to Edgy?

I've upgraded this way all the way from Breezy, with more or less no problems whatsoever on two separate machines (my desktop and my laptop). 

-Kalle.

---

### Post by UberKnight on 2006-10-26
Thanks for the tip, but unfortunately bandwidth is very expensive here in South Africa.  I'd prefer to do the net install and already be up to date that download what I'm guessing might be 700MB of data (for Dapper) and then maybe another few hundred megabytes worth of updates...

How do we get the developers to hurry up and update *current *here: [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/) to 6.10 stable? :rolleyes:

---

### Post by UberKnight on 2006-10-26
Ok, looks like netboot isn't going to be updated today.

What would be the difference in me using the netboot.tar.gz of lase weeks release candidate instead of waiting for today's final version?

Thanks for the help guys ;)

---

### Post by christhemonkey on 2006-10-26
You will just have a few more updates to do thats all.

---

### Post by UberKnight on 2006-10-26
Thanks for that tip :)

I'm struggling to get this to work though.  I'm following the instructions here [https://help.ubuntu.com/community/Installation/WindowsServerNetboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot") but end up at the boot screen, that is to say boot: ...

I can access the the menu by pressing F1, etc. but as soon as it try and install nothing happens.

Do I need all the contents of [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/") directory?  According to the guide I've been following, I only need netboot.tar.gz.

But I must be doing something wrong, because even though I am following the instructions of the guide to the letter, it's not working...

---

### Post by UberKnight on 2006-10-26
Finally figured out the problem.  The guide ([https://help.ubuntu.com/community/Installation/WindowsServerNetboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot")) seems to have a small error.

> 6. Go To ../cb/netboot/ubuntu-installer/i386/ or ../cb/netboot/ubuntu-installer/amd64/ then copy "pxelinux.cfg", "linux", and "pxelinux.0". Now paste them in ../cb/netboot/


**In fact, "linux" needs to remain in ../cb/netboot/ubuntu-installer/i386/ -- only copy "pxelinux.0" and the directory "pxelinux.cfg".** ](*,) 

(In fact, when I extracted "netboot.tar.gz" it created two dummy files (0 size) in "\netboot" which I simply erased in order to copy their namesakes into the directory.)

Hope this helps someone else :)

---

### Post by UberKnight on 2006-10-27
Update: I woke up this morning to a brand spanking new Ubuntu on my old laptop (Fujitsu Lifebook S4545)!  Installation via netboot went off without much of a hitch once I sorted out the the issue pointed out in the post above.

Silly me: Once the netboot has loaded the base-install system, a menu pops up asking which desktop you would like to download and install.  I chose Ubuntu and things were running along, but then it seemed to get stuck at 6% for what seemed like hours.  It was about this time that my battery was nearly dead (I have a horribly finicky power connector and this seems to have lost the AC connection).  Thinking this had caused the install to stall, I rebooted and started the whole process over... ](*,) 

Well, this cost me some bandwidth (I pay for 5GB / month, for those of you that don't know, we are hamstrung by our telecoms company, Telkom, which happens to have a monopoly in South Africa and charges exorbitant ADSL fees...) but at least I have a shiny new system to show off to colleagues!

By the way, I recently discovered that Mark Shuttleworth is behind another project in South Africa to make the distribution of Open Source software (e.g. Ubuntu) easier in SA (the problem is the exorbitant cost of bandwidth).  His solution: [Freedom Toaster]("http://www.freedomtoaster.org/"), "vending machines" where you can burn .iso's of various distros, etc.  (Think taking you own coffee mug (blank CD/DVD) to a coffee vending machine and pouring yourself a free cup ;) ).

---

### Post by UberKnight on 2006-10-29
Mohammed sent me a private message, but it might be useful to others, so I have posted it here:

[QUOTE=Mohammed Abbas]Hi there ,
I hope you're fine ...

About your topic listed here , 
[http://www.ubuntuforums.org/showthread.php?t=284832&highlight=netboot](http://www.ubuntuforums.org/showthread.php?t=284832&highlight=netboot)

I was just confused , cause I managed to begin a netboot installation using this method here ,
[https://wiki.ubuntu.com/Installation/FromWindows?highlight=%28installation%29](https://wiki.ubuntu.com/Installation/FromWindows?highlight=%28installation%29)

I canceled when the installer reached partitioning step ... but I coudn't figure out which version is gonna be installed on my machine !!

The question now , I need to do a clean install of Edgy to dual boot with working windows XP ... 

Could you tell me what the difference between the two methods ?

And if the method here , [https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot) 
is fine , could you explain how could I install Edgy using it ?

Regards,
Mohammed Abbas[/QUOTE]

Here is my response:

> Hi Mohammed

I am not much more than a beginner myself, so you would perhaps do better searching the forums. Nevertheless, I will try to help:

[LIST=1]
[*]I can't tell you the difference between the two methods.
[*]I used the second method: [Installation/WindowsServerNetboot]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot")
[*]I used [this edgy]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/netboot.tar.gz") netboot image
[*]Under [QUOTE]This is how we do it (Breezy Style) point 6. -- modify as per my [post]("http://www.ubuntuforums.org/showthread.php?t=284832&highlight=netboot")
[*]When you get to partitions, create new partitions in free space (I hope you have made free space so that your xp partition doesn't use the whole disk) and install in the free space.
[/LIST]
If you need more information on doing a dual boot installation, search the forums.

Hope this helps!
UberKnight[/QUOTE]

---

