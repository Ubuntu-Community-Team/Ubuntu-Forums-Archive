---
title: "aplay/startup sound works, but sound throughout system doesen't"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by AndrewTheArt on 2008-09-29
Hey guys, let me describe my situation to you -

* I have a Toshiba A215-???? laptop (can't remember the last four numbers, sorry)
* Running Ubuntu 8.10 Intrepid kernel 2.6.27-4-generic. Upgraded from Hardy recently, in which sound worked perfectly. 
* The sound driver that has consistently works for me is  snd-hda-intel, and ALSA.
* The start up sound when I'm logging into the Ubuntu desktop plays fine
* The command "aplay -vv whatever.mp3" works fine, I can hear the audio.
* Sound seemes to be working in a virtual machine of mine using VmWare.
* Sound throughout the system, however, does not work! (Firefox, Rythmbox, whatever)
* I have everything set to Autodetect in System -> Preferences -> Sound.

Any ideas why sound would not be working in Firefox, Rythmbox, and all other user applications? 

Andrew

PS - In Hardy, one of the things I did was add -

[B]options snd-hda-intel model=toshiba
[/B]
To my /etc/modprobe.d/alsa-base file. I've done this in Intrepid as well (got erased).

---

### Post by dogson on 2008-09-29
I had this aswell on Intrepid, try disabling the startup/waring sound, that made alsa/pulse work again for me.

---

### Post by markbuntu on 2008-09-29
Well, there have not been a lot of drastic changes in Intrepid as far as sound goes, but there is a thread on Intrepid sound fixes here:

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

### Post by AndrewTheArt on 2008-09-30
dogson - tired that, didn't seem to work.
markbuntu - followed that guide, now my sound is completely broken. When I try to change the volume (for example) I get

No volume control GStreamer plugins and/or devices found

---

### Post by markbuntu on 2008-09-30
Did you read the thread or just follow the OP?

---

### Post by AndrewTheArt on 2008-10-01
I read the OP at first, but at your suggestion I read (most) of the entire thread. The only additional info I got out of it was to install/run "padevchooser", but has not seemed to solve my problem. The options are a bit intimidating.

---

### Post by AndrewTheArt on 2008-10-05
OK, guys, I'm sort of desperate here. Sound simply does not work at all for me anymore.

---

### Post by markbuntu on 2008-10-05
You can look in my guide here which is basic sound troubleshooting, should be pretty much the same for Intrepid:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by AndrewTheArt on 2008-10-05
> **markbuntu said:**
> You can look in my guide here which is basic sound troubleshooting, should be pretty much the same for Intrepid:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I looked at your guide, but I got stuck pretty quickly because I couldn't even successfully open the volume/sound control in the top system tray without getting errors.

I fixed my sound problem though (running a Toshiba A215-???? laptop, kernel 2.6.27-4), by more or less directly following this guide -

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Essentially, I updated to the latest version of ALSA (by directly following the steps in the section "Update to the Latest Version of ALSA"). Note on that step - the latest version of ALSA will of course have the latest "[Last Modified]("ftp://ftp.alsa-project.org/pub/driver/")" date near it when you are downloading the files. After downloading the thee archives I proceeded to open the file "alsa-base" in gedit -

```
sudo gedit /etc/modprobe.d/alsa-base
```...ensuring the line

```
options snd-hda-intel model=toshiba
```was at the bottom. If you're looking at this post are trying to troubleshoot for your laptop/desktop, you'll probably need to change the model you put in the file. The process for finding out your model is by running the following command to get the codec - 

```
cat /proc/asound/card0/codec#* | grep Codec
```Next to Codec: will be the name of your soundcard. (For instance, I found Realtek ALC268, so I remembered "ALC268" and went on)

Then the guide says to run through a file and look for a reference to this codec.

The file (updated continuously I believe) is online, here - 

[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

or locally on your machine it may be here - 

```
/usr/src/modules/alsa-driver/alsa-kernel/Documentation/ALSA-Configuration.txt
```Safe bet is to use the one online.

Open it up and search for references to the codec you found before. You should get a result, at which point you'll see a list of models that are associated with the codec. Pick the one that best describes your machine (in my caes, "toshiba" because my laptop is Toshiba :P).

Then I went to System -> Preferences -> Sound and made sure everything was on Autodetect.

Then I rebooted. Everything worked at that point.

---

