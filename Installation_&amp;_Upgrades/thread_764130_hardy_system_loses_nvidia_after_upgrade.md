---
title: "hardy system loses nvidia after upgrade"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by newore on 2008-04-23
my 8.04 ubuntu (windows file system version) rebooted this morning
only able to use low resolution mode. I have a toshiba satellite pro
with nvidia and had used the drivers. 

perhaps the upgrade of 4/22 to gnome ate my setup, i can only boot
in low resolution mode. I have been installing upgrades and show
that the system is current, today.

what is the best way to proceed?

---

### Post by Pumalite on 2008-04-23
Reinstall your driver.

---

### Post by newore on 2008-04-23
easy to say, but none of the "unsupported driver" cruft is evident.
perhaps you can give me a pointer to the location. 

at least when the system was newly installed, it gave some icons linked
to the driver installation. 

the most awkward ubuntu integration experience for me, so far.

---

### Post by newore on 2008-04-23
ok, so i reinstalled nvidia-glx-new. using synaptic.

also looks like there is a 71 file upgrade list today. I'll check back
after doing the upgrade, reinstallation.

---

### Post by myfigurefemale on 2008-04-23
if you need to re-install the driver try using envy
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by newore on 2008-04-23
well...

reinstallation 

and installing todays (4/23) upgrades did not change the situation.

after a reboot from the upgrade notice, still low res.

the system appears to try three times in the local scripts phase
of the boot.

I'll try and see what's up with "envy", now.

thanks for the suggestions.

---

### Post by Pumalite on 2008-04-23
I'd recommend a clean install.

---

### Post by newore on 2008-04-23
reboot after installing envy-ng using synaptic.

still coming up in low res mode, after three tries in the
local scripts...

maybe something changed with hardware detection?

---

### Post by newore on 2008-04-23
> **Pumalite said:**
> I'd recommend a clean install.


re-install of what? entire hardy?

sub-component, or driver?


is there a likely place in bug reports for hardy?

I'm not sure how to categorize what's not working, exactly.

---

### Post by Pumalite on 2008-04-23
Hardy.

---

### Post by newore on 2008-04-23
I guess that's one way to troubleshoot.

I think I'll poke around in the guts, a little bit.

my model of community software says that this SNAFU
shouldn't happen.

an upgrade should be able to check drivers (even the presence
of an 'unsupported" driver) and give the user some warning, 
or information, that allows a rational choice.

---

### Post by firmit on 2008-04-23
Have you checked launchpad.net/ubuntu for related bug-reports? There has been several bugs related to nvidia during a kernel-update not too long ago.

---

### Post by Pumalite on 2008-04-23
To make an upgrade successful some conditions have to be met, and sometimes they are not.

---

### Post by newore on 2008-04-23
think I'll check out xorg after seeing this..
Bug #173418 in xorg (Ubuntu)
[Hardy] NVIDIA cards using vesa driver and low screen resolutions on livecd




bob@bob-laptop:~$ lspci -nn |grep VGA
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce Go 7900 GS [10de:0298] (rev a1)

---

### Post by newore on 2008-04-23
well, it seems the xorg bug was fixed.

checking now on linux-restricted-modules version for the generic
kernel.

---

### Post by newore on 2008-04-23
got back to high resolution by using:

sudo jockey-gtk

and then removing the new generation driver

obviously, no effects, feh

still checking...

reinstalling the glx driver drops in to low
resolution.

problem driver is nvidia-glx-new

---

### Post by newore on 2008-04-23
submitted bug report;

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/221239](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/221239)

---

### Post by tyblu on 2008-04-23
these may be helpful

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=(nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=(nvidia))

