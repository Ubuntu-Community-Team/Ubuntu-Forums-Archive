---
title: "Upgraded to Ubuntu 10.04, problems with Nvidia"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by DeeDe on 2010-06-29
Hi,

I'm sorry to say, I'm a computer n00b, and know practically nothing about ubuntu, so please bear with me. 

I upgraded to Ubuntu 10.04, but I encountered an NVIDIA problem. I followed all the instructions found here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) including removing Nouveau, activating the NVIDIA driver through System->Administration->Hardware Drivers (the second bullet under Installation mentions something about linux headers.  I don't know anything about that, so I haven't tried it.), and following the directions under Common Issues. (After attempting to activate the NVIDIA driver, I rebooted, but I did not get the login screen, instead, I believe I arrived at a terminal.)

When I entered the commands for the "Common Issues" section, after I entered "sudo nvidia-xconfig" this is what I got:

Using x configuration file: "/etc/x11/xorg.conf".
VALIDATION ERROR: Data incomplete in file /etc/x11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".
Backed up file "/etc/x11/xorg.conf" as '/etc/x11/xorg.conf.backup'
New x configuration file written to '/etc/x11/xorg.conf'

I don't know what any of that means.

Afterwords, I rebooted, but the login screen still doesn't appear, and I arrive at the terminal(?) I believe. 

This is the NVIDIA file version I have (I think): 7.15.11.7521

Any help is appreciated.  =)

---

### Post by dino99 on 2010-06-29
actual kernel directly deal with X, so no need of xorg.conf

into a terminal:

sudo rm -f /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get install nvidia-current
sudo apt-get install nvidia-current-modaliases
sudo apt-get install nvidia-common
sudo apt-get install nvidia-settings

( copy/paste one by one the above command and accept everything if asked)

then reboot

---

### Post by DeeDe on 2010-06-29
Thank you dino99.

I entered all of the commands, but I still can't get a log in screen. 

A friend suggested I try running Ubuntu on the open source driver and then activate the NVIDIA driver from my system, so this is what I did:

sudo aptitude install linux-headers-$(uname -r)
sudo mv /etc/x11/xorg.conf/etc/x11/xorg.conf.old
sudo update-alternatives --config gl_conf
      *I selected /usr/lib/mesa/ld.so.conf .... btw I know I previously had another selection here... I can't remember the name of it, but now I only have the nvidia-current auto, mesa manual, and nvidia-current manual.  I don't know if this is relevant at all, I'm just throwing it out there.*
sudo ldconfig
sudo update-initramfs -u
sudo reboot

So I was able to start Ubuntu on a low graphics driver, I logged in, went to Hardware Drivers from my system, activated NVIDIA current, and restarted.  When I did, I still didn't get a login screen.

---

### Post by dabl on 2010-06-29
If the "Hardware Drivers" method isn't working for you, you might want to try installing the downloaded Nvidia proprietary driver.  Version 256.35 is working very well on my rig.  Here is a "how-to":

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

It was written for Kubuntu, but the only difference is that GDM is your Gnome display manager, and gedit is your text editor -- everything else is the same.

---

### Post by memphisrich on 2010-06-29
I upgraded to nvidia-current via Synaptic today. Then I went to System->Hardware Drivers to activate them via Jockey. After restart, I could only get a terminal as well. /var/log/xorg indicated that screen was found but not usable or no driver loaded. After trying to reconfigure several things via dpkg and trying to modprobe nvidia with no luck, I ran sudo nvidia-xconfig. That auto saved to a new xorg.conf. Then I typed startx and everthing is now back and I am running the previous driver nvidia-173. 

Also, prior to running nvidia-xconfig, I removed the nvidia-current driver, so I don't know if it would've worked otherwise, but I think it would.

Hope this helps get your x back. A console might be fine for some, but the majority of my usage is browser and email, so I get a little panicky when I lose x.

---

### Post by DeeDe on 2010-07-02
Hi memphisrich,  
Okay, I tried following your instructions. Please remember that I'm new to all of this (as in, have only been trying entering commands for a few weeks new). 

So this is what I did:  

1) sudo nvidia-xconfig 
startx  

What was displayed in the terminal is exactly what you mentioned at the beginning, that the NVIDIA driver had no usable configuration and that screen found but not usable.  

So then I tried this:  

2) sudo update-alternatives  --config gl_conf 
(I choose nvidia 173) 
sudo ldconfig 
sudo reboot  

I got the terminal again.  

So then I tried removing the nvidia-current driver: 

sudo apt-get purge nvidia-current 
and tried the second steps again  

When I got the terminal again, I tried choosing nvidia 96.  Which got me a terminal again.  I tried startx, but I get the same error messages.  

Oh yes, after trying nvidia 96 and restarting, Ubuntu ran an error check on my disks, I don't know why.  

So now, I'm still at the terminal, but without nvidia-current. Thanks for your suggestions though.  

dabl, I'll try your procedure, but it looks awfully confusing to me, so I'll have to try it when I have more time.  I just hope I don't mess up my PC.

---

