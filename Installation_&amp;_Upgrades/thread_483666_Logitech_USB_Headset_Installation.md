---
title: "Logitech USB Headset Installation"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by cobert on 2007-06-25
Okay i have a logitech usb headset. I plug it into my machine and nothing happens. it doesnt even detect it i dont think. (2nd day on linux for me) I look at the sound devices list and it does not show up. are there any drivers i need? i looked on the logitech website and there were no downloads for it. no cd's came with it. just the headset.

---

### Post by merlinus on 2007-06-25
I have the same device, and selected usb audio in System/Preferences/Sound for Sound Events, Music and Movies, and Audio Conferencing - Sound Playback.

It works fine with Skype also.

-merlin

---

### Post by cobert on 2007-06-25
it does not show up under the device list.. any ideas on what to do?

---

### Post by cobert on 2007-06-25
bump... help guys i need this headset to work please help me

---

### Post by merlinus on 2007-06-25
What does show up under the devices lists?

-merlin

---

### Post by cobert on 2007-06-26
my sound card, and the on board sound

audigy 2 & sigmatel

---

### Post by merlinus on 2007-06-26
What is the output of:

```

cat /proc/bus/input/devices

```

I have this section in that file:

I: Bus=0003 Vendor=046d Product=0a02 Version=0100
N: Name="Logitech Logitech USB Headset"
P: Phys=usb-0000:00:1d.0-1/input3
S: Sysfs=/class/input/input5
H: Handlers=kbd event2 
B: EV=3
B: KEY=c0000 0 0 0

-merlin

---

### Post by TLoockx on 2007-07-06
I have the same problem with a logitech usb headset 250. Ubuntu recognizes it but when I try some settings in system -> preferences -> sound nothing seems to work.

---

### Post by Cairna on 2007-07-15
Same goes for me, troublesome.

---

### Post by byrona on 2007-07-23
I am also experiencing this same problem with the Logitech 250 USB headset.

---

### Post by byrona on 2007-07-24
Ok, so I was able to resolve this problem on my system.

I went to System>Administration>Services and checked the box next to Audio Settings Management (alsa-utils).

I then went into System>Preferences>Sound and choose USB.

This seemed to fix my problem.  Hope it helps some of the rest of you also!

---

### Post by guitarist809 on 2007-08-14
I can get sound to work w/ a Logitech USB headset in rythmbox, but as far as system sounds go (and any other app, including firefox), it fails to play anything.

I'm having trouble figuring this one out!

---

### Post by heimo11656 on 2007-09-15
I have the same problem. I play starcraft and skype with my ally at the same time. I have to talk with my headset and hear the game from my pc speakers. It's awkward.

---

### Post by msmarti58 on 2007-09-20
Thank you thank you. I went where you said and it works! I was so upset that I could not get it to work.

---

### Post by msmarti58 on 2007-09-20
Spoke too soon. I can hear songs in my headset, but I can't hear Firefox or anything else. Luckily I do have a regular headset, ah, but now I can't get it to work either.

---

### Post by heimo11656 on 2007-09-22
Again same situation for me, the headset seems to take only certain kinds of sound like music.

---

### Post by Quiane on 2007-10-30
bump...anyone got this fixed, or any idea where to start diagnosing and fixing this problem????
Thanks!

---

### Post by ubernoobuntu on 2007-11-01
I'm having the exact same problem....its plugged in and detected in system>Preferences>Sound>. I set usb audio for everything, but when i click on test there is no sound. lsusb shows it as connected, but there is no sound whatsoever.

---

### Post by ubernoobuntu on 2007-11-01
also, when i try to test the microphone in system>preferences>sound it gives me this error


Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'


Help needed, PLEASE!

---

### Post by Kallewoof on 2008-03-06
> **ubernoobuntu said:**
> also, when i try to test the microphone in system>preferences>sound it gives me this error


Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'


Help needed, PLEASE!

Exactly the same error for me.

---

### Post by teamkiller87 on 2008-03-06
Thought I might revive the thread as I've encountered problems as well, Ubuntu recognizes the headset in lsusb but no sound output is experienced. The fix suggested by a previous poster didn't work. I really hate doing this but, BUMP!

---

### Post by Kallewoof on 2008-03-06
Although GNOME does whine, I got things working after following the guide here (it's for Wine and World of Warcraft, so not interesting to some of you perhaps) --> [http://forums.worldofwarcraft.com/thread.html;jsessionid=197CFE7C6440B936DAD38E51382C3625?topicId=2200220013&sid=1](http://forums.worldofwarcraft.com/thread.html;jsessionid=197CFE7C6440B936DAD38E51382C3625?topicId=2200220013&sid=1)

---

### Post by SloYerRoll on 2008-03-06
I'll add a bump to this. 

I set up everything to USB. I can hear music and movies. :)

My headset doesn't pick up anything though so I can't Skype. :confused:

Any new ideas out there?

---

### Post by papaja1992 on 2008-03-07
check out this ubuntubrainstorm idea: [http://brainstorm.ubuntu.com/idea/3764/](http://brainstorm.ubuntu.com/idea/3764/)
and vote

---

