---
title: "Help Installing 8.04 LTS"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by jrich1516 on 2008-06-15
I am having a hard time with my laptop.  It is a Dell Inspiron 4000.  I am trying to dual boot WinXP and 8.04 LTS using [this]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") tutorial.  To start, I had had a hard time installing WinXP.  I got the "34 Minute Hiccup" and followed [this]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") tutorial.  I deleted a file from the setup called "wdma_es3.inf" which was the audio driver.  So after I deleted that file according to the tutorial XP worked fine, except the sound card didn't work.  I tried to install drivers from the Dell site after I installed XP but that just crashed my computer.  So I redid the whole setup and now XP is working fine, but again with no sound.

I have installed Linux before.  I previously ran openSUSE 10.3.  This was the only Linux distro that didn't have errors during the installation.  I tried Ubuntu, Mandriva, and other types.  openSUSE worked well, but I still had no sound.

When I try to install Ubuntu using the LiveCD and I press "
Try Ubunto without any changes to your computer", it always stalls on the same part.  The screen says:

*Loading hardware drivers...
[  189.382750] BUG: soft lockup - CPU#0 stuck for 11s!  [modprobe: 5532]

Then it keeps repeating that same message, except the number at the beginning increases by about 11.8.  I am almost sure this is about my sound card.  I am certain it is broken and causing all of these problems.  What should I do?  Send it to Dell for maintenance?  I don't really need sound on my laptop, so should I go in and somehow remove the soundcard?  Please help!  Thanks!!!

---

### Post by wpshooter on 2008-06-15
I certainly would not be going into a Dell laptop and trying to repair unless I was a trained Dell technician.

And I certainly would at least call Dell and ask them about the sound problem especially if the computer is still under warranty.  

Since you are having this same sound problems under several different O/S types, may I ask if you have gone into the BIOS and checked to see if all of the sound related BIOS parameters are set correctly ?  Two things you might want to consider is is your BIOS on the latest available version and also have you considered setting all of the BIOS parameters back to the DEFAULTS and see if this might be a cure for you sound problem ?

Good luck.

---

### Post by Pumalite on 2008-06-15
How much memory do you have in that laptop? And what iso are you trying to install?

---

### Post by jrich1516 on 2008-06-15
Wow, you guys are MUCH faster than the openSUSE people.  The laptop is 7 years old and there is no warranty on it.  Merely shipping the laptop to and from the Dell Repair Center might cost more than the laptop is worth.  I am trying to install Ubuntu using the ubuntu-8.04-desktop-i386.iso burnt onto a cd using InfraRecorder.  System Properties on WinXP says I have 384 MB of RAM.  I will now install the latest BIOS and set everything to the default.  Thanks for all of the help guys!!!

---

### Post by Pumalite on 2008-06-15
Do md5sum, burn at 4x or less and you are good to go. But, if you have 'funny' graphics, better use the Alternate CD

---

### Post by jrich1516 on 2008-06-15
Well, I did md5sum but I will reburn at 4x.  I will try to use the alternate cd, but I don't want to mess with the partitions only to find out that Ubuntu still won't install.  In WinXP I had to trick the installer, so I might have to do that here.  Is there a way to edit the installation cd and remove the audio drivers so they don't try to install?  I think that the only reason that openSUSE worked is that the setup tried to install audio drivers but then "gave up" and skipped them.  I really think that tricking the installer will be the ultimate solution here, I just don't know how to do it.

---

### Post by Pumalite on 2008-06-15
It probably can be done, but I couldn't guide you there; sorry.

---

### Post by VMC on 2008-06-15
I read something on this laptop working under Red Hat. It shows  the sound as "ESS Maestro-3i Soundcard". I'll give you the link because there are other links that helped set this up: [http://easyweb.easynet.co.uk/~maf/Inspiron4K.html](http://easyweb.easynet.co.uk/~maf/Inspiron4K.html)

The sound setup was from this: [http://www.cnbc.cmu.edu/~masmith/i4000/#sound](http://www.cnbc.cmu.edu/~masmith/i4000/#sound)

This is just for info on setting up your laptop under linux.

EDIT: Just apply to what you learn there for setting up ubuntu.

---

### Post by Pumalite on 2008-06-15
Install your Ubuntu, open up all your repos, including backports, do:
sudo apt-get update
sudo apt-get dist-upgrade
If you still have problems, post back with:
lshw -C sound

---

### Post by jrich1516 on 2008-06-15
Thanks for the help, but that still isn't the problem.  When I tried to install the ALSA sound drivers in openSUSE, the computer crashed, just as it did in WinXP.  I don't think it is a software problem, but merely a hardware problem.  I am almost sure that the integrated sound is broken.  When I find a way to somehow bypass my sound card in the Ubuntu setup and get Ubuntu successfully installed, I will probably buy a usb sound card or something.  Right now I want to get Ubuntu installed, then I will deal with the sound problem.  BTW, this speaker thing isn't new.  It started when I got the laptop used two years ago.  The previous owner sold it because it was old and the sound didn't work.

---

### Post by jrich1516 on 2008-06-19
I hate to double post.  Help please?

---

### Post by avtolle on 2008-06-19
I've looked at the posts here, and offer the following suggestion. Do a minimal install, which hopefully would skip the sound driver part, and build up from there. Otherwise, I have formed the opinion that the apparently broken sound card will be the limiting condition to installing 8.04 on the computer.

EDIT: See [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) for some ideas.

---

### Post by jrich1516 on 2008-06-25
how do you perform a minimal install?

---

