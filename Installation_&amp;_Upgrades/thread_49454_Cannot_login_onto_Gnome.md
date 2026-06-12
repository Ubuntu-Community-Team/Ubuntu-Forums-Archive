---
title: "Cannot login onto Gnome"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by korso on 2005-07-16
Hi to all people using this forum. Some friend of mine showed me Ubuntu in his computer and i thought it was worth giving it a try. So I downloaded the installation CD and installed the system into a logical partition, with no errors or problems at all... But when computer restarts to prompt for login into gnome the only thing I see in the screen is weird colors and the image completely corrupted... I am a not new to Linux nor i can say that I am an expert... So I hope someone can lend me a hand here ;)

My computer specs:

Athlon XP 1800+
768 Mb DDR266
80GB Seagate HD
200 GB Maxtor HD
Geforce 6600GT AGP

Windows XP OS on primary hard disk
installed ubuntu on logical partition of 200GB Maxtor, grub run without any problem.

Thanks a lot for reading :)

---

### Post by javiadip on 2005-07-16
Its prolly coz Ubuntu cant recognize your video card, when the screen comes up, press ctrl+alt+backspace. It will give you an prompt for login and password in command line. Type in your username and password there. You will need to manually go in and configure the Xorg's configuration file for your video card. Look in google to find out if you can find out a configuration file for your monitor/video card. Xorg's file is located under, /etc/X11. The configuration file is xorg.conf

---

### Post by korso on 2005-07-16
I´ll give it a shot, thx for the reply ;)

---

### Post by korso on 2005-07-16
Ok lock&loaded ;) Ubuntu running fine, just followed Ubuntuguide...

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

And worked like a charm. Thanks a lot Javiadip, the problem was in video card config as you pointed.

---

