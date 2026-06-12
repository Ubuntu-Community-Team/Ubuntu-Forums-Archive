---
title: "Video bios not available - after install of NVIDIA drivers on 12.10"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by wshaffer79 on 2012-12-20
Hello,
 
I recently installed Ubuntu 12.10 (separately as an upgrade, and as a fresh install) and installed the NVIDIA proprietary drivers. I tried installing the drivers both from a download off nvidia.com, and through the "system settings" applet in the "additional drivers" tab. When I reboot the system, the standard BIOS POST tests occur as usual, and the screen goes blank and displays a message: xgifb: video bios not available. The system does not appear to boot any further after this. Has anyone seen this issue?

---

### Post by wshaffer79 on 2013-01-22
Anyone?

I'm still having trouble with this.  There is some discussion about this issue on another thread I created about a different but related topic here:  [http://ubuntuforums.org/showthread.php?t=2105190](http://ubuntuforums.org/showthread.php?t=2105190)

Somewhat long story short:  I am running Ubuntu 12.10, which came with the nouveau drivers.  I attempted to install proprietary NVIDIA drivers from both "Additional Drivers" (I believe it's called Jockey?), and from nvidia.com for my two NVIDIA Quaddro NVS 290 cards.  Regardless of which method I use to install, when I reboot, I get a "xgifb: video BIOS not available" error message right after grub loads and the OS will not boot at all.

I can boot off a LiveCD, so I did that, chrooted into the installed OS, and made several attempts to disable nouveau and install the NVIDIA drivers manually.  I can't seem to get rid of this error message.

For now, I'm running off LiveCD, with a terminal opened and chrooted.  Not the most ideal situation.

Any ideas?

---

### Post by Bobhuber on 2013-01-22
> **wshaffer79 said:**
> Anyone?

I'm still having trouble with this.  There is some discussion about this issue on another thread I created about a different but related topic here:  [http://ubuntuforums.org/showthread.php?t=2105190](http://ubuntuforums.org/showthread.php?t=2105190)

Somewhat long story short:  I am running Ubuntu 12.10, which came with the nouveau drivers.  I attempted to install proprietary NVIDIA drivers from both "Additional Drivers" (I believe it's called Jockey?), and from nvidia.com for my two NVIDIA Quaddro NVS 290 cards.  Regardless of which method I use to install, when I reboot, I get a "xgifb: video BIOS not available" error message right after grub loads and the OS will not boot at all.

I can boot off a LiveCD, so I did that, chrooted into the installed OS, and made several attempts to disable nouveau and install the NVIDIA drivers manually.  I can't seem to get rid of this error message.

For now, I'm running off LiveCD, with a terminal opened and chrooted.  Not the most ideal situation.

Any ideas?
Read known bugs sticky under general help.

---

### Post by bogan on 2013-01-23
Hi!, **Bobhuber**,

You Posted: > Read known bugs sticky under general help.If you know of a relevant Post please give us a more detailed Link.

I have just searched both the general help forum and the 'known bugs' thread and nothing of any use came up.

**@wschaffer79**,

Was : "xgifb: video bios not available." the whole of the error message ?? or did it indicate where the origin or backlist was?

Edit: Does it make any difference if you press 'Shift' as the Bios Post test ends ??

Chao!, **bogan,**

---

### Post by wshaffer79 on 2013-01-23
> Read known bugs sticky under general help. 
 
That was helpful...
 
**bogan**,
 
The full error message is as follows:
 
***[     9.613425] xgifb 0000:20:05.0: video BIOS not available***
 
Nothing else is displayed on the screen.  The numbers in brackets at the beginning do change slightly at each reboot.  At this point, the system is completely unresponsive to ctrl-alt-delete, ctrl-alt-F1, F2, F3.... anything.
 
No need for 'SHIFT' because the grub boot menu displays automatically every time.  The menu gives me the standard 'Ubuntu' option as well as 'advanced' with a choice of two kernels.  Booting any of these selections results in the above error message.
 
Out of curiousity, I rebooted with a LiveCD, chrooted to the installed OS, and uninstalled nouveau (sudo apt-get --purge remove xserver-xorg-video-nouveau) and rebooted.  Still getting the above error.

---

### Post by wshaffer79 on 2013-01-30
Bump.  Anyone?  I am wondering if this is an issue just related to Ubuntu, or if other distributions experience this as well.  I had all four monitors working on this system on Ubuntu 11.x, but that version is no longer supported.

---

### Post by oldfred on 2013-01-30
Mixing installs often leads to issues, may be best to totally houseclean all nvidia and reinstall. I do not know if dual cards requires anything else or not. You may want the newest (experimental) version Ubuntu offers.

       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot

If still issues run these to see if system is seeing your nVidia correctly.
       To see nVidia info:
uname -ar
lspci -nnk | grep -iA3 vga 
sudo apt-cache policy nvidia-current 
cat /sys/module/nvidia/version 
/usr/lib/nux/unity_support_test -p
nvidia-settings --vv

   #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

---

### Post by bogan on 2013-01-31
Hi!, **oldfred**,

=1 for your comprehensive trouble-shooter list.

A few minor points:
(1)
I have found that following nvidia driver problems that involve more than one version being installed, - especially if 'kernal mismatch' errors show, - it is better to run: ```
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge  nvidia* 
``` To ensure **all **old components are purged.

This arose due to real bad trouble after using: nvidia-current   304.51-actually-304.43.

The 304.43 components got left behind after purging 'nvidia*'.

(2)
Running 'xw**[COLOR=Red]in[/COLOR]**fo' gave  me the following:```
alan@alan-MS-7616:~$ xwinfo-root
xwinfo-root: command not found
alan@alan-MS-7616:~$ xwinfo -root
No command 'xwinfo' found, did you mean:
 Command 'hwinfo' from package 'hwinfo' (universe)
 Command 'xvinfo' from package 'x11-utils' (main)
 Command 'xjinfo' from package 'xjadeo' (multiverse)
xwinfo: command not found
alan@alan-MS-7616:~$ 
```Edit: My error, - 'xw**[COLOR=Red]inin[/COLOR]**fo  -root', on the last line, gives: ```
"geometry 1920x1080=0+0"
```Chao!,** boga**n.

---

### Post by oldfred on 2013-01-31
@bogan
Thanks for the update. 

Over the years I have had more issues with nVidia's direct download and now just install the default from Ubuntu. 
Many, many versions ago I had to wait for nVidia to come up with a script to in-install its own version, so I stopped using any direct downloads. But now my video card is older and does not need all the bells & whistles of the very newest versions that some may need.

---

### Post by bogan on 2013-01-31
Hi!,** oldfred**,

Strangely, my experience has been the exact reverse: almost no problems using nvidia,com downloads - apart from the bug-ridden 295.40, which also infected nvidia-current - other than having to reinstall it after most kernal updates, prior to 304.14.

But lots of problems with nvidia-current, nvidia-updates & experimental-xxx, especially with low-res resolution after updates, and with those from x-swat ppa.

Though I must admit there have been many fewer problems with any of those recently, apart from '304.51-actually-3.4.43', which was the worst of the lot.

Edit: Moreover, that is the version currently offered by 12.10 Ubuntu Software Center, and, I believe, by Additional Drivers though it does not tell you what version it is until you install it,unless you run: > apt-cache policy nvidia-currentChao!, **bogan**.

---

### Post by grantjohnston on 2013-02-05
> **wshaffer79 said:**
> Bump.  Anyone?  I am wondering if this is an issue just related to Ubuntu, or if other distributions experience this as well.  I had all four monitors working on this system on Ubuntu 11.x, but that version is no longer supported.


No ****, right? I really wish I could downgrade to that to get my TV working as my third monitor (I'm still hoping someone will reply to your other thread here: [http://ubuntuforums.org/showthread.php?t=2105190&page=1](http://ubuntuforums.org/showthread.php?t=2105190&page=1))


Here's another thread I've found on that topic and am hoping for some replies there as well. [http://superuser.com/questions/81981/dual-nvidia-graphics-cards-in-ubuntu-xorg-conf-mania](http://superuser.com/questions/81981/dual-nvidia-graphics-cards-in-ubuntu-xorg-conf-mania)

---

### Post by oldfred on 2013-02-05
I saved this link, but it now is older and is not nVidia.

       12 monitors Natty Warhal
This is a success story for installing 3 ATI Firepro 2260's and 1 Radeon HD 5870 in the same computer. 
[http://ubuntuforums.org/showthread.php?t=1850517](http://ubuntuforums.org/showthread.php?t=1850517)

---

