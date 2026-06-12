---
title: "Xubuntu on old computer- boot live-cd problems"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by chameleonkid on 2007-09-18
So my friend somehow erased IE from his computer and it no longer connects to the internet (or something like this). So I thought it would be a good idea to try and hook him up with some Xubuntu.
His computer is ancient, probably from '94-97 era, and is a gateway. It runs windows 98.

So I switch the Bios setup  boot order up, but when it goes to load the cd, it doesn't recognize it Instead it says Please insert Boot diskette in A: I see this and then turn off the floppy in the Bios. Still doesn't work, so I mess around with a bunch of different configurations. I give up. Then come back the next day with a Xubuntu cd burned at the slowest speed my poor burner can muster 10X (he has a dvd drive btw).

I have really no idea why it doesn't work. Maybe because I mistook the dvd drive for ATPI cd-rom drive in the Bios Setup screen? I could tell he was getting annoyed but I would appreciate any ideas on how to get this to work.

---

### Post by matthew.lns1 on 2007-09-18
Did you try the alternet install CD? Some times it will work when the desktop CD will not budge.

---

### Post by chameleonkid on 2007-09-18
> **matthew.lns1 said:**
> Did you try the alternet install CD? Some times it will work when the desktop CD will not budge.

No. And here's why: I wanted him to try it out before to see what he thinks and before he totally wipes his windows part. We both agree win98 is less than useful with more modern software but I don't know if he is willing to make the jump.

---

### Post by Gremlinzzz on 2007-09-18
'94-97 era, cant have much ram think you better reinstall win 98

---

### Post by Pumalite on 2007-09-18
Try a smaller distro: Zenwalk, DSL, Puppy.

---

### Post by voided3 on 2007-09-18
Get Puppy Linux!!! It runs great on computers even with only 64mb RAM and can run entirely in RAM w/ only 128mb of RAM (though I think the live CD only needs 64mb to work, give or take). Seriously, try it. I've used it on only old stuff and it is very straightforward (EASIEST NETWORKING SETUP WIZARD EVER) and makes the computer run stupidly fast, especially if it is at least 500mhz. I once ran it on a computer w/ a 200mhz Pentium and 72mb of RAM and it was still very usable. Seamonkey is the default browser and is very fast, and you still have Gaim and Abiword like you do on Xubuntu. Plus you can get iPods and flash drives to work with it unlike windows 98.....

As for Xubuntu, I think the live CD needs 128mb of RAM, so check to see how much he has and if it's SDRAM, you can probably get it up to at least 256mb for $10 or less if you hunt eBay for some DIMMs (I have a bunch of old systems that use SDRAM at home so I have quite a stockpile, i'm sure others do too). Either way though, XCFE is a heavier WM than ICEwm that Puppy runs. You always can do an Ubuntu server install w/o a GUI and customize it to make it super light, but I think something like Puppy might be the better choice for your friend. If it has less than 64mb of RAM and you can't upgrade, try DamnSmallLinux. I have used that as well and it is very light but a little less intuitive for a less experienced user, however it will power his system just fine I guarantee. DSL only needs 16mb of RAM to work, but from experience have at least 24-32mb. Good luck!

---

### Post by crjackson on 2007-09-18
> **voided3 said:**
> Get Puppy Linux!!! It runs great on computers even with only 64mb RAM and can run entirely in RAM w/ only 128mb of RAM (though I think the live CD only needs 64mb to work, give or take). Seriously, try it. I've used it on only old stuff and it is very straightforward (EASIEST NETWORKING SETUP WIZARD EVER) and makes the computer run stupidly fast, especially if it is at least 500mhz. I once ran it on a computer w/ a 200mhz Pentium and 72mb of RAM and it was still very usable. Seamonkey is the default browser and is very fast, and you still have Gaim and Abiword like you do on Xubuntu. Plus you can get iPods and flash drives to work with it unlike windows 98.....

As for Xubuntu, I think the live CD needs 128mb of RAM, so check to see how much he has and if it's SDRAM, you can probably get it up to at least 256mb for $10 or less if you hunt eBay for some DIMMs (I have a bunch of old systems that use SDRAM at home so I have quite a stockpile, i'm sure others do too). Either way though, XCFE is a heavier WM than ICEwm that Puppy runs. You always can do an Ubuntu server install w/o a GUI and customize it to make it super light, but I think something like Puppy might be the better choice for your friend. If it has less than 64mb of RAM and you can't upgrade, try DamnSmallLinux. I have used that as well and it is very light but a little less intuitive for a less experienced user, however it will power his system just fine I guarantee. DSL only needs 16mb of RAM to work, but from experience have at least 24-32mb. Good luck!

Just wondering, can you still use gnome / kde apps. running under puppy w/ICE?

---

### Post by chameleonkid on 2007-09-18
> **voided3 said:**
> Get Puppy Linux!!! It runs great on computers even with only 64mb RAM and can run entirely in RAM w/ only 128mb of RAM (though I think the live CD only needs 64mb to work, give or take). Seriously, try it. I've used it on only old stuff and it is very straightforward (EASIEST NETWORKING SETUP WIZARD EVER) and makes the computer run stupidly fast, especially if it is at least 500mhz. I once ran it on a computer w/ a 200mhz Pentium and 72mb of RAM and it was still very usable. Seamonkey is the default browser and is very fast, and you still have Gaim and Abiword like you do on Xubuntu. Plus you can get iPods and flash drives to work with it unlike windows 98.....

