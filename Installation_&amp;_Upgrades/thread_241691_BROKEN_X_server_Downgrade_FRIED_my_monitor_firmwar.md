---
title: "BROKEN X server: Downgrade FRIED my monitor firmware!"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by anasofiapaixao on 2006-08-22
**EDIT 2:** This behaviour apparently is triggered whenever I alter my xorg.conf - Upon reboot, farewell screen... I know this may sound strange, but the fact is that it *is* happenning and is rendering my laptop unusable... Now I need to be fearful everytime I turn it on whether it will work or not? This is crazy... Oh, and I don't have an external monitor available at home. Nice ](*,)

**EDIT: **I guess I found the cause. My screen firmware was set to start on external monitor by default. After the whole connecting-to.TV thing, it stopped working again after reboot - but plugging an external monitor like Fatjoint said and resetting the BIOS to the defaults (I didn't have an option to choose the monitor tough) did the trick. BEWARE! The X server downgrade *messed up* my firmware settings! This is scary...

Sorry for double posting, but right after posting this in Video & Sound I realized this is where the whole broken X issue heat is, and after all it is thanks to this that my problem happenned. Also, I am really really worried, in YEARS of dealing with computers never such a thing happened to me!

I am in total desperation. My screen just doesn't work anymore, I can't see a thing, I can't see toshiba's logo, I can't see NOTHING! All of this happened after I tried to downgrade the X server core, and some way this just FRIED MY FIRMWARE! Also I can't try anything because I can't SEE what I'm doing, I can't run a LiveCD because the screen goes black from the moment I turn it on! This is just more serious than any problem I have had before... PLEASE, HELP!

EDIT: Some further info, now that I calmed down a little bit (I am still completely nervous)... my screen is totally DEAD. Dead really dead, even the backlights won't turn on. This happened on the very moment I pressed enter after typing the command "startx". I did not get alarmed, I powered off the computer, and restarted. And still the monitor was dead. The toshiba logo didn't appear. Nothing actually would appear...

I have an nVIDIA graphics card, and am running a 1900€ Toshiba Tecra M4 Laptop that will cost my guts to get fixed if I need to go to Toshiba support, and for the moment it will be hard to paste here any further configuration info. As I am totally incapable of acessing my computer.

My sound is working and apparently the rest of the system; I can hear the GDM sound and the login jingle if I enter my login info (TOTALLY blindly).This did happen immediately after the downgrade, so it can't be anything else!

---

### Post by anasofiapaixao on 2006-08-22
My screen is not dead after all. It is more like undead. I realised that, if I pressed Fn+F5 (switch from internal monitor to external monitor) I could see the splash, but that ends on the moment x starts. Killing X or Fn-F5'ing again won't work.

Still no toshiba logo as, of course, the combintion only works once the Fn-whatever driver is loaded. My guess is that somehow my screen was set to start external by default...

Edit: I can successfully start an X session from the LiveCD (I still wonder how in the world did I manage to choose the CD option in the Toshiba boot menu in a BLACK screen), so the possible solution is reinstalling the nvidia drivers like it was said on the Update fiasco thread; but anyway how can I stop my screen firmware to go try to 'eat outside' by default?

---

### Post by Fatjoint on 2006-08-22
Linux cannot fry LCD monitors i.e. laptop screens - impossible - they don't work the same way that a CRT does.

It is possible if you manually change CRT monitor files outside of your CRTs capability to blow a screen, but I haven't seen or heard of a case since like 1995.

I think that you've found the crux of your issue being that your laptop is starting up in external video.  Check your bios and make sure that your default mode is internal.  Plug a monitor into your laptop to help you get inside the bios and check your settings.

---

### Post by anasofiapaixao on 2006-08-22
**EDIT:** OH MY GOD. I must be crazy; there is no other explanation. I plugged a TV cable, rebooted from the liveCD session I was running and guess what - The monitor started just fine, the X session also started just fine! It must be my head, right?


Lol, 'fry' was a manner of speech... Funny enough I read your post right after writing that 'my guess was it was on external by default' :D. Many thanks for the quick answer, I'll try that... anyway, how could the x server downgrade change my FIRMWARE settings? It did though... :S

P.S. - Making a monitor explode... Many of my physics classmates would surely *love* to try that out...

---

### Post by Fatjoint on 2006-08-22
> **anasofiapaixao said:**
> Lol, 'fry' was a manner of speech... Funny enough I read your post right after writing that 'my guess was it was on external by default' :D. Many thanks for the quick answer, I'll try that... anyway, how could the x server downgrade change my FIRMWARE settings? It did though... :S

P.S. - Making a monitor explode... Many of my physics classmates would surely *love* to try that out...

That makes two of us then, because what I mean by 'blow' isn't literally flying glass but more like a whine, whimper, and then blank screen.  The flyback transformer cannot handle the frequency asked of it and consequently becomes a molten core.  Not very exciting and certainly something I wouldn't try to do purposely because of the fire and subsequent eletrocution hazard in attempting to extinguish.

CRT monitors contain high voltages/amperages and they can kill you flat out.

---

### Post by anasofiapaixao on 2006-08-22
Cathode rays can be nasty... I had no ideia that the current intensity could be high enough to kill a human!

---

### Post by anasofiapaixao on 2006-08-24
It is constantly stopping to work. Now I can't even see the screen with the Fn-F5 trick, nor can I login. Thanks to this update mess, I have now the 1900&#8364; equivalent of a bunch of trash.
Sorry for the harsh language, but my computer is now completely unusable because of all this.

---

### Post by tseliot on 2006-08-24
First of all I understand your frustration but please calm down.

That package can't flash the firmware of your laptop.

1) can you access the BIOS as soon as you boot?

