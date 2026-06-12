---
title: "Dose anyone know how to burn CDs /ISO Images with Ubuntu"
date: 2005-02-03
forum: Installation &amp; Upgrades
---

### Post by Eejay on 2005-02-03
I installed KB3 last night, but for some reason or another it's not working is there by any chance another CD burner that is computable with Ubuntu Linux 

I was told that all I had to do was right click on the ISO image that I wanted to burn then chose the option that says write to disk, however I don't see that option listed when right clicking on the ISO image the only options that I see is save to disk ( I'm assuming that means “hard disk” than after that open with file roller, nothing else.

So if anyone knows a way to get KB3 to work or a code that will install a CD burner please let me know cause I really need to download an ISO image asp

---

### Post by mark on 2005-02-03
[QUOTE=Eejay]I installed KB3 last night, but for some reason or another it's not working is there by any chance another CD burner that is computable with Ubuntu Linux 

I was told that all I had to do was right click on the ISO image that I wanted to burn then chose the option that says write to disk, however I don't see that option listed when right clicking on the ISO image the only options that I see is save to disk ( I'm assuming that means “hard disk” than after that open with file roller, nothing else.

So if anyone knows a way to get KB3 to work or a code that will install a CD burner please let me know cause I really need to download an ISO image asp[/QUOTE]You have to download the ISO to your hard drive before you can burn it with any app (as far as I know).  Once downloaded, I just use Nautilus - navigate to the directory containing the ISO file, select the file, right-click & select _W_rite to Disc...

Works for me - hope this helps!

---

### Post by poofyhairguy on 2005-02-03
[QUOTE=Eejay]I installed KB3 last night, but for some reason or another it's not working is there by any chance another CD burner that is computable with Ubuntu Linux 

I was told that all I had to do was right click on the ISO image that I wanted to burn then chose the option that says write to disk, however I don't see that option listed when right clicking on the ISO image the only options that I see is save to disk ( I'm assuming that means “hard disk” than after that open with file roller, nothing else.

So if anyone knows a way to get KB3 to work or a code that will install a CD burner please let me know cause I really need to download an ISO image asp[/QUOTE]

The other post nailed it. For the record, to get k3b to work use the command:

gksudo k3b

---

### Post by Eejay on 2005-02-03
Thanks Mark
The old laptop that I usually use to test distros with isn't working and I'm afraid to do anything that will ruin this $4000 computer, just wanted to double cheek and make sure that downloading one of these big ole' ISO images directly on to the hard drive wouldn't be an over kill.

It's to bad that KB3 won't work with Ubuntu, maybe I installed it wrong, not sure but a lot of people are saying something about KB3 being a CD burner that is only meant to be used with KDE and not Gnome...

---

### Post by zorba64 on 2005-02-04
Try here for CD burning using Gnome/Nautilus
 [http://ubuntuguide.org/#cddvdburning](http://ubuntuguide.org/#cddvdburning)
 
 Mike

---

### Post by Eejay on 2005-02-04
Thanks for the replies
KB3 made the computer crash
Guess everyone was right when they said that it wouldn't be a wise  idea to install KB3 on a Gnome desktop.

Might it was a  Coincidence, I don't know...

Has this ever happened to anyone else, I'm most certain that KB3 was responsible for making the computer crash, I just now had to reinstall Ubuntu in order to get the computer working again.

I'm hoping that this was just a coincidence, but it was most likely not :sad:

---

### Post by Mikeynewbie on 2006-01-10
t's to bad that KB3 won't work with Ubuntu, maybe I installed it wrong, not sure but a lot of people are saying something about KB3 being a CD burner that is only meant to be used with KDE and not Gnome...

K3B is working fine on my laptop which is running Ubuntu you may have installed it incorrectly or are missing some needed packages the only thing I can't do is rip audo as mp3 and I have installed the mp3 package and still get errors but wav and other formats work fine.

---

### Post by ardchoille on 2006-01-10
You can use graveman (it's in the repos) to burn ISO images. It works great for me.

---

