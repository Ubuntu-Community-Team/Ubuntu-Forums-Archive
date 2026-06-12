---
title: "Gutsy install shuts at 94% while 'setting up grub)"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by mushroomcloudwarrior on 2007-11-18
Right, i'll get straight to the point..i have a Dell vostro 1500 and i want a dual boot laptop with **windows xp and Kubuntu** - gutsy (7.10) on it.


Config;
Intel Core 2 Duo 
2Gb DDR800 RAM
nVidia GeForce 8800GTS (i think)
120 gig SATA hard drive

I've made the following partitions;
C: (windows) - 22 gigs
Swap: 2 gigs ( i know i'm supposed to make it double the ram size, but i think the system could handle it okay)
root partition: 2 gigs (EXT3) (mount point= '/')
Data partition - 87 gigs or something like that (EXT3 again) (mount point = 'media/sda6')

Booted with the live cd, everything goes well, did the manual set up of partitions during install, started the installation process..and it just closes when it comes to 82%..i read on the forums that was because i was connected to the internet, so tried again without being conncted to the internet..

Installation process continues normally through 82% which was a relief, but then it stops and dissapears again, this time at 94% (right when it says 'setting up grub' or 'configuring grub' or something like that) i've restarted to see if grub was installed, but it just boots into windows xp.

Could someone please suggest possible fixes? i'm frustrated now because i've had my laptop for about a month now and i still haven't been able to have it set up proper. :( 

P.S: i had another person install Gutsy (without problems) with the same cd on my laptop with no problems at all (he wasn't connected to the internet when it was being installed) so it makes sense my setup stopping at 82% but i can't figure what i'm doing is so different from what he did.

P.P.S: The cd is from the first week when the new distribution released, i'm not aware of any updates in the new version since then, or if the problem is because of that.

[-o< Help

---

### Post by Pumalite on 2007-11-18
Did youdo md5sum on iso, burn at 4x, check for integrity before install? Your brand new card might mean you have to install with the Alternate CD and install the new driver at the end of the installation.
[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

---

### Post by mushroomcloudwarrior on 2007-11-18
as i said, i've installed gutsy from the same cd on the same laptop before, but it crashed or some similar problem happened, which is why i am attempting to sort of clean everything up and re-do the whole thing.

---

### Post by Pumalite on 2007-11-18
'i've installed gutsy from the same cd on the same laptop before, but it crashed or some similar problem happened'
This is why I recommended downloading Alternate CD, doing md5sum on iso, burning at 4x in good CD-R media.

---

### Post by mushroomcloudwarrior on 2007-11-18
Well, problem solved.

Apparently, my root partition size was too small for some reason (while i thought and read on various pages that it was sufficient)

Increased the root partition size to 8 gigs and the installation ran smooth as a whistle.

I really appreciate your help though, thanks man..:KS

---

### Post by Pumalite on 2007-11-18
Glad you got it to work!

---

### Post by mushroomcloudwarrior on 2007-11-18
Thanks, 

although for some reason, the update manager does not seem to be working. I just set the repositories (selected all of them! i'm a very new linux user)

is this normal?
```
nikhil@nikhil-laptop:~$ sudo update-manager &
[1] 9253
nikhil@nikhil-laptop:~$ sudo: update-manager: command not found
```

---

### Post by Pumalite on 2007-11-18
I think you need to start a new thread (faster, better answers).

---