If not:
Plug in the tv cable, turn on your TV and your computer. You should be able to access the BIOS, right?

See if you can change the output of the graphic card (internal, external, or somthing like that).

2) If the BIOS does not provide any useful detail you can:
Boot in Recovery Mode (you can use the TV to see what you're doing)
type:
```
dpkg-reconfigure -phigh xserver-xorg
```

then:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver

select the Monitor and refresh rate as well.

then exit and reboot (by typing "reboot")

---

### Post by anasofiapaixao on 2006-08-24
Putting things in a chronological order, because the results have been disastrous at each attempt to do it any other way:

**1. **I was unfortuante enough to catch the X update fiasco. My X stopped working. After doing a scan on PCI addresses, re-checking xorg.conf and realizing the only thing I did was to update, I just decided to wait. This in the morning.

**2. **I go to the forums at night. By the time the 10.4 release hadn't been uploaded yet, so the instructions there told us to downgrade, grabbing a deb from an unofficial source. I did it. I started X. All would be well if it wasn't for the totally black screen. I rebooted.

**3. **What was my surprise when I saw that my screen was DEAD. I wasn't able to see anything prior (or even after) to loading the OS; the screen was plain simply turned off.

**4. **"[I]My sound is working and apparently the rest of the system; I can hear the GDM sound and the login jingle if I enter my login info (TOTALLY blindly).This did happen immediately after the downgrade, so it can't be anything else!
(...)
I realised that, if I pressed Fn+F5 (switch from internal monitor to external monitor) I could see the splash, but that ends on the moment x starts. Killing X or Fn-F5'ing again won't work.
Still no toshiba logo as, of course, the combintion only works once the Fn-whatever driver is loaded. My guess is that somehow my screen was set to start external by default...[/I]"

**5. **So I decided to plug the TV. I couldn't see anything in it (in the middle of all Fn-F5'ing the maximum I wold get would be gibberish), but the screen simply started to work again - I got Toshiba's logo back. This until the next restart. I can't recall what I did of relevant meanwhile; I just remember hearing internet radio with the laptop running on battery until I fell asleep, and only woke up next day.

**6. **Next day (Aug-23)... it stopped working again. Same symptoms as before. I went to a friend's place, plugged an external monitor, accessed the BIOS. It did not provide anything of useful (okay it sucked), except for "Home - Reset defaults". I did it, saved and exited. It started working again, sevral restarts were made for what I remember.

**7. **I decided to try to configure TV-OUT following [your guide]("http://www.ubuntuforums.org/showthread.php?t=98456&highlight=tv-out+newbies"). Upon editing - I am not sure if there was a reboot in the meanwhile, but I guess not - xorg.conf and rebooting, it stopped working again. In the middle of all this mess there was a time when the TV was more or less working, meaning I could see cleanly on it what I coud see on the external screen - the splash only though (I actually had to disable the splash due to an NVIDIA driver bug, but I mean the text output replacing it).

