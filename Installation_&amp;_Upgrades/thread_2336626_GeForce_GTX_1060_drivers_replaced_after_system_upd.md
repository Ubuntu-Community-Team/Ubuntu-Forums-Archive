---
title: "GeForce GTX 1060 drivers replaced after system update, password changed"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by Das Goat on 2016-09-09
I am sure someone else must have had this problem before so I hope this is an easy fix.

I have a specific use case and spec'ed the GeForce GTX 1060 because it has Ubuntu Linux drivers then built a new system around it.

Did a fresh install (fresh system totally) of 16.04.1. The default installation drivers made everything 800x600 and HUGE.

did the annoying install procedure by Ctrl+Alt+F3, init 3, then sudo running install script. Rebooted and everything was perfect. 

Ran updates and rebooted. Driver was removed, it was back to being HUGH and worst of all **my password was changed** somehow and I couldn't log in. That is the most troubling :confused: I thought maybe I fat fingered my password, but since I needed it to sudo install the driver, that seems unlikely unless I somehow magically fat fingered it the same way multiple times. Besides, I had to enter the password to get the updates in the first place.

I was able to re-install, then run updates, then install the driver and I am fine right now, but I am really worried about what will happen after the next updates. So I have two questions:

1) how can I prevent the nvidia drivers from being replaced by an update? Is that even possible? The procedure to re-install the drivers isn't hard, just annoying, and impossible for my wife if she runs updates.

2) I can't re-install the drivers if my password gets changed and I might loose all of my data, so has anyone seen this problem with the password getting changed during an update?

Thank you in advance for any help you might be able to give.

---

### Post by oldfred on 2016-09-09
How are you installing nVidia driver?
If from .run file you have to readd it to integrate into update image. If from repository then dpkg automatically does it.
But with that new of a driver you probably need to use ppa to get very newest driver. 

       Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 

If you installed from another source you must purge before attempting to install a new or different driver.
      
 # Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices 


 # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup # if it exists?

---

### Post by Das Goat on 2016-09-09
Oldfred,

First and foremost, thank you for your quick reply. It has been a long day and I am a little punchy.

Sorry if I wasn't clear. To install the driver, I first press Ctrl+Alt+F3 to exit GUI, then sudo init 3 to reboot into non-GUI mode, then I ran the install file (something very long).run

I am not sure exactly where you are pointing me with your links. My understanding is this is not a PPA or dpkg situation. However I did do what the first link suggested and I did add the last command you suggested in the last section. The middle three seemed mostly informational.

If it explodes I will come back and post some more! :o

---

### Post by oldfred on 2016-09-09
When you use the nVidia .run file, it has to in effect be reinstalled with every kernel update. So best not to do that. And you must totally purge that install or you get major conflicts.

Use ppa and install newest from the updated (with ppa) repository. Then with kernel updates the nVidia driver will automatically be included.

---

### Post by Das Goat on 2016-09-24
OK, well now I am stuck. I was out with the family, I live in Florida, and while we were gone there was a power outage. I know, I know, UPS. Truly sad that I had ordered and received the replacement batteries but had not had a chance to install them. So when I rebooted when I came home I could not get back into my desktop. I was getting a lot of EDID errors. From a really old thread I learned that Ubuntu was totally confused by my video card setup. Periodically, I would get the menu where the X window configuration utility would try to load, I tried the options under there, (basic configuration, default, view error log, view configuration, manual configuration, command line) but not would actually do anything (empty logs, dialogs would just repeat without doing anything). 

Just to throw another fly in the ointment, I have a mildly exotic setup with an additional video card that I blacklist and give over to QENU/KVM. That is not really the issue right now. But knowing my troubleshooting skills, I removed the second video card and rebooted.

