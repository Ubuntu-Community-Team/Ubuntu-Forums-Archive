---
title: "upgraded to studio, sound card not working, keyboard sluggish"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by itchy88 on 2008-02-28
hi all,

i do a lot of audio stuff, so when i heard about ubuntu studio i upgraded my gutsy 7.10 and was anxious to start exploring all the new apps.

problem is that two previously functioning aspects of my regular gutsy have disappeared.

now my sound card is wonky, only plays the first five seconds of any song and then crashes any app i'm using:  noatun, amarok, songbird, or banshee.

the test signal on the administrative sound module lets out and intermittent beep, not constant and then crashes that module!

any ideas?

also, my keyboard, (i'm dual booted into xp right now just to type this) acts like it is in slow keys accessibility mode.  i have to pause a number of seconds just to wait for the cursor to show up.  if i type at my normal rate, only the odd character is logged.

i checked the accessibility options and they're off.  the keyboard works, as i'm typing fine on it now in xp.

same with the sound card, btw.

i've read in other posts that this might be due to the latency.  but that doesn't make sense since a lot of sound programs, particularly trackers use keyboard shortcuts to trigger effects.  installing a low-latency kernel shouldn't seize up the rest of the os.

i have an amd athalon 64 bit dual core processor, so yes i checked the system stats and the machine is no where near taxed.  web pages load regularly and the mouse reacts properly.  

please help!  i'm stumped.

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by itchy88 on 2008-02-29
thank you for the quick response!
yes, i tried all the audio options in the sound settings, all have the same result.  really frustrating!  on an interesting note, my asio sound card (m-audio delta 440) did not show up in the list, only in the mixer module.  it doesn't matter though really as i want to use alsa as my main audio outs, not the asio.
any other ideas anyone?

---

### Post by itchy88 on 2008-03-02
hi all, there must be someone who's had this problem?  i'm sure something just needs a little tweak.  anyone?

---

### Post by itchy88 on 2008-03-07
please please please!

someone?

i got my keyboard and sound card working somewhat by copying the xorg file from ubuntu live into my X11 folder.  but the problem recurs shortly after launching any audio application.  i can run for hours, even days just running evolution, terminal, firefox, etc.  once an audio app gets running, jack, audacity, banshee, amarok, etc., i have a few minutes usually and then the keyboard starts to get sluggish and the sound card quits, program crashes.  and it doesn't matter if i'm running oss, alsa, asio.  blah.

i did an upgrade from my regular ubuntu to studio, so i'm wondering if something got lost in translation.

i'd like to try studio hardy heron alpha, but i don't want to lose all the info and settings i've got.  can someone point me to a wiki or forum entry for overlaying hardy heron on top of gutsy gibbon without affecting the current setup?

thanks.

---

### Post by itchy88 on 2008-03-24
temporary solution:

my sound issues were resolved here:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

also i figured out after many installs that the real time kernel we're encouraged to upload with ubuntu studio, de-prioritizes the usb hub onboard my motherboard.  it's installed this way:
sudo apt-get install linux-rt
i couldn't find anything to re-prioritize the usb hub so i then installed the regular linux kernel:
sudo apt-get install linux

now i have both versions to choose from in grub.

also, for the real-time kernel i got myself a ps2 keyboard and mouse to get around the usb latency.
sadly, i have a usb midi keyboard that slowly loses its usefulness over a period of hours.

if there are any devs reading this, i'd love a heads-up if there's a fix for this issue.  it seems ridiculous that usb would gain latency over time when so many music interfaces (keyboards, etc.) run off usb.  fyi, i have an MSI k9vgm-v with a VIA ksm890 chipset.  the one thing that i'm still looking into is my memory.  it's a fast motherboard and a dual core processor.  but the one gig of memory sometimes seems to get taxed for some reason.  up around 60-70% of system resources.  i'm going to play with the bios a bit and probably get some Kingston HyperX low-latency RAM.  we'll see!

i hope this helps anyone who's run into the same problem.

---

