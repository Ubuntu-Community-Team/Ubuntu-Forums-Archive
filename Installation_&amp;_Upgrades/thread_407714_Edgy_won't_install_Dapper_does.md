---
title: "Edgy won't install Dapper does"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by Panhead Bill on 2007-04-12
While trying to build a second mythtv box, I ran into a strange (to me anyway) problem.

Edgy doesn't install or work "live" properly on my "Test Mule" PC, but Dapper does.

All disks have passed the error check prior to install. 

 Edgy alternate text install sorta works but trying to play a mpg file with mplayer errors out and scrambles the keyboard responses. 

Edgy live seemed to load, but the logon screen was "horizontally shreaded" giving three partial images at screen left center and front.

Edgy install from live disk ended with "brown" screen without rest of desktop.

Edgy alternate oem install worked up to the point of logging in as oem, then entered an endless loop - where the desktop starts to load through nautilus, then the screen flashes black then back to logon screen.

Any ideas why this is happening?  Ultimately I want to have all my linux boxes running the same version, and hopefully the latest one.

Anyone have any ideas?

Details of the "Test Mule" PC are in the signature line below.

---

### Post by solar george on 2007-04-12
Have you tried installing dapper and updating?

---

### Post by zvacet on 2007-04-12
Go for solar george advice.Install Dapper  and upgrade it with Edgy alternate CD with command
```
gksu "sh /cdrom/cdromupgrade" 
```

---

### Post by Panhead Bill on 2007-04-13
I'll try that, and report back.

  I'm concerned that I don't know if the problem is the software or the hardware, nor how to determine it.  Eventially I'll want to install feisty, and I hope to not repeat the multiple installs.  Time will tell.

Thanks

---

### Post by majoridiot on 2007-04-13
what speed are you burning the CDs at?  i suggest trying 4x if you haven't.

---

### Post by Panhead Bill on 2007-04-14
I use the lowest speed that my burner and nero supports, my lowest speed is 8x.  The thing is that ALL of my linux disks are burned at 8x.

---

### Post by Panhead Bill on 2007-04-17
Same result for Dapper to Edgy alternate update via disk;

   Edgy starts to load, initial Edgy Ubuntu logo appears for several seconds but then the ubuntu image is "horizontally shreaded" giving two partial images (in green and purple) on screen left and right instead of one image in center.  

Next the screen gives the brown background for 2-3 seconds then flashes to a white screen for half a second then repeats the brown / white sequence over and over till hard reset.

Any thoughts?

---

### Post by Panhead Bill on 2007-04-20
The story so far;  My "test mule" PC has problems with edgy.

All disks were md5sum checked, burned at the same slowest speed, on the same pc-burner-disk-burner program.  All disks passed their error check prior to install or live loading.

"Test mule" pc info in signature - below.

Dapper live - works
Dapper desktop - works
Edgy live - does not work
Edgy Desktop - does not work
Edgy server - does not work
Feisty live - works
Feisty desktop - works
Feisty server not tried yet

---

### Post by majoridiot on 2007-04-20
> **Panhead Bill said:**
> Feisty live - works
Feisty desktop - works
Feisty server not tried yet

seems the ubuntu gods are telling you feisty is the way to go ;)

looks like there are obvious hardware issues with edgy that were (at least partially) resolved in feisty.

if you want to go the edgy route instead of feisty, your best bet is to find the most "stable" install you can do and
then start checking the system logs, dmesg, lspci, etc. to see where the harware faults are and if there is a 
possibility of updating the drivers that are failing.

i had one edgy driver issue (forcedeth) that was resolved with the inclusion of a newer version in the feisty distro.

---

### Post by Panhead Bill on 2007-04-21
Since this seems to be a software issue, I'd be surprised if I am the only one that runs into it.
 I plan on running feisty in the pc's, but I would like to find out what went "kittywhumpus" in edgy.
I'll try to investigate as you suggest, with what (little) know how I've accumulated so far.

PB

---

### Post by majoridiot on 2007-04-21
> **Panhead Bill said:**
> Since this seems to be a software issue, I'd be surprised if I am the only one that runs into it.
 I plan on running feisty in the pc's, but I would like to find out what went "kittywhumpus" in edgy.
I'll try to investigate as you suggest, with what (little) know how I've accumulated so far.

PB

i suggest going back and taking a look at the changelogs between dapper and feisty, then... to see if you can suss
what went wrong from dapper to edgy that was fixed between edgy and feisty.

the situation is not unheard of, tho... especially with an ever-evolving kernel.

---