**7.b. **Through Fn-F5'ing and then introducing login info blindly, X would start and I could see it - but I noticed I was starting screen 2 in my monitor. All the time when I was able to check xorg logs, I would find out it would say that Screen[1] doesn't exist. I couldn't get the mouse pointer on the loaded screen except when using the stylus.

**8. **For some very stupid reason (something about finding where to reset the bios) I took off the RAM and the keyboard, to peak inside. Kept looking at that for a considerable time. Saw something on a board with the name "RESET", but next to were just two little metal dots. Re-assembled the stuff back.

**9. **Abracadabra... It started working! I don't know how or why, but it started working again! Then I thought: Does this have anything to do with being plugged to electricity? So, while it was still booting I turned it off, unplugged the AC cable, turned it on. Didn't work. Turned off, plugged the cable. STILL didn't work.

**10.** This brings us to today. If we can define "intuition" what makes us do weird things with no logical support whatsoever, then it was by intuition that I removed the ram, the keyboard, touched those little RESET metal dots, removed the HDD and plugged this all back. I tried for the sake of I don't-know-what to turn the PC on without the RAM to see what happened, but oh little detail, remember you don't have a funcioning screen? So I did see nothing.

**11.** News! No it didn't start to work, but actually I can't even blindly login again! I suspect this had something to do with me taking the disk off, but come on, I have done it before and how many ways are there of incorrectly plugging back a disk!? So now I have to get the pc plugged to an external monitor again and check there what the hell is going on...


**APPENDIX:**
I will use the CRT in my mum's office, and as that computer still has a mined XP SP1 (it was a clean install, can't even be connected to the net or it will freeze; hasn't been used ever since mostly out of laziness as that computer was mine and I got a laptop) I was thinking of installing Ubuntu on it. Tried to burn a DVD-RW on my mum's laptop with the 6.06.1 ISO which has 6.06 already burned. Burning pure and simply *doesn't work*. Guess what I have in my mum's PC??? Yeah, Ubuntu.

PLUS I have just broken the compiz install on her laptop. I had problems with compiz on mine, but as I had apt-get installed and removed various compiz-related packages in order to try to make it work again after update I tought, okay my problem. Forum people told me later that they simply updated and compiz was running fine, so the repos problem had been fixed. I did that on my untouched mum's laptop. I broke her compiz.
DISCLAIMER: I know that it is the non-ubuntu repos (Beerorkid, etc) that are broken.

See why am I so mad? All of this started with the update fiasco and now I just have my nerves blown off...

---

### Post by tseliot on 2006-08-24
> **anasofiapaixao said:**
> **8. **For some very stupid reason (something about finding where to reset the bios) I took off the RAM and the keyboard, to peak inside. Kept looking at that for a considerable time. Saw something on a board with the name "RESET", but next to were just two little metal dots. Re-assembled the stuff back.

**9. **Abracadabra... It started working! I don't know how or why, but it started working again! Then I thought: Does this have anything to do with being plugged to electricity? So, while it was still booting I turned it off, unplugged the AC cable, turned it on. Didn't work. Turned off, plugged the cable. STILL didn't work.
It might be your (falty) hardware. My laptop lost the cdreader 2 times (even after I replaced it) and enventually died for no apparent reason. It was under warranty so that they fixed it and it has worked great ever since (I use Xubuntu).

> **anasofiapaixao said:**
> Tried to burn a DVD-RW on my mum's laptop with the 6.06.1 ISO which has 6.06 already burned. Burning pure and simply *doesn't work*. Guess what I have in my mum's PC??? Yeah, Ubuntu.
Install K3b and use it instead of Ubuntu. Or try another program. Don't give in.

> **anasofiapaixao said:**
> PLUS I have just broken the compiz install on her laptop. I had problems with compiz on mine, but as I had apt-get installed and removed various compiz-related packages in order to try to make it work again after update I tought, okay my problem. Forum people told me later that they simply updated and compiz was running fine, so the repos problem had been fixed. I did that on my untouched mum's laptop. I broke her compiz.
DISCLAIMER: I know that it is the non-ubuntu repos (Beerorkid, etc) that are broken.
You shouldn't use Compiz if your main concern is stability.

