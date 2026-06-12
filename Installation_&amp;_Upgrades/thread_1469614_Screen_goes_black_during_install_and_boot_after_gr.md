---
title: "Screen goes black during install and boot after grub"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by miketirakis on 2010-05-02
Hi, i have a serious problem with my main PC when trying to install ubuntu from wubi.

Ubuntu 10.04 installed perfectly on my netbook, not the netbook remix edition, the desktop edition. No problem whatsoever. Detects all devices, all my other OS, and so far i had no problem. 

When i decided to install on my main desktop PC things gone wrong. I don't have a spare partition, and i decided to go for wubi. But once i rebooted and saw the message, completing install, the screen went black. Monitor entered stand by mode, so the signal from VGA was lost. I left it open to finish installing even with no input from me. When disk activity stopped, i did a hard restart (Hold power button down) and after selecting Ubuntu from windows boot loader i saw grub screen. So i think, everything is fine, and now i can boot normal, maybe the problem was installation screen resolution.

But again, once i select the Ubuntu entry to boot, the screen goes blank and i cant do anything.

I read somewhere that Ubuntu doesn't like 16:9 monitors, and mine happens to be 16:9 aspect ratio in 1920x1080 native resolution. My VGA is Ati 5870. Maybe something of these 2 is the issue? Thats the only things changed from my previous 9.04 and 9.10 installations that worked correctly on a 16:10 monitor and Nvidia 8800GTX VGA.

Any way i can force the correct resolution and boot normally?

I would prefer a way to do it with wubi, but if a normal installation is required on a dedicated partition let me know that this is at least an option.

---

### Post by jplinderman on 2010-05-02
> **miketirakis said:**
> Hi, i have a serious problem with my main PC when trying to install ubuntu from wubi.

Ubuntu 10.04 installed perfectly on my netbook, not the netbook remix edition, the desktop edition. No problem whatsoever. Detects all devices, all my other OS, and so far i had no problem. 

When i decided to install on my main desktop PC things gone wrong. I don't have a spare partition, and i decided to go for wubi. But once i rebooted and saw the message, completing install, the screen went black. Monitor entered stand by mode, so the signal from VGA was lost. I left it open to finish installing even with no input from me. When disk activity stopped, i did a hard restart (Hold power button down) and after selecting Ubuntu from windows boot loader i saw grub screen. So i think, everything is fine, and now i can boot normal, maybe the problem was installation screen resolution.

But again, once i select the Ubuntu entry to boot, the screen goes blank and i cant do anything.

I read somewhere that Ubuntu doesn't like 16:9 monitors, and mine happens to be 16:9 aspect ratio in 1920x1080 native resolution. My VGA is Ati 5870. Maybe something of these 2 is the issue? Thats the only things changed from my previous 9.04 and 9.10 installations that worked correctly on a 16:10 monitor and Nvidia 8800GTX VGA.

Any way i can force the correct resolution and boot normally?

I would prefer a way to do it with wubi, but if a normal installation is required on a dedicated partition let me know that this is at least an option.

Did you hear the ubuntu login "music" even though the screen was dead?  If so, you may be having trouble with the default nvidia drivers, like I was having.  I couldn't get my DVI or HDMI connections to keep signal after the grub boot, but I was able to connect an old VGA card and get a window through the VGA port.  After that, after logging in as root, I was able to install the non-standard nvidia drivers with

System > Administration > Hardware drivers

After installation and a reboot, the DVI port was fine again.

Note: you have to install the drivers as root, so log in as root,
don't just do a sudo.  You can set the root password to a known value using

sudo passwd root

--jpl

---

### Post by miketirakis on 2010-05-02
The truth is that the login sound did not play.

I though trying with a different monitor on second port, but my 5870, has only 2 DVI slots, 1 hdmi, and 1 mini display port. 

i have an older 7300gs nvidia card, but if i boot with that one the hardware drivers promt wont install the nvidia drivers? And if i try to manually install the catalyst drivers from ati website will they complete even if the hardware is not present?

---

### Post by emacs on 2010-05-02
I would like to share how I was able to solve a similar
"blank screen" problem.

I upgraded from 9.10 to 10.4 over the weekend on my Dell laptop 
with nvidia Quadro NVS 135M video.  When booting up I can
see the splash screen with purple background with white "ubuntu"
letters and five dots whose color switched between white and red.
After about 25 seconds of this, the screen goes blank and nothing
seems to work such as Control-Alt-Delete Control-Alt-Backspace.  Even
the virtual consoles (reachable via Control-Alt-F1, Control-Alt-F2,
etc) were all messed up with very colorful characters showing
lots of letters, numbers, and other graphics characters.

First I upgraded my bios, because I had to do this before a year or
two ago.  This did not help.

Second I followed grub tweak that I read in this forum where you

- Hit 'e' at grub prompt
- Go to second from last line that had "quiet splash" and replace
  these letters with "nomodset".

This did not help either.

I also tried to install the proprietary driver from nvidia.com
after finding an article in this forum.  However it failed to
install saying something like nvidia.so or some module could not be
found. I'm glad this failed, because of the following quote from
[https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching)

    nvidia's drivers do not (yet) honor the alternatives system. For
    this reason installation of them would cause your system to get
    into a horribly inconsistent state.

