---
title: "[SOLVED] Xorg with Nvidia"
date: 2008-12-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chrismine on 2008-12-17
I have a broken X - totally my own fault.

I am trying to remove nvidia-glx-177 so as to install xorg to at least have a desktop.

Nvidia defies all attempts with a dpkg-divert error - /usr/lib/xorg/modules/extensions/libGLcore.so no such file or directory.

I have tried to reinstall nvidia - rm the directory

The nvidia driver blocks the install of xorg.

Xfix is not available in recovery console and fix broken packages goes into a loop.

Any help will be appreciated or shall I just do apt-get update and upgrade twice daily from the recovery console and hope it solves itself?

Thanks - hopefully Alberto will appear to save me from my misery!

---

### Post by jfernyhough on 2008-12-17
Off the top of my head, three possible approaches:

1) $ sudo touch /usr/lib/xorg/modules/extensions/libGLcore.so to create a file so it can be removed.
2) Reinstall nvidia-glx-177 and allow the xorg upgrade to remove it.
3) Install the drivers from nvidia.com. This will put the necessary files in place, but has the potential to completely bork the drivers.

---

### Post by chrismine on 2008-12-17
Thanks for the reply

1. Not working - no such file or directory
2. Tried that already.
3. Alberto had to rescue me from that option in July 2008 - I am too "stupid" to do that from the recovery console - how do I get he package on the machine if I D/L it from another machine and copy it to that machine?

Thank you for the suggestions.

---

### Post by dinxter on 2008-12-17
looks like the nvidia removal is trying to relink to xorgs version of libGL, which is missing because (im guessing) large chunks of xorg have been ripped out by the recent upgrades. try to
recreate a fake xorg extension directory by,

sudo mkdir -p /usr/lib/xorg/modules/extensions/

then follow [jfernyhough]("http://ubuntuforums.org/member.php?u=143103") intructions by touch-ing the missing file,

 sudo touch /usr/lib/xorg/modules/extensions/libGLcore.so

then you should be able to remove  nvidia-glx-177 and then,

sudo apt-get install xorg

---

### Post by chrismine on 2008-12-17
Brilliant! Shall I install nvidia-glx-180 to see if I can bugger up the system again?

Hopefully you guys will save my bacon again!

---

### Post by dinxter on 2008-12-17
dont try to install nvidia-glx-180 from the repositories, it will purge most of xorg. the only way to get the 180 driver working at the moment is to use nvidia's installer and tweak xorg to ignore ABI checks. see [http://ubuntuforums.org/showpost.php?p=6378516&postcount=25](http://ubuntuforums.org/showpost.php?p=6378516&postcount=25)

---

### Post by chrismine on 2008-12-17
Thanks I am not all that adventurous - maybe I should try to install nvidia-glx-177 again?

---

### Post by dinxter on 2008-12-17
same problem, it will try and remove most of xorg. the nvidia installer is the only way at this time sorry

---

### Post by paul_in_london on 2008-12-31
Hi,

Been using Ubuntu for a few months now, but haven't posted here before. 

