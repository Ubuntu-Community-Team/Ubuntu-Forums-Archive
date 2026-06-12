---
title: "Sound problems (82801H - HD Audio Controller - rev 02)"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by veliro on 2007-11-12
First of all, sorry for the new post. But I have searched, tested and failed many of these guides about getting the sound working.

The problem: No sound in Gutsy. The strange thing is that I had Edgy before, and the sound worked there. After some days without sound in Gutsy I gave it up and tried both Feisty and Edgy again. No sound there neither! I have reinstalled and upgraded many times, I have also set my options in the bios to default.

```

me@desktop:~$ lspci -vv | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

```

me@desktop:~$ cat /proc/asound/cards
--- no soundcards ---

```

```

me@desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

Mainboard: Asus P5B-Deluxe (wifi edition)
I don't know if there is a difference between rev 02 and rev 03, most threads I have read is about rev 03.
Any tips? Btw. I have a clean install of Gutsy 7.10 32bit now.

---

### Post by veliro on 2007-11-13
I'm giving up, hope someone can post a solution to this problem if they find any.
Tomorrow I'm gonna buy a cheap pci-soundcard.
*Need sound :)*

---

### Post by kyphi on 2007-11-13
The only solution that I can offer is that you install a soundcard, such as the Creative Soundblaster Live 5.1 which works very well and does not cost an arm and a leg.

I have the same audio controllers on my motherboard but they worked only erratically.

Inbuilt sound and video controllers are still the Achilles heel for manufacturers of motherboards.  Best to replace them with separate sound and video cards.

Remember to disable the onboard sound chips in the BIOS after installing your soundcard.

---

### Post by veliro on 2007-11-13
Creative Soundblaster Live 5.1 it is :)
Thanks for the bios hint!

---

### Post by derfinsterling on 2007-11-13
> **kyphi said:**
> Inbuilt sound and video controllers are still the Achilles heel for manufacturers of motherboards.  Best to replace them with separate sound and video cards.


That's hardly an explanation or solution when my sound card worked fine till the necessary reboot after upgrading from Feisty to Gutsy.

---

### Post by kyphi on 2007-11-14
> That's hardly an explanation or solution when my sound card worked fine till the necessary reboot after upgrading from Feisty to Gutsy

My advice was in response to a question from veliro.

To 'shanghai' someone else's post is impolite, derfinsterling.

For your particular problem, please start your own post.

---

### Post by Seikmann on 2007-11-14
I also have a soundcard problem in Gutsy. 
```

seik@portable:~$ lspci -vv | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```
As you can see I use a laptop, which means that I cannot buy stuff like extra PCI soundcards (and neither dragging around an USBsoundcard either). 
I got my hands on a driver for the soundcard, but I don't know how to install it. 
My friend talket about ALSA, but I don't know how :/

---

### Post by THROBiX on 2007-11-14
Seikmann: You could try to read the readme within the compressed driver package. It should explain the most advanced part and so on of compiling the driver and install it.
However, compiling a driver doesn't always work as easy as you may think. There may be necessary packages needed to compile the driver, and without them, problems while compiling may occur and give you the headache.
But as written above, try reading the readmes - they exists to help you out.

---

### Post by Seikmann on 2007-11-14
> **THROBiX said:**
> Seikmann: You could try to read the readme within the compressed driver package. It should explain the most advanced part and so on of compiling the driver and install it.
However, compiling a driver doesn't always work as easy as you may think. There may be necessary packages needed to compile the driver, and without them, problems while compiling may occur and give you the headache.
But as written above, try reading the readmes - they exists to help you out.

About the readmes, I've read most of them, and they don't seem to help much. 
I'll try to use ALSA, if I just figure out how to do whatever I must do.

---

### Post by THROBiX on 2007-11-14
ALSA is already loaded in the Linux kernel. It's in use by default.

---

### Post by veliro on 2007-11-14
And a good advice. A Creative sound blaster 5.1 costs nearly nothing. Got mine today, and everything worked at once after restart!
I tried plenty of howto's with the integrated card, but after some days with failing you get really impatient. Can't use my computer without sound! Now everything works, it's wonderful! :)

Seikman: Most howto's out there is about rev 03, my soundcard is rev 02... I don't know if there is a difference, but thats the reason why i gave up.

---

### Post by Len_C on 2007-11-17
seikmann:

Try [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)
This howto should also work with rev 02  - [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/#comment-6](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/#comment-6)

---

### Post by Seikmann on 2007-11-21
> **Len_C said:**
> seikmann:

Try [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)
This howto should also work with rev 02  - [http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/#comment-6](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/#comment-6)

Thank you very much. This did indeed work on my HP dv9550eo with Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Edit: Problem is that there is little sound in my headset, and it does not actually mute my speakers.

---

### Post by Ashrael on 2007-11-21
hmmm, i seem to have a similar problem :

[http://ubuntuforums.org/showthread.php?t=618554](http://ubuntuforums.org/showthread.php?t=618554)

But when i start up the livecd my soundcard works correctly???
Please try this too and post your experiences, please.

thanx

---

### Post by veliro on 2007-11-22
> **Ashrael said:**
> hmmm, i seem to have a similar problem :

[http://ubuntuforums.org/showthread.php?t=618554](http://ubuntuforums.org/showthread.php?t=618554)

But when i start up the livecd my soundcard works correctly???
Please try this too and post your experiences, please.

thanx

I gave up my soundcard (read earlier in the thread). But I do remember that my soundcard did not work with the live cd either (I'm 100% sure),

---

### Post by Ashrael on 2007-11-28
i removed pulseaudio package, and now it works....

HTH

---

