---
title: "Can't install any version of Ubuntu"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by vapotrini on 2008-04-29
Hi guys. Lately I've been wanting to install Linux on my machine but I'm not having any luck whatsoever. I first tried to install Ubuntu 8.04 via the Live CD but it didn't work. It reaches to an Orange screen then stops doing anything. I waited for over 30 mins but nothing else happened. I then tried to do it from within windows, that didn't work either - same result. I then downloaded and tried the alternate version of the CD and it reaches the same exact place as before and then stops. To me it looks almost to be a video card driver problem, where it's not displaying what it should but who knows.

I then tried downloading and installing Ubuntu 7.1. Where the same thing is happening except it hangs on a black screen now. Just like with 8.04 is goes past the splash screen then about 10 seconds in, it reaches a screen and everything stops (IE: Disc activity, no mouse to be found, etc). I'm really at a lost and don't know what else to try. I've gone through my bios and set it to have floppy drive off as I don't have one (as I've read that causes problems). I also checked everything else while in there too but I can't seem to find anything wrong.

Can someone please shed some light on what I can do to get Linux on my machine?

Here's a little video of me trying to get 8.04 on my machine. You can see where it reaches the Orange screen and stops. [http://files.filefront.com/ubuntump4/;10099278;/fileinfo.html](http://files.filefront.com/ubuntump4/;10099278;/fileinfo.html)

System Specs:
Amd 64 3000
1 Gig Ram
Geforce 7800 GT

---

### Post by jimmyd850 on 2008-04-29
The exact same problem is happening to me. I too would be very interested in finding a solution as I am desparate do give Ubuntu a try!

---

### Post by kerry_s on 2008-04-29
sounds like bad burns. with a iso you want to burn slow, 4x will give the best results. a bad cd leads to a bad install, use the check cd option to verify the cd is good when you boot it.

---

### Post by vapotrini on 2008-04-29
It wasn't a bad burn I don't think, I burnt it at 4x and used the check cd integrity option. No problems were found.

---

### Post by jimmyd850 on 2008-04-29
same here i've burnt the cd at 4X and verfied it.

---

### Post by spudratic on 2008-04-29
did you guys do a check sum(md5sum) before you burnt the cd.I made this mistake before by not checking the iso from a torrent before I burned it

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by jimmyd850 on 2008-04-29
Not sure why things are starting to work but I've got the graphical installer going.

I had used the windows install option.

Then when it rebooted I pressed esc to get some boot options and I added the following to the 2nd option "acpi workaround"(?)

pci=noacpi ide=nodma ide=reverse

which I read on another post helped someone else. I understand the no dma option but not the others and why that would help. Currently it is installing and is about 57% of the way through. I am hoping that I just haven't wiped XP or my other files!

Any explaination would help me understand what I've just done!

---

### Post by vapotrini on 2008-04-29
Spudratic, thanks for the link, I checked and it says mine are the same. So it's not a CD problem.

Sad to say but from browsing the forums it seems to me that there are **tons** of people out there experiencing some sort of install problem with Ubuntu... I think the developers need to really take a hard look at this. It's **never** going to grow in popularity if simply installing it is a headache. I'm not giving up though, it's a personal thing now...

Jimmy, gonna give that a try also. Thanks!

---

### Post by adrk on 2008-04-29
It happened to me also .Please give us an expert advice

---

### Post by bullfrog2 on 2008-04-29
try a fresh install bet it works did for me  hope it does bullfrog2

---

### Post by vapotrini on 2008-04-30
Well, it was like I first guessed... vga driver problem (kinda). Seems that it was there all along and that orange screen I was talking about is the main window, however since I'm on a 24 inch monitor with a standard 1920 x 1200 resolution I could only see the top left corner. By chance I plugged in smaller monitor and there it was. 

Thanks to all who tried to help... I appreciate it!

Trying to get the right nvidia drivers to install now, Envy doesn't seem to like me.

---

