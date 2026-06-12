---
title: "Startup Manager Problem"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by anectine17 on 2009-11-14
OK, I'm a Linux newbie, so please forgive me if this is a stupid question. I recently installed Ubuntu 9.10 on my desktop as a dual boot with Windows XP. I already had Ubuntu 9.04 installed as a dual boot with XP on my laptop. I was getting an error message upon booting to 9.04, so I decided to use Gparted to format the partition and install 9.10 clean, rather than upgrade. 

When I installed 9.10 on my desktop, it was flawless...I was able to install Startup Manager using Synaptic Package Manager and set Grub to make XP as the default OS. When I tried to do this on my laptop, Startup Manager was not listed in the Package Manager. Does anyone have any ideas how to fix this? I used the exact same disc for both installs, so I'm confused. Remember, I'm a Linux newbie, so any instructions need to be pretty detailed. Thanks. 

Alden

---

### Post by wilee-nilee on 2009-11-14
I think startup manager is part of the backports or extra repositories that can be ticked on in software sources.

---

### Post by anectine17 on 2009-11-14
Thanks for the reply. I looked where you suggested, saw Startup Manager listed and tried to install it. I got an error saying it could not be installed.  I have, however solved the problem. 

The partition I installed Ubuntu on was only 8GB.  After the installation, I kept getting warnings about low disk space. I also wondered why Update Manager didn't show any available updates. So, I booted to Gparted and did some partition juggling, which included deleting the questionable install of Ubuntu. I then created a 12GB partition to install it on, and reinstalled. Update Manager ran as expected upon completion of the install, and Startup Manage was available in the Package Manager and installed properly. 

I'm assuming that since the partition was so small, Ubuntu didn't install everything the first time.  Thanks again for your reply. 

Alden

---

### Post by wilee-nilee on 2009-11-14
The usual install of Ubuntu is about 2.5 gigs but it makes the swap partition so it sounds like the swap took up a bigger portion then needed as well, glad you figured it out. Gparted is my best friend.

---

### Post by pjbaillie on 2009-11-15
With a similar system configuration (XP primary; Ubuntu 9.10 dual) I also had problems finding startup manager. I eventually found it and tried to change the default boot. The process seemed to complete but the grub configuration file or what ever it is that now controls the boot (because it doesn't seem to be the old menu.list) does not get updated. However the grub.d header file does. Is there something missing in Startup Manager to complete the boot configuration?
Any help would be appreciated.

---

