---
title: "Backup and copy ubuntu 8 install?"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Johnnyboyct on 2008-07-10
Hey guys, Ive gotten a little more comfortable, but Im still on my journey. I installed 8 on my desktop, completely getting rid of windows on an ide drive. I also have 2 sata drives 1 with an old ubuntu intall Id like to remove and 1 NTFS drive that has all my docs and stuff. 

Id like to make the best and esiest to restore image of this install, everything is the way Id like it, but I also think this drive is on its way out. Im unsure how to backup correctly, I did the tar backup from another thread, but I want to completely move this install over, a clone if possible. 

Is there a fairly simple way I can try without killing this install? Id like to clone my ide to one of my satas, but Im not completely sure, its the one with ntfs on it.

John

---

### Post by Pumalite on 2008-07-10
This might help:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by Johnnyboyct on 2008-07-10
Thanks, I also am having audio troubles :( 

I have an x-fi and an onboard soundcard. I couldnt get the xfi to work so I started using the onboard one. It works, gave me trouble with flash, but its ok now. Only problem is, none of the audio apps work. I tried unistalling and reinstalling the apps, no luck. How do i find out which its using now asla or oss or whatever? How do i remove?

John

---

### Post by Pumalite on 2008-07-10
Preferences>Sound
Have you installed all the codecs?

---

### Post by Johnnyboyct on 2008-07-10
Sound says asla in all the boxes. I installed ubuntu studio audio and video, and most of the apps dont work :( A few of the mp3 players freeze or fail.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

When I hit test, but it works. Also the tray  volume is hacked and I cant put the other one back:
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.



But sound works...

---

### Post by charonred on 2008-07-10
I had a similar prob with sound after I installed KDE 4.0 (won't do that again), anyhow the only way I could get it fixed was to re-install Ubuntu, and to avoid messing up other drives, I unplugged all but the one I was installing to.

And to the cloning,
I used Acronis True Image from Hiren's Boot Disc 9.5 to creat a disc image of my Ubuntu install, and saved it to another drive (ready for 'restore' if needed) - I'll also be making other images as I progress with Ubuntu customising so I can easily go back to a version that works.

[About Hiren's]("http://www.hiren.info/pages/bootcd")  |  [Download from here]("http://www.9down.com/Hiren-s-BootCD-9-5-23765/") (unzip and burn .iso, then boot from disc) :)

---

