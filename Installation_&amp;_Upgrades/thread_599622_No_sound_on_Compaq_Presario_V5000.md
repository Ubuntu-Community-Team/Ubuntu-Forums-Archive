---
title: "No sound on Compaq Presario V5000"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by saurabhperiwal on 2007-11-01
Hi all,

I have seen other threads but they all are specific to a laptop made.

I have Compaq Presario V5000 serial laptop
AMD Sampron processor Graphics by ATI Radeon Xpress 200M

I upgraded to Gusty today and there is no sound .... 

I made some chages in syatem -> Pref ->sound then also no sound.

Please help cant live with out movies and music :)

Thanks in advance

Cheers
Saurabh

---

### Post by Pumalite on 2007-11-01
Here are a few links and tips among which you might find your answer:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound)
[http://ubuntuforums.org/showthread.p...ght=sound+will](http://ubuntuforums.org/showthread.p...ght=sound+will)
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)

If it doesn't work go to [http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage), download the
alsa-driver, lib and utils and follow the Howto at the same address and look for your driver at the Sound card matrix. Then, if needed, apply the patch and add something at the end of /etc/modprobe.d/alsa-base (sudo gedit) at described in the previous link. I do not own the same laptop but I also have got a Intel Sound Card and worked a bit to have a functioning audio.
I hope it will help you

After fiddling with the sound settings trying various suggestions in the Comprehensive Sound Problem Solutions Guide thread, I totally buggered up my sound. Oh well, a fresh install of Feisty never hurt anyone and I had my /home directory on a separate partition.

After the new install, I still had the 6 symptoms described above.

Thinking that it might be some sort of .config file remnant, I created a new user and everythng worked properly. A-HA! Comparing the user home directories, I noticed the presence of a .asoundrc file and another similarly named file. After doing some research here about what the file is for (and it's safe removal), I deleted it, logged out and returned to a system with full working sound.

My suggestion is this:

1. Create a new user account
2. Login using new user account
3. Check to see if sound works properly
4. If it does, then the issue is likely some sort of config file. Look for the .asoundrc file in your original home directory and move it to a backup folder (just in case)
5. Log back in as your original user and test.
6. If it fails to cure the problem, try the Comprehensive Guide above.

---

### Post by saurabhperiwal on 2007-11-02
Hi,

Thanks a little success :) , I created new user and sound works great in that ... but i cant find .asoundrc anywhere :(

What can I do

Thanks 
Saurabh

---

### Post by saurabhperiwal on 2007-11-02
Hey ... looks like my new user healed the old one ... I couldn't find the file but when i logged back in as old user sound was working :guitar:

Thanks^100
Saurabh

---

### Post by Pumalite on 2007-11-02
You are welcome. Good luck.

---

### Post by mpeters13 on 2007-12-28
I have the same laptop. I can't find anyway to force the volume keys to adjust the PCM audio (as the Master audio track volume sliders don't actually adjust the volume...) Any advice?

---

### Post by Pumalite on 2007-12-28
Did you try the 'Arrow Up?
Post a screenshot of your alsamixer.

---