I could, however, boot the recovery kernel, i.e., the second item 
in the list of kernels that grub shows at boot up.  I could bring
X up in fail-safe-x mode.  I tried removing the nvidia driver by
typing

   sudo apt-get remove xserver-xorg-video-nv

Upon rebooting, X came up fine.  I think my system was now using
default X driver rather than accelerated one for nvidia.
Then I installed nouveau alternative driver following these
instructions that I found at the same url I mentioned earlier:

  sudo nvidia-settings --uninstall
  sudo apt-get remove --purge 'nvidia*'
  sudo apt-get remove --purge xserver-xorg-video-nv xserver-xorg-video-nouveau
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

Note that I tweaked one line to add quotes around nvidia*.
Upon rebooting, X came up fine!  So I tried to see if the accelerated
features were working by

  Select System->Preferences->Appearance menu
  Select "Visual Effects" tab.
  Click the third item labeled "Extra".

In response I was shown a dialog box that said that a restricted driver
needed to be downloaded.  I was not paying close attention (having
seen such dialogs before)  so I don't
know what the exact wording was.  After I clicked OK, it took a
while downloading and installing something.

Upon reboot the effects seem to work.  I can get the rotating cubes
effect to work for example after I turned it on with CompizConfig
Settings Manager.

In summary it took some trying, but my laptop now has accelerated
graphics working.  Obviously there is much to improve regarding nvidia support.

I hope this helps.

---

### Post by miketirakis on 2010-05-02
I am exactly at the state you describe, nothing working, not even Control-Alt-Backspace or the virtual consoles. But since i am not upgrading i don't have any drivers to remove. So basically my best option is to boot with my older vga, nvidia 7300gs, and not use the hardware drivers utility because it will install nvidia drivers but i need my main card to work wich is an Ati 5870, but instead do a manual install of the drivers from ati site.

Hope this will work, although i would prefer to use the built in utility to install, because i had some problems before with installers for linux, they seem to be very poor and run in all sorts of problems.

---

### Post by Covarrubias on 2010-05-02
Exactly the same here I have an ATI 5770 and my monitor its 1920x1080 and starting with LiveCD x64 and after orange dots I have a black screen and can´t do anithing. I think it´s a display driver or monitor detection problem but I don´t know what to do. I know other people with Nvidia have similar problems but mine it´s an ATI.

Some help would be apreciated.

---

### Post by Spliff85555 on 2010-05-07
Same thing here, but with NVIDIA 9600M.

To eliminate a graphics driver isuee I uninstalled every graphics driver and get 

a black screen running
kernel 2.6.32-22-generic
kernel 2.6.32-22-generic recovery mode
kernel 2.6.32-21-generic
kernel 2.6.32-21-generic recovery mode

a default resolution running
kernel 2.6.31-20-generic
kernel 2.6.31-20-generic recovery mode

Unfortuantely I can't install the nvidia driver for the old kernel due to missing source headers.

What is broken in the newer kernels?
How do I get it working again?

- Spliff

---

### Post by miketirakis on 2010-05-07
So basically both ATI and Nvidia card have the same issue? Whats wrong? I always admired ubuntu ability to identify almost every piece of hardware on my PC, and previous versions worked with my Nvidia 8800 GTX, and and older Ati card.

What changed now? :(

---

### Post by frantid on 2010-05-07
there's a  known issues thread.  you guys may want to look through the whole thread.  But this post is about ati:

[http://ubuntuforums.org/showpost.php?p=9228124&postcount=14](http://ubuntuforums.org/showpost.php?p=9228124&postcount=14)

---

### Post by miketirakis on 2010-05-07
> **frantid said:**
> there's a  known issues thread.  you guys may want to look through the whole thread.  But this post is about ati:

[http://ubuntuforums.org/showpost.php?p=9228124&postcount=14](http://ubuntuforums.org/showpost.php?p=9228124&postcount=14)

The single post you linked, is a workaround to slow minimize and maximizing windows. That means that you can see the windows, and your desktop, but they are slow. I created a new thread for a complete different reason. I can't see the desktop at all! Not during install, not even after the selecting the grub entry and waiting to boot to desktop. I read the rest posts of the thread but not helpful on my issue.

---

### Post by frantid on 2010-05-07
ok, thought I had read something about it.

Did you try switching dvi ports?  I know in the beta there were problems with hdmi.

---

### Post by frantid on 2010-05-07
here's the thread I was originally thinking of...

[http://ubuntuforums.org/showpost.php?p=9200710&postcount=17](http://ubuntuforums.org/showpost.php?p=9200710&postcount=17)

the thread has more comments,

good luck.

---

### Post by miketirakis on 2010-05-07
> **frantid said:**
> ok, thought I had read something about it.

Did you try switching dvi ports?  I know in the beta there were problems with hdmi.

I am already using DVI connection to my monitor, and tried on the second dvi to use a second monitor, no luck. Didn't try hdmi at all, don't have hdmi cable.

---