[https://help.ubuntu.com/community/BuildYourOwnNvidiaGlx?highlight=(nvidia](https://help.ubuntu.com/community/BuildYourOwnNvidiaGlx?highlight=(nvidia))

[https://help.ubuntu.com/community/NvidiaManual?highlight=(nvidia](https://help.ubuntu.com/community/NvidiaManual?highlight=(nvidia))

---

### Post by wannjanjic on 2008-04-23
I was having a same problem after upgrading form Feisty and this is how I solved it:
```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`
```
Hope this helps ;)

---

### Post by walter_j on 2008-04-24
I exp the same problem i managed to get the proper resolution by editing /etc/X11/xorg.conf. My monitor wasn't properly set up. it was set for plug n play. when i changed it to the proper monitor, i got the high res, although i cannot get the special effects of nvidia to work, and therefore no compiz effects. envy didn't work either.

---

### Post by tautnubu on 2008-04-24
My update manager asked me if I wanted to update about 100 things. I said yes without reading in details through the list. However this update included a new kernel which is not compatible with my nvidia driver.
My panels and the main menu disappeared. 

Then I moved back to the previous kernel. In the file  /boot/grub/menu.lst
I saw the previous kernel was the third in the list of available kernels.
so I set the default to read the third one by changing "default 0" to "default 2"

Then it went back to the old kernel and all is well again. I think in a  few days I will update my nvidia drivers again, and use the latest kernel again.

---

### Post by mgmiller on 2008-04-24
I have noticed that all the Hardy live CD's right up through the release candidate, would not properly detect my Nvidia 7800GT or Viewsonic 22" widescreen monotor.  I would end up with 800x600 really ugly.  ](*,)

The fix is to right click Applications and select Edit Menu.
Then go to the Other section and put a check mark next to the Monitor and Video card applet.( It's called something like that, I'm doing this from memory on a Gutsy install).  

Once that's in, go to Applications > Other > Monitor and Video card applet (or whatever it's called).

In there, you can select your monitor by name or I found generic LCD worked fine with 60 Hz refresh, make sure the "Wide Screen" check box is checked if you have a wide screen monitor.

Next, go to the video card tab and select the correct driver for your card.

Click on the test button and if it's OK, just accept everything and you're done.

This has worked for me on all Hardy Live CD's since the Alpha's.

I don't know why it fails to properly detect my Nvidia card and monitor, Gutsy had no problems with them.

---

### Post by falkaholic on 2008-04-24
> **wannjanjic said:**
> I was having a same problem after upgrading form Feisty and this is how I solved it:
```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-new linux-restricted-modules-`uname -r`
```
Hope this helps ;)


The last command in this dies on me.

```
Package linux-restricted-modules-2.6.22-14-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

Not sure what the best way out of this is.

It also looks like the System->Hardware Drivers is now empty. It doesnt list my video card anymore. Is the driver in the kernel now?

---

### Post by biriachan on 2008-04-24
I've had some problems with the beta 8.04 after upgrading the Kernel.  Resolution dropped to 800x600.  I was able to get it fixed by rebooting, Pressing ESC during the GRUB bootup and selecting recovery, and then selecting "xfix Try to Fix X Server".

---

### Post by mosestruong on 2008-04-24
It seems like you're still using the kernel from gutsy - hardy uses 2.6.24 version

---

### Post by falkaholic on 2008-04-24
> **mosestruong said:**
> It seems like you're still using the kernel from gutsy - hardy uses 2.6.24 version


Looks like that was the problem. The kernel was old. I should have noticed that. AFter updating that, and a little more tinkering, i'm back up and going.

thanks.

---

### Post by gtdaqua on 2008-04-24
NVIDIA Drivers have to be recompiled every time the kernel is upgraded.

Here is one guide I prepared for Gutsy. No reason why it shudnt work on Hardy. This works for me.

[http://ubuntuforums.org/showthread.php?t=596875]("http://ubuntuforums.org/showthread.php?t=596875")

Ignore the title of the thread.

---

### Post by oribi on 2008-06-24
After trying various things described in this and other threads, I decided to experiment (noob-style). It seems that the new kernel has a problem automagically identifying the native resolution.

This is what I did:

[LIST=1]
[*]Install the newest driver using EnvyNG

[*]Open the terminal and type:
  ```
sudo gedit /etc/X11/xorg.conf
```
[*]Inside the first 'Section', look for the line 'Virtual' and change the values to your preferred (supported) screen res.
(mine was set to '640   480', I changed it to '1280   800')

[*]Save -> Close -> Restart
[/LIST]

I'm not sure which side effects this has except for an oversized nVidia splash at startup. Everything seems to work fine, even Compiz.

My setup:
Ubuntu 8.04, kernel 2.6.24-19-generic
HP dv 6000 laptop
GeForce Go 7400

---

