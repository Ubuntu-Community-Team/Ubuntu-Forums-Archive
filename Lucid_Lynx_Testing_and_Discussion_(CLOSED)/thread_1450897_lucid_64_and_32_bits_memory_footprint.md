---
title: "lucid 64 and 32 bits memory footprint"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by camaron1 on 2010-04-09
I've been testing Lucid 62 and 32 bits to eventually decide which to install. The 32 bits version starts off with about 200 MB of RAM (or even less) which I find very impressive. The 64 bits version starts with about 900 MB. I was expecting a significant increase but this about 5 times as much. I wonder what are your thoughts (or experience) on this.

---

### Post by TheGreatBunghole on 2010-04-09
I just recently installed 10.04 Beta 2, (i386)... & it uses around 400 MB!!  when I use 9.10 (i386), it uses only around 150 MB ram... I wonder why it is using so much more RAM than Karmic?!

Personally, I see no advantage in performance from using the 64-bit version over the 32-bit version, so if you have less than 3.7 -4 GB or whatever the limit of Swap & RAM is, then I say stick with the 32-bit version :)

---

### Post by ajgreeny on 2010-04-09
> **TheGreatBunghole said:**
> I just recently installed 10.04 Beta 2, (i386)... & it uses around 400 MB!! [COLOR=Red] when I use 9.10 (i386), it uses only around 150 MB ram[/COLOR]... I wonder why it is using so much more RAM than Karmic?!

Personally, I see no advantage in performance from using the 64-bit version over the 32-bit version, so if you have less than 3.7 -4 GB or whatever the limit of Swap & RAM is, then I say stick with the 32-bit version :)
Really; only 150MB ram used in karmic?  How on earth do you manage that?  I would love to know, as my system running nothing except the startup programs, and I've stopped several of those that usually run, uses about 230MB without compiz and 250 with compiz.

Perhaps you are using another desktop than gnome, but if not, then I think you are either very lucky, or your skill at configuring the machine to run very little in the way of processes is a great deal better than mine.

---

### Post by TheGreatBunghole on 2010-04-09
I think I am just lucky, or maybe it has something to do with my strange setup... I have an Acer Aspire 5100 that is messed up in more ways than I can count. Maybe it has something to do with the extra drivers that I had to install that were proprietary? I am not quite sure why it runs only with 150, but Karmic also runs with the same RAM usage on a VERY old HP Pavilion desktop with only 384 MB RAM. But I am really not sure why Lucid is using sooo much ram on my laptop. I only have 874 MB ram after the graphics card uses 128 MB of my ram... so right now I am not liking my performance on Lucid very much. I just figured I would help out the community by installing it and reporting bugs with my excessive use  :)

---

### Post by -humanaut- on 2010-04-09
Im using the 64bit Lucid ISO if compiz is turn off it seems to only use around 300-350mb of Ram compiz adds an extra 100mb's or so. Pretty typical of Gnome regardless of arch for me.

---

### Post by howefield on 2010-04-09
> **camaron1 said:**
> I wonder what are your thoughts (or experience) on this.

Sounds like a problem with your setup in some way.

My experience with Lucid 32 bit is around 275 megabytes at startup, and 375 megabytes for 64 bit.  

It is usually the same for me going back a few releases, always approximately 100 meg difference.

---

### Post by -humanaut- on 2010-04-09
One major difference I did note though was Lucid Xubuntu 32bit I had that down to a nimble 105-110mb but the 64bit Xubuntu ran at no less then 280Mb and I'd compare that even to Debian Squeeze 64Bit Xfce was running at 90-100mb

---

### Post by TheGreatBunghole on 2010-04-10
wow there must be something wrong (or just different) with the way this next release is going... I hope more will be done to check out this issue.

---

### Post by WinterRain on 2010-04-10
I'm using 1.2gb ram with 2 browsers, transmission and vlc running. RAM is there to be used, not conserved. As long as you have enough memory, I wouldn't worry about it.

---

### Post by camaron1 on 2010-04-10
> I just recently installed 10.04 Beta 2, (i386)... & it uses around  400 MB!!  when I use 9.10 (i386), it uses only around 150 MB ram... I  wonder why it is using so much more RAM than Karmic?!Karmic uses about 50percent more memory than Lucid in my experience

> Im using the 64bit Lucid ISO if compiz is turn off it seems to only use  around 300-350mb of Ram compiz adds an extra 100mb's or so. Pretty  typical of Gnome regardless of arch for me.     I would've expected something on those lines, but that seems to indicated that my computer for some reason (but it is quad core) struggles with 64

> My experience with Lucid 32 bit is around 275 megabytes at startup, and  375 megabytes for 64 bit.  

It is usually the same for me going back a few releases, always  approximately 100 meg difference.Confirming the above said.

Well it seems that unless the **release candidate **changes matters i'll stick to 32 bits:)

---

### Post by cariboo on 2010-04-10
+1, Even Windows 7 and Vista try to use ram the same way Linux does, unused ram is useless, it just sits there and does nothing. Programs cached in ram load faster. Let the system manage ram and don't worry about it.

---

### Post by TheGreatBunghole on 2010-04-10
the only reason why I worry about it, is because my performance has taken a huge hit. I have to wait a long time for some of my RAM to be freed-up and put onto my swap partition... I almost never needed Swap in Karmic. I only have 1 GB ram, & 10.04 takes a significant chunk out of that in comparison to 9.10. That is why I am concerned. ( & yes, a hardware upgrade would be a smart thing at this point. )

---

### Post by Longinus00 on 2010-04-10
64bit will always take more memory than 32bit. The benefit to us, in the x86 case anyway, is all the extra features they added in to make computing faster/safer. ([http://en.wikipedia.org/wiki/X64#Architectural_features](http://en.wikipedia.org/wiki/X64#Architectural_features)) That being said, if 64bit is taking up more than 2x the amount of memory as your 32bit install, there is likely something is wrong with your system.

---

### Post by Reiger on 2010-04-10
On my currently running Lucid, Kubuntu 64bit installation I use 1.3GB which is fairly typical usage. I've got about 32MB in use out of 2.8GB swap also. I do have a lot of effects turned on (including multiple desktops). When I have Netbeans running I'll see the system driven to swap fairly quickly; it'll consume another 800MB of memory or so. :P 

Notes: (a) I have Opera 10.10 running with the usual generous amount of tabs. So that is 0.3GB right there.
(b) I have Nepomuk/Virtuoso configured to use 250MB of memory for faster performance, rather than the default 50MB. And indeed the various processes do consume about that in memory right now.

---

