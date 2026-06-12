---
title: "No Sound with Snd Blaster"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by Sidewinder1 on 2007-11-27
Greetings,
Have searched and played with settings, drivers, etc. to no avail. No sound whatsoever. Trouble shooting page said to post to forum:
ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ubuntu@ubuntu:~$ lspci -v
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
        Subsystem: Creative Labs Unknown device 1003
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at ecc0 [size=32]
        Capabilities: <access denied>

02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
        Subsystem: Creative Labs Unknown device 1003
        Flags: bus master, medium devsel, latency 64
        I/O ports at ecf0 [size=8]
        Capabilities: <access denied>

ubuntu@ubuntu:~$ sudo modprobe snd-emu10k1
ubuntu@ubuntu:~$ sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
E: Couldn't find package module-assistant
ubuntu@ubuntu:~$ sudo dpkg-reconfigure alsa-source
/usr/sbin/dpkg-reconfigure: alsa-source is not installed


    This is as far as I got when trouble shooting page suggested to post here.
All sound works perfectly when I boot to XP 
Please keep in mind that since this is live session and I can't save, changes will only effect current session. Am a total noob to Linux but I love it!!!
A heart felt thank-you in advance for any help you folks can provide,

Side

---

### Post by linuxwizard on 2007-11-27
Have you tried this
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF.

To get to the switches > right click speaker icon on gnome panel > open volume control > click on switch tab > you could have 3 or 4 settings there look for the one analog/digital unmark it > try playing something

---

### Post by Sidewinder1 on 2007-11-27
Thanx for the response Wiz. Yes, I've tried that. I think I've toggled every switch I could find; still no joy. Not even system sounds work. I've had a music CD running while trying all of he) switches and settings, not a peep. BTW am running GG (7.10) under live session if that makes a difference.

---

### Post by Sidewinder1 on 2007-11-28
Well I've now done a full install of GG 7.10 to my second hard drive and everything works fine; except the sound. No system sounds, no sound when playing CD in Soundjuicer or Rythmbox I've done the searches, tried all of the fixes from threads on this board, even screwed around with the plugs on the card to no avail. If Windoze XP wasn't working with full sound ability, I'd think my card was shot or the speakers weren't connected. 
   Perhaps I'll just have to hum alot.

---

### Post by cessnap on 2007-12-02
I also have the same problem:

Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X

Appears there are recurring problems by other users as well. Also searched everywhere, Creative has no Ubuntu drivers, that was one of my searches.

Silence is golden. By the way, for switches i only have one choice:Analog/digital Output Jack, if i check this speakers crackle and humm, otherwise nothing.:(

---

### Post by Sidewinder1 on 2007-12-14
Finally solved the sound problem. I plugged the speaker lead into the next jack on the sound card and IT WORKS!! The really interesting aspect is windows also works, plugged into this second jack; when it (windoze) worked flawlessly for years when plugged into the first jack. If that makes any sense.
Ed

---

