---
title: "Updated nVidia drivers cause sound issues."
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by Goldfoot on 2010-06-02
Ok, let me start by saying that I did search, a lot, and couldn't find a solution to my specific problem.  If it's somewhere in the Comprehensive Sound Problems Solutions Guide, then I didn't find it.  

I just installed 10.04 (64 bit, in case that matters) last night.  I have onboard sound and video,  and they working fine until I installed the proprietary drivers for my video card.  When this happened, my sound got all fuzzy/scratchy.  I can go back into the Hardware Drivers and remove the proprietary ones and then the sound is fine.  My problem is that I want to use better drivers for my video, but not at the sacrifice of sound quality.  I went to the nVidia site, and they have drivers from April 24, 2010 on there, but there's a couple problems with that.  I don't know if they are any different than the ones I already installed through Ubuntu, and I don't know if they will cause the same issue.  Since I'm fairly new to linux, installing the drivers from the .run file seems like more of an undertaking than I want to do right now, and I don't want to mess anything up and not be able to revert my changes.  With the Hardware Drivers utility, I can easily remove the drivers and the sound works, but I don't know if that will be the case.

I have an ECS GeForce7050M-M motherboard.  I can't really find specifics for chipsets, but the nVidia site detected a GeForce GTX 480 for video.  If I recall correctly, my audio is some Realtek HD thing.  I had this same problem when I tried 9.04, but I didn't narrow it down to the nVidia drivers at the time.  This time I was able to, but I don't know how I can fix my issue.  Any ideas?

---

### Post by Goldfoot on 2010-06-07
Anyone?  Not having the video drivers installed caused some pretty substantial slow down on my computer, so I had to install them.  Now I have that fuzzy I sound I mentioned, and it's very irritating.  I use my computer for music and watching videos more than anything else and having a sound issue like this is very unnerving.  I've tried removing/purging the existing sound drivers and then reinstalling them but that didn't do anything for my issue.  I don't really know where else to start because I have no idea what the video drivers may have done to my system that would effect the sound.  Like I said, before I installed the proprietary video drivers the sound worked fine, but now that the video drivers are installed, there's a distinct fuzzy or scratchy sound whenever a sound is played.

---

### Post by Axos on 2010-06-07
Hmmmm. I hadn't played any music since installing 10.04 a couple days ago. Saw your post, gave it a try. I don't think my issues are as severe as yours but I'm getting occasional skips which I definitely did not have on 9.10. Bummer.

I would rather use the Nouveau driver but it causes the fan on my notebook to run much faster than the nVidia proprietary driver even when CPU usage is 0%, suggesting the problem is the GPU running hotter, not the CPU.

I wish I had an answer. I'm just confirming the problem (even though it isn't as severe as yours).

---

### Post by John-ooo on 2011-08-27
I have exactly the same Motherboard and exactly the same issue. I am a newbie and pretty reluctant to try anything where I lose my safety net of removing the Nvidia driver (Music being more important than eye candy) but would appreciate any help

---

### Post by gordintoronto on 2011-08-27
John-ooo: Did you install 11.04? Sound is one area where (mostly) improvements appear with every release.

---

### Post by scottstensland on 2011-08-27
I can second the suggestion that more recent ubuntu releases are MUCH better with sound and video drivers.  ubuntu 11.10 actually comes loaded by default with the very newest nvidia drivers 280.13
so no manual install needed

---

### Post by John-ooo on 2011-09-03
Thx for suggestions guys. In the end I bought a new pci soundcard and avoided the on board sound. Then I could use the restricted drivers happily. Not particularly purest solution but i thought £10 was worth my sanity, john-ooo

---