> **anasofiapaixao said:**
> See why am I so mad? All of this started with the update fiasco and now I just have my nerves blown off...
Something similar happened to me a year ago. My laptop and my main computer were broken, in addition to a series of (unfortunate) events, and I went nuts. Then I calmed down and sent my computers (which were under warranty) back to Compaq.

Take a breath, try to relax for a bit and then learn from what you experienced. No more Compiz, or unstable things, etc. and above all think that your hardware might die unexpectedly (you should keep a spare computer just in case ;) ).


NOTE: the xserver can't break your computer in that way. If the Xserver doesn't work you can run GNU/Linux from the command line (since Unix was not created for making use of Desktop environments)

---

### Post by anasofiapaixao on 2006-08-24
Thanks for the help... my biggest problem is that I am sure for a good couple of reasons that I voided the warranty. That's what makes me more nervous.

I knew compiz/XGL were unstable, and I don't mind having to reinstall the OS, I have done it for more times than I can remember in these three months of Linux, most of them in the first month - even tough it is bad, ESPECIALLY in my tablet that needs a LOT of specific configuration work, it is a risk I am willing to take. I installed it in my mother's computer for the sake of eye-candy playing, and had it disabled for a while until I saw nothing was conflicting with it (more specifically, GMail notifier). What wasn't in my plans was having problems not solvable through a mere OS reinstall... And that's why I panicked. And the money... My laptop had an accident - it fell into the ground and an edge is slightly wrecked. And because of that I've been avoiding going to Toshiba...

ANYONE WITH A TECRA M4 BEWARE: The monitor screws are JUNK, total junk. I have 'screwed up' one; it couldn't be taken off anymore - I am careful with screws, so can you imagine HOW BAD they must be? I am going to buy new ones to replace all the others just for caution -  and the only possible way to remove it wasn't fancy: forcing the monitor cap. The marks are discreet, it is okay being held by the other five screws, but it certainly won't pass unnoticed in Toshiba.

...And I was forced to open it why?? Because of the fall...

The warranty void also means I'll have to ay for the AC adapter repair. The cable sucks, the plug is very fragile and the rubber broke. That NEVER happened to me with LiteON chargers, and I gave them the exact same treatment.

---

### Post by tseliot on 2006-08-24
> **anasofiapaixao said:**
> Thanks for the help... my biggest problem is that I am sure for a good couple of reasons that I voided the warranty. That's what makes me more nervous.

I knew compiz/XGL were unstable, and I don't mind having to reinstall the OS, I have done it for more times than I can remember in these three months of Linux, most of them in the first month - even tough it is bad, ESPECIALLY in my tablet that needs a LOT of specific configuration work, it is a risk I am willing to take. I installed it in my mother's computer for the sake of eye-candy playing, and had it disabled for a while until I saw nothing was conflicting with it (more specifically, GMail notifier). What wasn't in my plans was having problems not solvable through a mere OS reinstall... And that's why I panicked. And the money... My laptop had an accident - it fell into the ground and an edge is slightly wrecked. And because of that I've been avoiding going to Toshiba...

ANYONE WITH A TECRA M4 BEWARE: The monitor screws are JUNK, total junk. I have 'screwed up' one; it couldn't be taken off anymore - I am careful with screws, so can you imagine HOW BAD they must be? I am going to buy new ones to replace all the others just for caution -  and the only possible way to remove it wasn't fancy: forcing the monitor cap. The marks are discreet, it is okay being held by the other five screws, but it certainly won't pass unnoticed in Toshiba.

...And I was forced to open it why?? Because of the fall...

The warranty void also means I'll have to ay for the AC adapter repair. The cable sucks, the plug is very fragile and the rubber broke. That NEVER happened to me with LiteON chargers, and I gave them the exact same treatment.
Sorry to read your frustration.

Think that almost every single piece of hardware I bought was faulty:
2 motherboards, 2 sticks of RAM, 4 Dvd Burners + 2 cdreaders, 1 SCSI controller, 2 hard disks, 1 monitor, my laptop (battery + 2 DVDreaders), and other pieces which I can't remember.

Think that even my saxophone was faulty ](*,) .

I could work as a detector of faulty peripherals (and things in general).


Good luck with your laptop ;)

---

