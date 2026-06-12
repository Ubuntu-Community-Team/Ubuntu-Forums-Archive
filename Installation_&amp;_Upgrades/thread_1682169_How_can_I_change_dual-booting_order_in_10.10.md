---
title: "How can I change dual-booting order in 10.10"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-02-05
I am using windows 7 ubuntu 10.10 dul booting.
I want to change the booting order, in the old ubuntu version I could do this in /boot/grub/menu.lst.?

---

### Post by Apv507 on 2011-02-05
The location is now /bo0t/grub/grub.cfg

The last Ubuntu release moved or renamed a lot of well known config files which can make them hard to find. Grub and Xorg.conf are a two of them. Using terminal enter the command "sudo nautilus" and it will open up a file browser with root privileges. PLEASE be careful as you can really mess up your system if you change anything while browsing as root, however this is helpful if you have a general idea where a config file might be but aren't sure of it's name. Remember if you aren't 100% sure what you are doing, don't change and save anything, look but don't touch until you find what you need and know for sure.

Hope that helps you now and in the future :)

---

### Post by oldfred on 2011-02-05
You do not edit grub.cfg.

If you just want to default to another system:

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The easiest way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Or you can manually do things by copying the windows entries to 40_custom. Then turn off osprober to eliminate duplicate entries.
If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.


Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

If the new entries work /etc/default/grub add this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true

---

### Post by Apv507 on 2011-02-05
OldFred is right, after rereading your question I got caught up on how you were lost when it came to finding menu.lst and completely missed the point of your question. Sorry about that. 

But if you do reorder things in grub.cfg it will select the top one first.

---