As for Xubuntu, I think the live CD needs 128mb of RAM, so check to see how much he has and if it's SDRAM, you can probably get it up to at least 256mb for $10 or less if you hunt eBay for some DIMMs (I have a bunch of old systems that use SDRAM at home so I have quite a stockpile, i'm sure others do too). Either way though, XCFE is a heavier WM than ICEwm that Puppy runs. You always can do an Ubuntu server install w/o a GUI and customize it to make it super light, but I think something like Puppy might be the better choice for your friend. If it has less than 64mb of RAM and you can't upgrade, try DamnSmallLinux. I have used that as well and it is very light but a little less intuitive for a less experienced user, however it will power his system just fine I guarantee. DSL only needs 16mb of RAM to work, but from experience have at least 24-32mb. Good luck!

I'll give puppy linux a shot. 

Although I have a feeling it still won't be able to boot. As any live cd should be able to run regardless of how much memory a computer has, correct? I think the problem lies in the hardware, or something of that nature. Oh well. Thanks all

---

### Post by chameleonkid on 2007-09-18
I think I found the answer accidentally *coughGooglecough*. For future Reference: Old computers can only boot from floppies. In steps Smart Boot Manager, and it acts as an intermediary between the Bios and the Cd. Let's hope this works!

[http://ubuntuforums.org/showthread.php?p=2464982]("http://ubuntuforums.org/showthread.php?p=2464982")

---

### Post by kerry_s on 2007-09-19
> **chameleonkid said:**
> I'll give puppy linux a shot. 

Although I have a feeling it still won't be able to boot. As any live cd should be able to run regardless of how much memory a computer has, correct? I think the problem lies in the hardware, or something of that nature. Oh well. Thanks all

your wrong about the ram, a live cd uses ram to store the cd info, so you need a minumum to work, in the case of xubuntu you need 128ram to use the livecd and 192ram to use the installer.

---

### Post by voided3 on 2007-09-19
I forgot to mention SBM. I had to use that on an old Compaq from '96 that was only floppy-bootable. Great little tool for the old ones and it should get you up and running!

---

### Post by Puistokemisti on 2007-09-19
I have also a problem with xubuntu live-cd. Before I go on I want to point out that I'm a total n00b with this linux thing.

I tried to run xubuntu live on my "old warhorse" and everything worked pretty nicely until this light blue background color and mouse cursor appeared. It seems to be unable to get on from that point. Toolbars never appear. It's not totally frozen as I managed to get into some kind of command prompt by  pressing "ctrl-alt-f1"*.

*I saw this combination mentioned in one of the forum discussions  and thought it might  do something


System specs are:
amd-k6/2 500MHz, 128Mb ram, Tseng labs ET6000/6100 video card.

Now I assume that 128Mb of memory should be enough to at least run this live-cd even if installing wasn't possible. Could the problem be that old junk video card(it gets the job done though) which I just put in when my riva tnt2/m64(not that magnificent either) died?

---

### Post by voided3 on 2007-09-20
> I tried to run xubuntu live on my "old warhorse" and everything worked pretty nicely until this light blue background color and mouse cursor appeared. It seems to be unable to get on from that point. Toolbars never appear. It's not totally frozen as I managed to get into some kind of command prompt by pressing "ctrl-alt-f1"*.


I had this happen to me too on a computer with a small amount of RAM. You can either try to get 64mb additional (or more) of RAM, or hit Alt+F2 when you get to the blank desktop w/ the cursor and type in "xfce4-panel" and  hit enter. That should manually launch the panel so you can try out stuff. Good luck!

---

### Post by maybeway36 on 2007-09-20
It's a good idea to install a minimalist window manager if even Xfce is too slow. Try fluxbox, blackbox or openbox. Also install the "menu" package.

---

### Post by Pumalite on 2007-09-20
DSL or Puppy will do it. They are incredibly fast. Including Zenwalk.

---

### Post by wingrider101 on 2007-09-20
> **voided3 said:**
> Get Puppy Linux!!! It runs great on computers even with only 64mb RAM and can run entirely in RAM w/ only 128mb of RAM (though I think the live CD only needs 64mb to work, give or take). Seriously, try it. I've used it on only old stuff and it is very straightforward (EASIEST NETWORKING SETUP WIZARD EVER) and makes the computer run stupidly fast, especially if it is at least 500mhz. I once ran it on a computer w/ a 200mhz Pentium and 72mb of RAM and it was still very usable. Seamonkey is the default browser and is very fast, and you still have Gaim and Abiword like you do on Xubuntu. Plus you can get iPods and flash drives to work with it unlike windows 98.....

As for Xubuntu, I think the live CD needs 128mb of RAM, so check to see how much he has and if it's SDRAM, you can probably get it up to at least 256mb for $10 or less if you hunt eBay for some DIMMs (I have a bunch of old systems that use SDRAM at home so I have quite a stockpile, i'm sure others do too). Either way though, XCFE is a heavier WM than ICEwm that Puppy runs. You always can do an Ubuntu server install w/o a GUI and customize it to make it super light, but I think something like Puppy might be the better choice for your friend. If it has less than 64mb of RAM and you can't upgrade, try DamnSmallLinux. I have used that as well and it is very light but a little less intuitive for a less experienced user, however it will power his system just fine I guarantee. DSL only needs 16mb of RAM to work, but from experience have at least 24-32mb. Good luck!

Be careful with Puppy... Hardware support for Wireless cards (especially low end like TrendNet, D-Link etc.) is very poor.  Worked on a Trendnet card for weeks and never got it working even with NDIS Wrapper!  Also, it didn't understand the oldest Intel chip set around 8255 Intel Pro 100!  EVERYONE understands this card... it's the great granddaddy of all Intel products!

BAM

---