So now it boots up just like before with the video driver lost, only one screen up, and resolution is something like 800x600. That would not be a problem because I could just reinstall the driver, except that the damn password error has come back. I used the system normally for a week and had ample opportunity to use my password so this is not an issue of fat fingering my password. Somehow Ubuntu will not recognize my password. What could possibly be causing this and how can I get around it? Knowing that my system was dodgy it is not like I kept lots of live documents there and I use the cloud, but on this occasion I had written an important letter in a VM (I try to only use Windows in a VM) and I can't just erase everything and start again, I need to get that VM fired up again get the letter off. Long term, I have to find a better resolution than reinstalling / reloading when ever these issues come up, but for now I am desperate to understand why and how to get around the fact the Ubuntu no longer acknowledges my password for no apparent reason. I must get this letter off tomorrow, 9/25

Please help with the password issue. Everything else I can deal with later.

Goat

---

### Post by Das Goat on 2016-09-25
Update:

I pulled the NVIDIA card and plugged in the AMD one. Video restored itself to normal resolution, presumably because AMD is better supported in Ubuntu. But the password thing has me stumped. I booted to a Live USB and got my VM off and recovered my document, but I don't know what to do about the password.

Anyone have anything I can try? Is it possible to change a user's password on the system from a USB Key? Is the password file corrupted and can it be restored from the shadow file? Is there a way to back up things to prevent this in the future? I still don't understand how a video card driver corruption could change my password.

:confused:

---

### Post by oldfred on 2016-09-25
Do not know if virtual installs are the same or not:

 [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

### Post by Das Goat on 2016-09-26
Under kernel versions:
4.4.0-38-generic (recovery mode)
4.4.0-36-generic (recovery mode)

I received these errors

[2.972920] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem

under 4.4.0-31-generic (recovery mode)

it was able to reset the user password,  however on reboot I could not login.


so  I am not sure what to do now, I can rebuild the entire system, but that is not really a solution.

---

### Post by oldfred on 2016-09-26
You said you switched to AMD.
Not sure about support on AMD, currently. 
 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html)
[https://www.x.org/wiki/radeon/](https://www.x.org/wiki/radeon/) 

There is a beta AMD driver, but that should really only be installed for second or test installs, not main working install.
      
 AMDGPU-PRO  beta Radeon RX 460/470/480 vs. NVIDIA Linux GPU Benchmarks
[http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1](http://www.phoronix.com/scan.php?page=article&item=amdgpu-pro-rx460&num=1)

We never suggest installing the .run from nVidia. Use a ppa to get newest driver.

 Ubuntu 16.04 LTS installation problem with GA-Z170X-UD5 TH & GTX 1080
[http://ubuntuforums.org/showthread.php?t=2327648](http://ubuntuforums.org/showthread.php?t=2327648) 
   NVIDIA GeForce GTX 1060 Offers Great Performance On Linux
[http://www.phoronix.com/scan.php?page=article&item=nv-linux-gtx1060&num=1](http://www.phoronix.com/scan.php?page=article&item=nv-linux-gtx1060&num=1) 



 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   [http://askubuntu.com/questions/813676/installing-ubuntu-mate-with-dual-boot-option-on-windows-10-usb-booting-not-hap/814413#814413](http://askubuntu.com/questions/813676/installing-ubuntu-mate-with-dual-boot-option-on-windows-10-usb-booting-not-hap/814413#814413)
# Shows standard repository versions
ubuntu-drivers devices
sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
ubuntu-drivers devices

---

### Post by Bucky Ball on 2016-09-26
The drivers for this card are in Additional Drivers as far as I know. Why not install from there and that should keep them where they are.

---

### Post by Das Goat on 2016-11-02
How do I close this thread?

I don't know if it was really solved, but it hasn't broke again in a few months.

---

### Post by oldfred on 2016-11-02
Did you end up using nVidia 1060 driver as title of thread?
Or just convert to AMD?

If results match title, you should change to solved.
       Let us know what works and to mark your thread as [SOLVED] for new forum vb4:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

