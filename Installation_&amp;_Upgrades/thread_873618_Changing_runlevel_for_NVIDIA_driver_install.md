---
title: "Changing runlevel for NVIDIA driver install?"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by delta_charlie on 2008-07-29
Hi all, I have a fresh install of Hardy. Want to try and fix a strange video display problem that I have. At intermittent times the display will jump (almost like the power switch was turned off for a fraction of a second) Some times this happens one or two times in a row a few seconds apart then not again for 10 min or so.

I'm thinking it might have something to do with the video driver. I have only the open NVIDIA driver that was installed by default.

Note - I did try the restricted driver before the current install but it did not help with the problem. Decided I wanted to make a dual boot computer so I re-installed Hardy with the default open driver.

Thinking it might help to install the closed driver direct from NVIDIA I downloaded: 

NVIDIA-Linux-x86-173.14.05-pkg1.run

When I try to install it I get a warning to close X and change to runlevel 3

After running some google searches I read I'm suppose to edit /ect/inittab but I do not have that file in that location. So my question is on Hardy how do I change the runlevel and keep the computer at the command prompt. I tried changing it from a terminal window then killed the X server but it boots back to X. I need to set it to boot into the command prompt and runlevel 3.

More info that might help: the other OS is XP Pro and I have no problems with the video when running XP.

The motherboard is a PGMGM-FD

Thanks for any help, DC

---

### Post by PmDematagoda on 2008-07-29
Changing the run level is not necessary, just running the Nvidia in the current run level should work properly. But you do need to kill the X-Server(GUI), this can be done by:-
```
sudo /etc/init.d/gdm stop
```
after doing this you will be dropped to a CLI where you will have to use commands. After you are done installing the Nvidia driver, start X again with:-
```
sudo /etc/init.d/gdm start
```

---

### Post by logos34 on 2008-07-29
I just tried tried to install the x64 version of that very same driver and after successfully completing the  module build it complains about 'libnvidia-tls-so.1' not being in the right folder--but it's the one that put it there!  I've uninstalled and reinstalled, removed the offending files, and it just puts them right back and complains about afterwards...

Any ideas?  I have no other apps using the OpenGL stuff I know of...Never had this prob in past (although it has been a very long time since I installed theproperietary nvidia driver manually. )

---

### Post by PmDematagoda on 2008-07-29
> **logos34 said:**
> I just tried tried to install the x64 version of that very same driver and after successfully completing the  module build it complains about 'libnvidia-tls-so.1' not being in the right folder--but it's the one that put it there!  I've uninstalled and reinstalled, removed the offending files, and it just puts them right back and complains about afterwards...

Any ideas?  I have no other apps using the OpenGL stuff I know of...Never had this prob in past (although it has been a very long time since I installed theproperietary nvidia driver manually. )

Can you post the log created by the Nvidia installer?

---

### Post by logos34 on 2008-07-30
> **PmDematagoda said:**
> Can you post the log created by the Nvidia installer?

yeah, here it is (I posted it in another [thread here]("http://ubuntuforums.org/showthread.php?t=873790"), but not much of a response):

> [COLOR=Green][ 1226.068812] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.05 
   Mon May 19 00:03:22 PDT 2008
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility OpenGL libraries? (Answer: **Yes**)
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64'
   (173.14.05):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:[/COLOR]
[COLOR=Red]ERROR: The runtime configuration check failed for the library
      'libnvidia-tls.so.173.14.05' (expected:
       '/usr/lib32/tls/libnvidia-tls.so.1', found:
       '/usr/lib32/libnvidia-tls.so.1').  The most likely reason for this is
       that conflicting OpenGL libraries are installed in a location not
       inspected by `nvidia-installer`.  Please be sure you have uninstalled
       any third-party OpenGL and/or third-party graphics driver packages.
-> done.
-> Runtime sanity check failed.
ERROR: Installation has failed. [/COLOR] Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com/"). 			 		


It's killing me, I'm so close yet so far away.  It seems to be able to build the kernel module just fine...I do 'sudo sh NVIDIA....run --kernel-source-path=/usr/src/linux-headers-2.6.24-19-rt' and it goes thru the whole deal until it comes to the part about 32-bit compatibility OpenGL libraries...Whether I say yes or no it fouls up the last stage...I even went back and deleted the 'libnvidia-tls-so.1' and 'libnvidia-tls-173...so.1' files in /usr/lib and /usr/lib32, leaving just those in the tls/ subfolder, but no go.

It tried the nvidia 173.14.09 driver (same release used by EnvyNG), which even has preliminary support for 2.6.26 kernel, as well as the latest beta 177.-  version, but I can't get those to even start the kernel module build, they fail right away.  

it's too bad because if I can't get the official driver to work, I can't move to a custom compiled kernel--my ultimate object in all of this.

---

### Post by PmDematagoda on 2008-07-30
I see that you've created similar threads on this logos34, so shall we just keep the problem to that thread only without going/creating other threads?

Thanks:).

---

### Post by logos34 on 2008-07-30
yeah, sorry, i'm flirting with double posting...But my kernel compile and nvidia driver installation are interrelated, and you and galleon and VOR have so many helpful insights :)

---

### Post by delta_charlie on 2008-07-30
> **PmDematagoda said:**
> Changing the run level is not necessary, just running the Nvidia in the current run level should work properly. But you do need to kill the X-Server(GUI), this can be done by:-
```
sudo /etc/init.d/gdm stop
```
after doing this you will be dropped to a CLI where you will have to use commands. After you are done installing the Nvidia driver, start X again with:-
```
sudo /etc/init.d/gdm start
```

Hi, I just tried running the command above but I did not get a command line. Just some text - can't remember what it said.

I need to disable the auto start direct into x and I can't figure out how to do this with Hardy. What files do I need to edit to cause the computer to boot direct into the command line without starting x.

Thanks, DC

---

### Post by logos34 on 2008-07-30
> **delta_charlie said:**
> Hi, I just tried running the command above but I did not get a command line. Just some text - can't remember what it said.

ctrl+alt+F1

login at prompt

then run gdm stop command

To restart X:

...gdm start

ctrl+alt+F7

---

### Post by delta_charlie on 2008-07-31
> **logos34 said:**
> ctrl+alt+F1

login at prompt

then run gdm stop command

To restart X:

...gdm start

ctrl+alt+F7

Thanks for the info. I had forgotten about the virtual terminals. I think I must have killed x then did not change to one of the virtual terminals and that is way I did not see the command line prompt.

I will try it in a few minuets.

Take care, DC

---