This is what worked for me originally (and again now after I borked my Jaunty installation yesterday, but that's another story).

No need to use the Nvidia installer. Install 180.18 from this ppa:

[I][https://launchpad.net/~anders-kaseorg/+archive](https://launchpad.net/~anders-kaseorg/+archive)
[/I]
Update your apt sources list with these entries:

[I]deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main[/I]

Then do:

[I]sudo aptitude install nvidia-180-kernel-source
sudo aptitude install nvidia-180-modaliases[/I]

Aptitude doesn't say it's going to remove xorg or anything.

180.18 and related stuff should then be installed.

Finally, add this to your xorg.conf:

[I]Section "ServerFlags"
Option "IgnoreABI" "True"
EndSectio[/I]n

Reboot and you should be good to go.

Jockey (Hardware Drivers) won't show anything, but NVIDIA X Server Settings should show 180.18.

HTH

Paul

---

### Post by Bachstelze on 2009-01-01
> **paul_in_london said:**
> Then do:

[I]sudo aptitude install nvidia-180-kernel-source
sudo aptitude install nvidia-180-modaliases
**sudo apt-get install nvidia-glx-180**[/I]

Fixed ;)

---

### Post by chrismine on 2009-01-01
Thank you it worked! A Happy New Year to everybody!

---

### Post by PRGUY85 on 2009-01-01
> **paul_in_london said:**
> Hi,

Been using Ubuntu for a few months now, but haven't posted here before. 

This is what worked for me originally (and again now after I borked my Jaunty installation yesterday, but that's another story).

No need to use the Nvidia installer. Install 180.18 from this ppa:

[I][https://launchpad.net/~anders-kaseorg/+archive](https://launchpad.net/~anders-kaseorg/+archive)
[/I]
Update your apt sources list with these entries:

[I]deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main[/I]

Then do:

[I]sudo aptitude install nvidia-180-kernel-source
sudo aptitude install nvidia-180-modaliases[/I]

Aptitude doesn't say it's going to remove xorg or anything.

180.18 and related stuff should then be installed.

Finally, add this to your xorg.conf:

[I]Section "ServerFlags"
Option "IgnoreABI" "True"
EndSectio[/I]n

Reboot and you should be good to go.

Jockey (Hardware Drivers) won't show anything, but NVIDIA X Server Settings should show 180.18.

HTH

Paul

Will this cause conflict when Ubuntu fix their end of things with respect to Nvidia drivers?

---

### Post by autocrosser on 2009-01-02
No-a PPA driver will just "blend" in with the numbering structure that we use----Of course if there is a problem, all you have to do is uninstall the PPA driver first & then install the "stock" driver.....then restart X.

---

### Post by sirjasonr on 2009-01-02
I just successfully installed the nvidia-glx-180 drivers as per all of the helpful directions posted in this thread. The only issue that I'm having now is that when using two screens running in the "Seperate X screen" mode (as opposed to TwinView), if I move the mouse over into the second screen, the X server crashes, restarts and takes me back to the GDM login screen. Any solutions/hints as to how to debug this?

---

### Post by plun on 2009-01-02
> **sirjasonr said:**
> I just successfully installed the nvidia-glx-180 drivers as per all of the helpful directions posted in this thread. The only issue that I'm having now is that when using two screens running in the "Seperate X screen" mode (as opposed to TwinView), if I move the mouse over into the second screen, the X server crashes, restarts and takes me back to the GDM login screen. Any solutions/hints as to how to debug this?

"Bleeding edge"...

You probably needs a nVidia bug report, please take a look at this URL

[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

**The tty terminal** is also **probably broken** for you but with a _nosplash boot_ tty works

Ctrl-Alt-F1 from login screen

Login tty

```
sudo /etc/init.d/gdm stop

startx -- -logverbose 6
```


>>>>>  se URL....


nVidias manual:
[ftp://download.nvidia.com/XFree86/Linux-x86/180.16/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/README/index.html)

---

### Post by sirjasonr on 2009-01-02
Thanks for your reply :)

I have generated the nvidia bug report log file and will submit this as a new bug to nVidia.
As a workaround, to anyone experienceing similar issues, setting to TwinView instead of Seperate X server works fine.

---

### Post by quaa on 2009-02-08
using the repo from - [https://launchpad.net/~anders-kaseorg/+archive](https://launchpad.net/~anders-kaseorg/+archive)

when installing that package does it automatically install nvidia-180-libvdpau ?

I am wondering because i believe my card does not support vdapu and that would cause everything to go bad!

I have a 7600GT btw.
thank you!


i am wondering because i need to update my mythtv to the newest weekly and libmyth requires nvidia-180-22 or better

---

### Post by ronacc on 2009-02-08
I just checked and it did on my sys , but it don't seem to be causing my 7600gs any problems . do note though that right at the moment there is another problem with x and nvidia that needs a little workaround , see this thread    [http://ubuntuforums.org/showthread.php?t=1061919](http://ubuntuforums.org/showthread.php?t=1061919)

---

