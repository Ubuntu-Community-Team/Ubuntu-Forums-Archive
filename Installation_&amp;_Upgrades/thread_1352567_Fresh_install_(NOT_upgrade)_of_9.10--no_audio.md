---
title: "Fresh install (NOT upgrade) of 9.10--no audio"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Force Flow on 2009-12-11
I installed ubuntu 9.10 on a PC with an Asus A7N8X board, and I'm not getting any audio out of it.  This is NOT an upgrade issue.  This is a fresh installation.  I had windows XP installed before I wiped the drive, so the hardware itself does work.

I'm not an experienced linux user, but from what I can tell, the onboard audio is detected (ie, there is no "dummy audio").

Audio output is at 100%

In "sound preferences" > hardware, an "internal audio" hardware device is listed, which is defaulted to "analog stereo duplex".

In "sound preferences" > output, "internal analog audio stereo" is selected, and defaults to "analog output / amplifier".

When I have an application playing audio, such as VLC, it shows up on the "applications" tab at 100% volume.

Anything else I should check?

Thanks :)

---

### Post by FOSman on 2009-12-11
I can't be much help, but have you checked the [Comprehensive Sound Problem]("http://ubuntuforums.org/showthread.php?t=205449") sticky thread in the Multimedia & Video section?

---

### Post by Alutiiq on 2009-12-11
I'm having a very similar problem after replacing my hard drive. Everything seems to work fine except for the audio, which is rather annoying. I've tried everything listed on other threads regarding the same issue. Don't know why everyone is bashing Windows... looks to me like Linux/Ubuntu have plenty problems of their own. I've tried for a week now to resolve this with no success. It appears that no audio is Ubuntu's glitch. I wonder why so many people still have the problem, and the issue remains a frequent occurrence. So there's my rant. I actually do enjoy Ubuntu, maybe because it's new and a challenge.

Can anyone out there help me get my sound to work?

---

### Post by Force Flow on 2009-12-11
I got to step 4 and loaded the driver indicated here:

[http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Setting_up_modprobe_and_kmod_supporthttp://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Setting_up_modprobe_and_kmod_support](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Setting_up_modprobe_and_kmod_supporthttp://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0#Setting_up_modprobe_and_kmod_support)

But nothing happened when I entered this command:

> sudo modprobe snd-intel8x0

No message in the cmd window, and no magical appearance of audio.

---

### Post by Gene Rodgers on 2009-12-11
Can't be much help, but have you installed a sound mixer such as Gnomealsa-mixer or Kmix? and check you main volume control. For some reason mine was set to mute after installation. I then had sound with every program EXCEPT Amarok. Never could get audio with it. I licked the problem by starting with Xubuntu 8.04 and upgrading up. I also had Amarok with audio playing during each upgrade and each update. Install  the update , then upgrade. I stopped at 9.04 as after 3 upgrades to 9.10. There were too many problems with everything from no way to exit except turning off computer, to applets sticking to top left of screen to 800 x 600 resolution where all the applets were larger than the screen. Good luck! I've installed and upgraded 4 times from scratch to get a well operating system with a little help.

---

### Post by pedja_portugalac on 2009-12-11
Did you tried to unmute everything in alsamixer as well? Type alsamixer in terminal and put everything to maximum, then esc to finish. I had to do the same after fresh install of 9.10 on my acer aspire 8920G laptop.

---

### Post by Force Flow on 2009-12-11
Nothing is muted as far as I can tell.

The main volume is up and unmuted

VLC's volume is up and unmuted

System sounds are up and unmuted

> Can't be much help, but have you installed a sound mixer such as Gnomealsa-mixer or Kmix? 
Why would a sound mixer be necessary if audio's not working to begin with?  I'm getting *no* sound whatsoever.

[edit]:
alsamixer already has everything to the max.

---

### Post by pedja_portugalac on 2009-12-12
Sorry. Did you tried this thread [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

