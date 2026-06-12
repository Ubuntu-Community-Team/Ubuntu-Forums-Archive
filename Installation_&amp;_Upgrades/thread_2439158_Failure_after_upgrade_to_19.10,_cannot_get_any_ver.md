---
title: "Failure after upgrade to 19.10, cannot get any version working"
date: 2020-03-23
forum: Installation &amp; Upgrades
---

### Post by abalone542 on 2020-03-23
Hello, 

As I described [in a previous post]("https://ubuntuforums.org/showthread.php?t=2438693&p=13939293#post13939293"), I was noticed of a failure during an update from 19.04 to 19.10. 

Without answer in the other post, I tried what I could, and here is in order what I observed:
- I could transfer my data from using ubuntu install on a usb key (safe graphics mode, didn't try otherwise)
- I tried the boot repair usb, without success
- I reinstalled ubuntu 19.10. This time I could boot, but only by going in the Advanced options > [some version] recovery mode
- I reinstalled ubuntu 19.04, this time no boot was possible, even in recovery mode. This version was the one that had been previously working perfectly so far. 
- I reinstalled ubuntu 18.04, same thing, but, however, during the installation it was clear that a graphics problem occured (bugs on the screens made it apparent, such as my mouse casting a permanent shadow,...). This version was working in the past on my machine. 

I believe there is some graphics problem somewhere. When I was on the recovery mode of ubuntu 19.10, I tried to update the graphic drivers (as described in the section "Install Nvidia driver using GUI method on Ubuntu Linux" of [this]("https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/")), but there was no update to be made. 

Note the existence of a dual boot, with Windows. I assume there may be some interference there too, but I have not had any impact on Windows thus far. 

Has anyone a suggestion for me?

---

### Post by yancek on 2020-03-23
If you already have boot repair the best option to use is the Create BootInfo Summary option using the 2nd option at the boot repair site, using the ppa as described on their page.  You can do this with the Ubuntu install media.  When it finishes, you will get  a link you can post here as there are a number of members who have a lot of knowledge of booting, Grub and EFI.

---

