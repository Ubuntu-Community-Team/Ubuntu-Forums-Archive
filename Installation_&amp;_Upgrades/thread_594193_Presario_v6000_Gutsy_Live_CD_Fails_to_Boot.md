---
title: "Presario v6000 Gutsy Live CD Fails to Boot"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Criminosis on 2007-10-27
Both Gutsy Main (Desktop) and Alternate cd have failed to install Gutsy on my laptop. 

I used (after hitting F6) the  "noapic irqpoll noirqdebug" flags as I used in Fiesty Fawn Live CD.

The Live CD gets to the Ubuntu Logo and then hangs after a few seconds, the bar freezes. Eventually it disappears and the black screen is all that's left.

After I took away "quiet" it hung "configuring X". (While typing this I did another one without quiet and it hung at```
 Setting Preliminary Keymap...

```
On the next attempt I also took off "Splash" it hung at (with only noapic flag) ```
squashfs : version 3.2-UBUNTU (2007/07/26) Phillip Lougher
``` or (with noapic irqpoll noirqdebug)  ```
[     49.839069]           ide0:  BM-DMA at 0x3080-0x3087,   BIOS settings:   hda:DMA,  hdb:pio
```  

The Alternate cd went further, but still failed. 

I burned two cd's, in case the first was bad. The text installer freezes at what seems to be random locations. I have had a couple freeze at the first screen (where you pick your language). I have had some freeze when it started installing (there was a moment of joy...then frozen at 3% :( ) The most frequent one however it when it gets to the "Scanning CD-ROM" window, I've had maybe 9 times there. 

If I don't use any of the flags (or just noapic by itself) no progress is gained.

I noticed the HP systems having issues thread, but I crossed my fingers for my Presario, there was a post about installing successfully, but just having sound issues. 

Any thoughts?

---

### Post by Criminosis on 2007-10-27
bump for hope

---

### Post by commonplace on 2007-10-27
Same laptop here, and my Gutsy is working fine. HOWEVER, this isn't a clean install; I upgraded from 7.04. But the upgrade went flawlessly and I've thrilled with 7.10.

I realise this doesn't help you much, but maybe knowing that it's somehow possible will help. :)

/Kevin

---

### Post by Criminosis on 2007-10-28
I was gonna do the update manager, but I borked a program...or something and I got the "your system isn't stable, do not reboot"....and I rebooted #-o so now I am back at this stage. Any other thoughts? I'm gonna rule out bad mirror tomorrow, seen some posts about that possibility.

---

### Post by Criminosis on 2007-10-28
The new Alternative CD failed, I'll try the live cd later...not much hope though. Anyone have similar experiences?

---

### Post by Criminosis on 2007-10-28
Nightly rebump for hope. :(

---

### Post by spiderbatdad on 2007-10-29
can't get the cd to install on an older HP ZE1110. My experience sounds similar to yours. It's frustrating. I've tried a dozen times, at least, to run the live cd installation, to no avail. Funny thing is I had a working version of kubuntu (maybe 6.04) on that computer once upon a time, but can't even get dapper toinstall on it now. Maybe a windows virus has rendered some hardware unworkable.

---

### Post by Criminosis on 2007-10-29
I'm kinda doubtful, anything that would have infected windows, you'd have to have run through WINE (and who would do that intentionally? :lolflag:) I may be wrong though. Still looking for some help though :(

---

### Post by Criminosis on 2007-10-29
Nightly bump

---

### Post by Criminosis on 2007-10-31
Nightly bump

---

### Post by Criminosis on 2007-11-01
Found little progress by adding the vga=nv, strike a thought to anyone?:confused:

---

### Post by Criminosis on 2007-11-02
ok, maybe the vga=nv didn't do anything....

---

### Post by spiderbatdad on 2007-11-05
I believe the answer to my problem on the HP ZE1110 is too little RAM. 248 usable. I'm going to give Xubuntu a go.

---

### Post by Criminosis on 2007-11-07
don't think that is my issue. I've got 1 GB under the hood.

---

### Post by buddah1620 on 2007-11-07
I tried loading ubuntu 7.10 on my main computer, it always freezes @ "kernel direct mapping tables up to 100000000 - 8000-d000".  

I ran the rescue cd and it said "Kernal panic - not syncing: IOAPIC + timer doesn't work!"

Whats the story guys?  has this bug been fixed?  I went looking through my BIOS and didn't see anything called APIC.  I had read in another post saying a guy couldn't use any USB devices with the APIC being unselected.  :(

---

### Post by Criminosis on 2007-11-09
rebump. using the Noapic flag shouldn't bother your USB usage, using that is what got 7.04 to work for me.

---

### Post by Pumalite on 2007-11-09
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))

---

### Post by Criminosis on 2007-11-11
Awesome! That got me into the installer and it is installing now...however what are the repercussions of using these flags? 

```
noapic nolapic noapci noirqpoll noirqdebug nosmp
```

such as disabled abilities, etc?

THANK YOU BY THE WAY :guitar:

---

### Post by Criminosis on 2007-11-11
Here is an interesting conflict.

I'm trying to install the nvidia-settings (attain control of my vga port if I need to hook up into a project for presentations, etc) package through synaptic. It is telling me I need to remove nvidia-glx-new.

Sudo apt-get instal nvidia-settings also yields the same result, except it recommends i install nvidia-glx-legacy. 

Is there a new tool out for the newer drivers? :confused:

Besides that, tip of the hat for having the drivers good to go, now I see why Gobuntu came out, having both of my restricted drivers in box was pretty surprising

---

### Post by Pumalite on 2007-11-11
Your card might need 'Legacy'. Check in the Nvidia site.

---

### Post by Criminosis on 2007-11-11
Checked the legacy listing, for my chip (Nvidia GeForce 6150 Go) and it wasn't listed, unless I was looking in the wrong list ([http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html))

---

### Post by Pumalite on 2007-11-12
The Legacy driver has to be compatible with your motherboard. It's not compatible with all.

---

