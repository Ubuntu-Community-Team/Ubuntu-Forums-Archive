---
title: "No sound after upgrading"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by the lush on 2007-10-19
I just upgraded to 7.10, and although I have lost things like the desktop cube, I really like it, unfortunately I have one huge issue - I have no sound. None. Perhaps I screwed up during the upgrade (the system asked me about keeping or replacing files and I had no idea what to do). If I go to System>Preferences>Control Centre>Sound and try the test buttons I am given the following response:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

If I right click on the Volume Control icon in the top panel of the desktop and chose 'Open Volume Control' a pop-up says:

No volume control GStreamer plugins and/or devices found

Any advice would be greatly appreciated.

---

### Post by freemti on 2007-10-19
me too!

Probably something simple, but I haven't found it yet on the forums

---

### Post by Jimlas53 on 2007-10-19
Lots of problems with sound.  Toshiba notebooks are susceptible.  It seems to be a problem with the ALSA driver selection for your particular hardware.  Seems that the installer is not picking the correct drive for the hardware, or the hardware discovery is not right.  Do you have one of the Intel sound devices?

---

### Post by the lush on 2007-10-19
Yep, Intel sound. I had a similar problem going from Edgy to Feisty, but the solution I used that time is not working this time.

---

### Post by Therion on 2007-10-19
My Gutsy install was mute too.  What solved the problem were the instructions in this [[COLOR="Blue"]Comprehensive Sound Problems[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide") thread.  

I skipped down to the **Getting Alsa Drivers from a *Fresh* Kernel** section and started from there.  Those steps got my soundcard up and running in Feisty as well.  Once that was done, I used the save command:

```
sudo alsactl store 0
```

Also as instructed in the post and *voila*... Glorious sound.

---

### Post by opm8 on 2007-10-19
While fixing another Feisty to Gutsy upgrade problem I inadvertently fixed my sound problem.

The useless Adept Manager installer, which crashed half a dozen times, decided that it needed to boot me into the 2.6.22-14-386 kernel after all was said and done.  My dual core cpu was now showing as a single core and smp was not there, either.

Long story short, check which default kernel you're booting in /boot/grub/menu.lst.  I changed mine back to 2.6.22-14-generic, which is what most modern machines should be using.  I got my dual core-ness re-established and the sound came back, too.  :)   It's like playing a country song backwards: your girlfriend and dog come home, you get your job back and find your truck.

opm8

---

### Post by rylleman on 2007-10-20
> **opm8 said:**
> ...Long story short, check which default kernel you're booting in /boot/grub/menu.lst.  I changed mine back to 2.6.22-14-generic,...
THANK YOU!
I've spent all evening trying to fix my audio-problem, compilating ALSA-drivers and whatnot, but to no avail. I then came across your post, tried booting up with generic kernel and voila!, now I can happily go to sleep.

---

### Post by J-Morris on 2007-10-20
I have the same problem. I just upgraded from the beta (The beta!) where the sound worked perfectly and now my sound doesn't work. I have too many things to deal with. Bonx on upgrading to gutsy. 

Therion, what post specifically solved your problems?

EDIT:
OR:

rylleman, can you tell me step by step what you did? I'm not very experienced with linux or grub yet.

---

### Post by Gimli on 2007-10-21
I have also had the sound problem but this post of OPM8 solves my sound problem as well. By choosing the 2.6.22-14-generic option at startup from the Grub menu, my sound is back. Now just the other nagging issue of the VMWare Server that is not workiing because I re-installed it while unknowingly booding up into the 2.6.22-14-386 kernel. I guess I need to reinstall VMWare Server again.
Thanks for the solution.

---

### Post by hinge on 2007-10-21
anybody know what the difference is between the 386 and generic kernel - is one better /more modern than the other or is it same same no difference ?

---

### Post by juk_de on 2007-10-21
Hi all!

I had the same problem after upgrading to gutsy.
In my case the sound module snd_hda_intel could not be loaded, because it has been moved to a new package called **linux-ubuntu-modules-$kernelversion** which has not been installed during the upgrade. :-(

```
apt-get install linux-ubuntu-modules-2.6.22-14-386
```
solved all my sound problems.

HTH
Jürgen

---

