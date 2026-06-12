---
title: "Dual boot (XP) &amp; 12.04, Ubuntu no boot"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by mrag on 2012-07-15
Last year I somehow installed 11.04 on my Win XP. Worked well, upgraded  to 11.10 and then 12.04. I was happy camper. Moved box downstairs and  didn't use for a month. Went to use it the other day and no go.  Eventually XP and 12.04 working, but 12.04 incredibly sluggish. So I  reinstalled 12.04 from LiveCD. Now XP is fine (although I have to reset  (Walmart) tv/monitor on every start), but now I can't get to 12.04. I  can get the start menu (is that GRUB?) listing Ubuntu 'generic,' a  recovery mode (duh?) a mem test and Windows.

If I select the first Ubuntu, I get a blinking cursor and a bit later:
Gave up waiting for root device: Common problems ....
ALERT: /dev/disk/by-void/bd ...........does not exist
Dropping to shell, BusyBox v1.18.4...(initramfs)

My keyboard and mouse are useless at that point and I have to force  shutdown (hold down start button). In fact I then have to ALSO physically  unplug the pc and discharge it (press start button while unplugged)   before I can even get it to begin booting again.

I have no data or files that I care about on the Ubuntu partition so I  could start 'fresh.' I just have no clue what 'fresh' now consists of  ;-) 12.04, 11.10 ? ? ? or how to proceed in the simplest(!) manner.
Thanks for any advice.

---

### Post by darkod on 2012-07-16
That sounds like possible hardware issue too.

As for reinstalling over the existing partitions, you need to do that with manual partitioning, not with the auto methods in the installer. Although it seems in 12.04 there is an option to install over existing ubuntu installation, but I have never tried it.

Sometimes if the bootloader grub2 doesn't install correctly, it can keep the old one on the MBR which will be broken, because the old installation is deleted. In that case you can simply reinstall grub2 to the MBR, no need to reinstall whole of ubuntu again.

---

### Post by mrag on 2012-07-16
Thank you for your response. While the pc was working quite fine for both XP and 12.04 when I put it away a month ago, I could not rule out some hardware issue. On first attempt after its 'rest,' the monitor said "no signal." At that point I was using a Walmart combo 22" tv/monitor that had been working fine also. At one point I switched over to an old 15" monitor and or took out a video card I had installed a few months ago and just used the one on the mother board. Being a dummy, I did not keep track of the details. However, the 22" tv/monitor AND the 15" monitor both now work fine when separately connected to 'new' video card and using Win XP. I do though have to reset/adjust (center the window) on the 22" monitor on each start. Hardware?

"In that case you can simply reinstall grub2 to the MBR, no need to reinstall whole of Ubuntu again." I apologize. I have absolutely no clue how to do that. I also have no qualms about installing the entire 11.10 or 12.04, but wonder if I should look for anything in particular. (Frankly as I recall, I believe I thought 11.10 'friendlier.')

---

### Post by darkod on 2012-07-16
Restoring various bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by mrag on 2012-07-17
So I tried your suggested tutorial on Grub. First note, people should know there is a difference between 1, l, L, I that I missed on my first try ;-)  I think it went well although it did not immediately fix the problem. However, I was playing with installing 11.10 and 12.04 so it is very possible I was 'fixing' 12 while 11 was the installed version. In any event, I followed you council and then installed 12.04. That went quite smoothly EXCEPT at the very end where it says to 'restart' and the pc hung at that point. I forced a shut down and restarted and things have been fine now through numerous stops and  starts.

Before all this, I did pull out the 'new' video card (MSI-nVidia) I bought several months ago from NewEgg and connected instead to the on-board video. The Walmart monitor I was using and that wasn't keeping its positioning on boot up in Win XP, I hooked up to another pc. It worked fine there! When I had the video card in the problem pc and earlier tried to boot Ubuntu it would just hang. Suspicion on the 'new' video card.

How do you 'test' a video card? 

I don't play 'games' or do much in video, but in the past there was one java app where the graphics were 'messy.' I never could figure how to update the drivers for this eMachine so I bought this on sale video card. It actually had/has been working quite well until I put it on the shelf for a month ;-) leading to this post.

In any event, THANK YOU for the feedback, advice and prodding.

---

### Post by darkod on 2012-07-18
Uh, well, you could try the card in another computer if you suspect it's not working properly.

Also, with nvidia in many cases you need to add the boot parameter nomodeset to allow you to boot once after the installation, and activate (install) the correct driver. Usually even live mode doesn't work with many nvidia cards without the nomodeset.

You could try adding the card back, be prepared if you need to use nomodeset to boot, and activate the driver. You have more about nomodeset in this link, note that it also explains what to do before installation (which you already did install), so focus only on the part about the first boot after the install (lets consider it forst boot after you put the card back in):
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

Even if that doesn't work, when you take out the nvidia it should keep working with the onboard as it is now.

---

