---
title: "gateway g6 350 live CD problem"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by hotrod6657 on 2008-01-08
Okay, i just took an old gateway g6-350 off my aunt's hands.  It's a real old PII that was made for Win 98.  I of course don't want win 98 and would much rather have ubuntu.  I've dug out my Live CD's and i'm having some trouble.  I'm using CD's that i know work, i've installed on other machines with them, but i can't get very far with tthis one

Everything seems just fine, it loads the first screen that has me decide what i want to do and it acts like it's loading the CD but then it hangs up.  It loads the splash screen with the progress bar and then the screen goes black with a little underscore in the upper left corner and stays there, for a while.  It just never gets past that.  I do know the computer only had like 64 mgs of ram so i'm assuming that the problem might be in that.  Any way, how would i determine if that's the problem and what are some other ways of trying this? 

I've never used the text based installer and i think i would need a walk through to do so if that's a viable option.  I don't want to clear the drive right yet, i'd like to keep win 98 on there until i get linux working on it so that would likely complicate the whole partitioning process.

any ideas would be greatly appreciated.  Thanks in advance.

hotrod

---

### Post by hotrod6657 on 2008-01-08
Okay, so i did some more looking around and i'm pretty sure that my ram is what's holding me back.  

[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu]("http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu")

That link says you need 192 mbs to run the  CD and 64 is far from that lol.  Not to mention that it gives a really nice tutorial on installing ubuntu with the text installer, i just need to figure out the partitioning so that i can keep win 98 for a little and make sure that ubuntu works.  Any ideas?

---

### Post by Partyboi2 on 2008-01-09
you could have a look at xubuntu the alternate cd
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)
Alternate Install CD only requires you to have 64  mb of ram

---

### Post by hotrod6657 on 2008-01-09
i got the alternate CD to work and installed xubuntu just fine.  I'm downloading the one for ubuntu right now to try just for fun.

What's the difference between the two, aside from minor layout differences?

EDIT:
I must say, i was rather impressed with the partitoning "wizard" on the alternate CD.  I think it worked as well if not better than the GUI one on the normal Live CD.

---

### Post by hotrod6657 on 2008-01-10
I got the Ubuntu alternate CD to work too, but it's sooooooo slow.  xubuntu moves along pretty well when i'm opening windows and what not, the ubuntu one doesn't at all.  I had the system resting with the system monitor open and the cpu raised up to 100% for a few seconds, i wasn't doing anything, it's strange.  I'm hoping once i get connected to the internet and update it that it might fix something.

---

### Post by 512mattw on 2008-03-31
I have this same computer and when I try to boot from live cd it tells me I need to put bootable dis in and press enter.  I changed the boot order from bios to do cd first and everything else disabled.  Could it be that I need more ram 256 or 312 to get it going off bios.  Right now I have 192 mb ram.  please help I would like to get ubuntu running on the relic.

new to ubuntu

Matt

---

### Post by DMBrazil on 2008-07-06
Any luck with these?! I just came across one of my dads out work computers and sure enough, it was the g6 350. I had the same idea, but am running into similiar problems, my also says i fail the bios cut off but i can find new bios for it anywhere..

---

### Post by hotrod6657 on 2008-07-06
I really didn't have much luck with ubuntu on this machine.  The processor is very slow and mine has practically no memory(64 MB).  Using the alternate CD you I got it to load without doing anything special but the computer was really struggling to keep up once the system booted.

I did get Fluxbox and Xubuntu to work okayishly.  Nothing with a live CD seems to work on mine because there's just no memory so others with more ram might have better luck.

(I hate to say it but right now it's running an absolutely bare bones version of XP and actually doing quite well.  I will add though that if i knew half as much about Linux as I do about XP that i would expect similar results with Ubuntu.)

I didn't have any issues with the bios giving me grief.

The setup screen says i have version:

4R4CB0XA.15A.0014.P04

No idea when that version would point to but knowing my aunt (who i got it from) it's probably never been updated... lol

If you want to try one of the low resource versions of Ubuntu like Xubuntu go for it!  I think they would be just fine once you got used to the slightly different menus and what not.  I'm just a little spoiled with my other faster computers so waiting for windows to load really bothers me.

(I installed win95 at one point and even that was pretty slow so the fact that the latest version of Ubuntu would even load even if it was slow is amazing!  That would be like installing a full version of XP on the thing and expecting everything to be lightening fast lol)

hope that helps a little, i had forgotten all about this thread.

hotrod

---

### Post by Partyboi2 on 2008-07-06
Here are a couple of useful links:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by DMBrazil on 2008-07-06
i am planning on running xubuntu. but i still cannot get past this bios cutoff failed error, it keeps going but then ever loads anything... any ideas anyone?

and also, ive always been curious, is there a way to know my processor speed and ram without loading a OS?

---

### Post by hotrod6657 on 2008-07-06
Can't really help on the bios thing but if you press F1 i believe while the thing is booting up it should take you to the bios setup screen.

You don't have to have anything loaded for that, just start pressing F1 as soon as you hit the power button and it should load the setup screen which will give you boot order, processor speed, ram, bios version, etc.

---

### Post by Partyboi2 on 2008-07-07
> **DMBrazil said:**
> Any luck with these?! I just came across one of my dads out work computers and sure enough, it was the g6 350. I had the same idea, but am running into similiar problems, my also says i fail the bios cut off but i can find new bios for it anywhere..
Try booting using some [[COLOR=Blue]boot options [/COLOR]]("https://help.ubuntu.com/community/BootOptions")like acpi=force or acpi=off

---

### Post by hotrod6657 on 2008-07-07
man, as far as finding a bios update i don't know what to say... All the searching i did said it's pretty much a lost cause...

If anyone can tell me how to copy my Bios I would do it and upload my Bios image to help you out but i don't know...

Ideas?

---

