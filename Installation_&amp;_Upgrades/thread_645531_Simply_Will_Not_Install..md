---
title: "Simply Will Not Install."
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by messageman3@hotmail.com on 2007-12-20
Hi guys, i am trying to install linux for the first time, and so i have chosen ubuntu!

i have downloaded:
[LIST]
[*]7.10 install iso
[*]7.04 install iso
[*]7.04 alternative iso
[/LIST]

and none of these work.

all of the md5's are fine

i run the cd at boot, check the cd, and there are a load of files missing eg. nvidia ones! :S

i am running vista, and have tried to do the image from hdd install method, but cannot seem to get this to work: error at boot = 
file: \grldr
status: 0xc0000007b
info: the selected entry could not be loaded because the application is missing or corrupt.

i get the same message if i try to install with unetbootin.

help please?

thanks,
--messageman3--

---

### Post by DrMega on 2007-12-20
Many of the drivers are downloaded after you install. This would include the proprietary nVidia drivers.

When you boot from the CD, if you ignore the Check CD option and choose 'Start or Install Ubuntu' (or whatever the exact wording is), does it boot into Ubuntu?

If it does, then just do that, then on the desktop there is an 'Install' icon, just launch that and off it goes (the install wizard is all very intuitive and self explanatory).

I've installed Ubnuntu several times on several machines, but I've never bother running the disk check.

---

### Post by messageman3@hotmail.com on 2007-12-20
no, it does not boot into ubuntu at all, just comes up with error after error, and finally sits sulking untill i turn it off and then on again....

i have only run the disk check in order to see if it is the disk....

i do not have an nVidia card, that is what is confusing me most!

:S

--messageman3--

---

### Post by Partyboi2 on 2007-12-20
> **messageman3@hotmail.com said:**
> no, it does not boot into ubuntu at all, just comes up with error after error, and finally sits sulking untill i turn it off and then on again....

i have only run the disk check in order to see if it is the disk....

i do not have an nVidia card, that is what is confusing me most!

:S

--messageman3--

Can you post the errors you are getting, that way someone might be able to point you in the right direction.

Edit: Sorry I didn't read all of your first post, you have already posted the error. :oops:

---

### Post by messageman3@hotmail.com on 2007-12-20
(i am generating these from virtualpc - they are the same errors as i would usually get)
(these only occur when reading from the actual cd - when running from the iso, it works perfectly)
the first two errors i get, just after telling it to "start" are:

"[    29.358297] isapnp: checksum for device 1 is not valid (0x89)"
"[    29.366949] isapnp: checksum for device 2 is not valid (0xbe)"

i think that perhaps the way ahead is for me to use the image on hdd method...

---

### Post by Partyboi2 on 2007-12-20
> **messageman3@hotmail.com said:**
> (i am generating these from virtualpc - they are the same errors as i would usually get)
(these only occur when reading from the actual cd - when running from the iso, it works perfectly)
the first two errors i get, just after telling it to "start" are:

"[    29.358297] isapnp: checksum for device 1 is not valid (0x89)"
"[    29.366949] isapnp: checksum for device 2 is not valid (0xbe)"

i think that perhaps the way ahead is for me to use the image on hdd method...
I am not sure if this will help, or atleast give you some ideas. One guy suggest reducing the amount of ram for the install.
[http://ubuntuforums.org/showthread.php?t=1556](http://ubuntuforums.org/showthread.php?t=1556)

---

### Post by messageman3@hotmail.com on 2007-12-20
i was just looking at that, myself!

it is not virtualpc that i am having the problem with however, it is the actual installation to my system that is causing the problem! :S

i will keep looking, but anyone else who reads this, please help!!

thanks,

--messageman3--

---

