---
title: "X server hangs on startup (12.04)"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by sword_guy on 2013-10-21
Hello All,

I know, another x server hangs thread.  Well, I did a lot of searching and I can't find anything pointing to this problem (and if you can, I'll be more than happy to read it).

The problem:  Whenever I restart, Ubuntu loads into a command prompt instead of loading the x server (lightdm, I believe).  When I enter the commands to start lightdm, it does a bunch of stuff (the prompt shows a lot of processes starting up) and then just stops.  It is almost completely unresponsive except that ctrl-alt-delete will restart it again.  The only way to get the computer to start up is by reinstalling the Nvidia drivers when it goes to the command prompt.  Every time I start up, I have to do that.  One thing I noticed is that when I reinstall the driver, an error pops up that says "Could not locate module" or something like that.  It's right at the beginning of the installation, and the installer ignores the error and keeps going.

The history:  I had a similar problem once before and reinstalled the Nvidia driver one time and the problem went away.  Then I upgraded to 12.04.  The computer still worked fine.  Then I updated the driver, which fixed one of my problems (emulator issues), but caused a slew of other things to go wrong.  Those have all been fixed, but this one issue still remains.

My specs:  
Ubuntu 12.04 (duh)
Kernel 3.2.0-54 generic pae
GCC 4.6 (i686 linux gnu)
Xorg version 1.11.3
Processor: Pentium E6700 3.2 Ghz
Graphics card (sysinfo says unknown model and card type but lshw shows the following):
Nvidia GTX 550 Ti
Driver: Kernel module 325.15

I assume you'll want a log of some kind, but I don't know which one.  Please help me out on this.  Let me know what you need and I'll post it as soon as possible.

Thanks!

---

### Post by sword_guy on 2013-10-22
I hope it's ok to bump this.  Don't really know the etiquette of that.

---

### Post by mörgæs on 2013-10-23
Bumping is tolerated as a last resort if at least 24 hours have passed. Best advice is to wait 36 hours though in order to reach an audience in other time zones.

For your problem I would suggest a fresh install of 13.10. You have a new graphics card, so old-ish software does not necessarily provide good support.

---

### Post by sword_guy on 2013-10-23
The reason I've been sticking with 12.04 is because it's an LTS release.  Should I upgrade anyway?  What about 12.4.3?  I guess I can try to upgrade.  It just seems like every time I do, more problems arise.  I don't want to do a fresh install because then I'll lose all the programs I've installed over the years.  All the settings.  Unless there's a way around that, I'd really rather not do a fresh install of a newer release.  Do you have any other suggestions?  Any logs you think I could look through to try to find what's going wrong?

---

### Post by steeldriver on 2013-10-23
How are you installing the nvidia driver? are you using Additional Drivers / jockey-gtk / jockey-text? or getting it from elsewhere?

Have you tried Ctrl-Alt-F7 or Ctrl-Alt-F8 when the server startup appears to hang? Have you tried Ctrl-Alt-F1 and then logging in and seeing whether the display server is in fact started?

---

### Post by sword_guy on 2013-10-24
I'm using this command which I got from another forum post: cd /usr/local/bin && wget -Nc smxi.org/sgfxi && chmod +x sgfxi && sgfxi

