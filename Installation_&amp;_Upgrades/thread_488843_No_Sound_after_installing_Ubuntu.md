---
title: "No Sound after installing Ubuntu"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by GITanker on 2007-06-30
I'm new to Ubuntu, but so far I like it. There is one thing that as not worked since I installed it. I have no sound. I have a Creative "Sound Blaster Live" card. I've tried everything I know, but when it comes to Linux I'm a newbe. I've download the drives for Linux but when I go to in stall it says "gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again." The character it is using is "UTF-8

 Any help would be greatly appreciated.

Thanks

---

### Post by logos34 on 2007-06-30
this might help you out:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

### Post by GITanker on 2007-06-30
Thanks for the fast response, I did as it says and it does see my sound card. So it sent me to the alsamixer section. Did as it says and saved everything, still no sound.:( 
Anything else I may try???

Thanks again

---

### Post by Adam_GUI on 2007-06-30
> **GITanker said:**
> Thanks for the fast response, I did as it says and it does see my sound card. So it sent me to the alsamixer section. Did as it says and saved everything, still no sound.:( 
Anything else I may try???

Thanks again

How old is the Sound Blaster Live! card?
You may have to use OSS instead of ALSA.

Just so I'm not overlooking anything, you do have volume turned up and speakers plugged in, right?

---

### Post by GITanker on 2007-06-30
Yes, my speakers and volume is up all the way, I have 3 hard drives in this system and each has a different OS on them. So they all use the same hardware. I had Redhat on  here a few weeks ago and the sound work then. But Redhat was not as simple as Ubuntu. As for the sound card it is about 6 years old. 
What is OSS???

Thanks again guys for the fast response.

---

### Post by Adam_GUI on 2007-06-30
> **GITanker said:**
> Yes, my speakers and volume is up all the way, I have 3 hard drives in this system and each has a different OS on them. So they all use the same hardware. I had Redhat on  here a few weeks ago and the sound work then. But Redhat was not as simple as Ubuntu. As for the sound card it is about 6 years old. 
What is OSS???

Thanks again guys for the fast response.

OSS is Open Sound System:  [http://www.opensound.com/linux.html](http://www.opensound.com/linux.html)
Let me switch go Gnome for a second....
System>Preferences>Sound

Sound Playback should say "Autodetect."
Try the different drivers in the menu and hit the test button.  One of them should work.  I hope.

---