I *think* I got that from this page: [http://crunchbang.org/forums/viewtopic.php?id=29003](http://crunchbang.org/forums/viewtopic.php?id=29003)

As stated in the first post, this was in order to fix an issue with a badwindow error I was getting when starting certain emulators.  There was a post that said to update the drivers after a new kernel is installed and I thought, "Hey, that's a good idea.  Who wants outdated drivers?"

As far as the Ctrl commands, I think I tried those and nothing happens.  When I get the chance to boot into the command prompt, if I try a regular boot then I can see everything loading.  Loading lightdm fails.  Sometimes it gets to the next line which is something like, "Loading backup in case lightdm fails".  I've seen that once, but it still froze up.  I can't boot failsafeX either.  The only way I ended up getting it to boot this last time was by editing the boot in the grub menu in order to get it to boot to text.

How do I figure out if I have two drivers installed at once?  I just read something about that and I do remember having installed a Nvidia driver from a package a while back.  I'm thinking of trying what's on this page next: [http://askubuntu.com/questions/173721/how-do-i-update-my-nvidia-modules-after-updating-my-kernel](http://askubuntu.com/questions/173721/how-do-i-update-my-nvidia-modules-after-updating-my-kernel)

What do you think?

---

### Post by steeldriver on 2013-10-26
what do these say

```

dpkg -l | grep nvidia

jockey-text --list

```

---

### Post by sword_guy on 2013-11-02
Sorry for the delay.  Here are the results:

user@user:~$ dpkg -l | grep nvidia
ii  nvidia-173-modaliases                                   173.14.28-0ubuntu1                                         Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-71-modaliases                                    71.86.08-0ubuntu1                                          Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                                    96.43.19-0ubuntu1                                          Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-cg-toolkit                                       3.0.0016-0ubuntu1                                          Cg Toolkit - GPU Shader Authoring Language
ii  nvidia-common                                           1:0.2.44.2                                                 Find obsolete NVIDIA drivers


user@user:~$ jockey-text --list
xorg:nvidia_304 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_304_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
xorg:nvidia_319 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_319_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)

---

### Post by steeldriver on 2013-11-02
I'm not an expert on the video side of things but it looks like you currently have none of the proprietary drivers enabled, so presumably your system has fallen back to the open source nouveau driver - or possibly a plain unaccelerated VESA driver. I guess we should check though

```
$ lsmod | grep 'nvidia\|nouveau'
```

(you could also run lshw -C display again, and/or grep /var/log/Xorg.0.log for nouveau and/or nvidia).  If that looks like the case, you could try re-enabling xorg:nvidia_304 or xorg:nvidia_304_updates and then starting lightdm.

---

### Post by sword_guy on 2013-11-03
The output of the first command is this:

nvidia               8439534  39

I gave the second command (the xorg.0.log) a long time to run but nothing ever came up.  It just sat and acted like it was doing something.  I'm going to try to install the proprietary drivers (I thought I had those installed) and see what happens.  I'll post the results.

---

### Post by sword_guy on 2013-11-06
Well, I was forced to restart, so I tried to install the drivers based on the instructions on this page: [http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)

It was a no-go.  The x-server still froze while booting.  I reinstalled the other drivers using the method I originally used just to get the computer running again.  Any more ideas?

---

### Post by sword_guy on 2013-11-14
My computer just restarted properly!  The only thing I can figure is that I installed the proprietary drivers in the software center.  I did that and restarted and things seem to be working now!  If anything changes I'll post, but it's looking good!  Thank you to anyone that tried to help. :)

---

### Post by sword_guy on 2013-11-14
One thing after another with this guy :P

So, my Dolphin emulator wouldn't work after I installed the Nvidia drivers from the software center.  The issue was that openGL wouldn't work (well, the driver wouldn't work with the openGL I had).  Simple solution, install latest driver from Nvidia.  NOT SO SIMPLE!  I had the same problem again (the original problem that started this thread).  Finally, I found a thread with this information:

dkms status

Which yielded this result (paraphrased):

nvidia-319; 3.5-something (kernel); etc.
nvidia-331; (same thing as above)

The reason I did this was because dmesg | less showed at the end of the list:

API mismatch: the Nvidia kernel module has version 331 but this Nvidia driver component has version 319. (Etc. etc.)

So, all I had to do after the dkms status was this command:

sudo apt-get purge nvidia-319 nvidia-319-updates

It ran, it freed 111 MBs, then it finished.  I rebooted and it started completely normally (and even had a slightly different splash screen)!  I hope this information can help someone else out there someday.  I wonder how often this is happening (the module mismatch thing).

---

### Post by sword_guy on 2013-11-14
Oh, and Dolphin works now too.  (Some of you may remember that getting Dolphin to work was what started all this).

---

### Post by mörgæs on 2013-11-15
If it all works then please mark the thread 'solved' using 'thread tools'.

---

