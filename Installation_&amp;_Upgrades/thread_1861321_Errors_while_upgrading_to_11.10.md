---
title: "Errors while upgrading to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by DoRullings on 2011-10-15
Hi

Ubuntu asked me if I wanted to upgrade to 11.10 (from previous version), on which I answered "yes". Even though I did not have the power cable connected (or with me to the university), but the battery was completely full charged and the laptop did never run out of power during the upgrade. 

The upgrade went fine with some questions about keeping some config files or overwrite them with a new one from the upgrade, I believe I chose the default option, to keep the old config file, every time. When the upgrade was nearly finished I got an error that told me that the upgrade had failed and had to stop. To avoid a non-working system it would roll back to the previous version. This is not literally the error-message, but I if I remember right this was basically the meaning of the error-message. I clicked ok and I went for a reboot, right before the desktop closed I saw a update window popping up. I could not read what it said because it was killed far too fast by the reboot.

Anyway, after the reboot I logged in to Ubuntu with a new log in screen, some changes in how Unity works, and the System Info says that I'm running Ubuntu 11.10. I don't know if everything works as it should yet because it happened today, but something obviously went wrong and I don not know what. 

What I would prefer to do is to roll back the upgrade as the error message told me it would, but didn't, and do another attempt to upgrade. Is this an option now, or do I have to do a complete new installation? Any other helpful advice will be received with gratitude.

Thanks!

Thomas

---

### Post by MAFoElffen on 2011-10-15
> **DoRullings said:**
> Hi

Ubuntu asked me if I wanted to upgrade to 11.10 (from previous version), on which I answered "yes". Even though I did not have the power cable connected (or with me to the university), but the battery was completely full charged and the laptop did never run out of power during the upgrade. 

The upgrade went fine with some questions about keeping some config files or overwrite them with a new one from the upgrade, I believe I chose the default option, to keep the old config file, every time. When the upgrade was nearly finished I got an error that told me that the upgrade had failed and had to stop. To avoid a non-working system it would roll back to the previous version. This is not literally the error-message, but I if I remember right this was basically the meaning of the error-message. I clicked ok and I went for a reboot, right before the desktop closed I saw a update window popping up. I could not read what it said because it was killed far too fast by the reboot.

Anyway, after the reboot I logged in to Ubuntu with a new log in screen, some changes in how Unity works, and the System Info says that I'm running Ubuntu 11.10. I don't know if everything works as it should yet because it happened today, but something obviously went wrong and I don not know what. 

What I would prefer to do is to roll back the upgrade as the error message told me it would, but didn't, and do another attempt to upgrade. Is this an option now, or do I have to do a complete new installation? Any other helpful advice will be received with gratitude.

Thanks!

Thomas
Welcome to Ubuntu Forums.

Ah... Good description of what you and your PC did, until you got to:
> but something obviously went wrong and I don not know what. 
That sort of leaves me vague as how to help you (at the moment.)

You say that you got to the Login Screen and everything looked fine, then (poof)...  Could you describe what your PC is doing and/or not doing?

---

### Post by 23dornot23d on 2011-10-15
Might be as well looking through the log info viewer too

To see if that tells you anything .... but if its running ok - then upgrades later may 
bring it fully uptodate

as for going back - I doubt that is possible now ..... unless you have a back up

---

### Post by oddparticle on 2011-10-15
This sounds exactly like what happened to me whilst upgrading last night. I got some error messages saying that something had failed to install and that the upgrade had failed, it tried to send an error report but I think this also failed. When I restarted my computer, it appeared to be running the new version, and most things were working fine (internet, music & video, office stuff etc...). 

However, I just discovered that Ubuntu software centre doesn't seem to work. It opens, but the window is empty. No error messages or anything, just an unhelpful empty window... 

I'm sorry for the lack of detail - it was early in the morning when I got the error messages, having left the machine to upgrade overnight, and I restarted it in a bit of a sleepy daze without writing anything down :-/

EDIT: But I'm using 32 bit not 64 bit. And I was upgrading from Natty Narwhal.

---

### Post by DoRullings on 2011-10-15
MAFoElffen: That is partly the point in my post. I tried to upgrade, got an error that told me the upgrade failed and that it would roll back to the original state. Everything is fine until now; When I restarts Ubuntu it has upgraded, it is indeed Ubuntu 11.10, everything seems to work fine, so far. My problem is that it update tool didn't do what it told me it would do; Roll back to the previous version. Now I'm stuck with an upgrade that I was told by an error-message could not complete the upgrade because of an error. I believe I should take that error-message seriously and assume that there is an error somewhere, and that it eventually will show up. I prefer to be pro-active rather than sitting and wait for the error to show up.

I'm do apologize if I was unclear in the first post, and I hope this post make things clearer.

---

### Post by MAFoElffen on 2011-10-15
> **DoRullings said:**
> MAFoElffen: That is partly the point in my post. I tried to upgrade, got an error that told me the upgrade failed and that it would roll back to the original state. Everything is fine until now; When I restarts Ubuntu it has upgraded, it is indeed Ubuntu 11.10, everything seems to work fine, so far. My problem is that it update tool didn't do what it told me it would do; Roll back to the previous version. Now I'm stuck with an upgrade that I was told by an error-message could not complete the upgrade because of an error. I believe I should take that error-message seriously and assume that there is an error somewhere, and that it eventually will show up. I prefer to be pro-active rather than sitting and wait for the error to show up.

I'm do apologize if I was unclear in the first post, and I hope this post make things clearer.
Just my feeling on this-
If it boots the kernel... If it starts the lightdm DM to login... If it starts the GUI desktop... If it updated the grub2 menu... <-- especially that last item!  Then it possibly did finish the distribution upgrade.  The update-grub grub upgrade is always the last step in an upgrade or install.  So it sounded like the "roll back to natty" message didn't work.

What you should do is to Boot into the GUI > open a terminal session > ensure their is no broken or orphaned packages, update the package lists and ensure the upgrade was through.
```

sudo apt-get update
sudo apt-get clean
sudo apt-get -f
audo apt-get dist-upgrade

```If you want to check your installed info:
```

uname -r && lsb_release -a

```

---

### Post by DoRullings on 2011-10-16
MAFoElffen: Thank you for your reply. I did run the commands you posted, and got this result from the upgrade and install info: 

> thomas@thomas-U45JC:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  wine
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
thomas@thomas-U45JC:~$ uname -r && lsb_release -a
3.0.0-12-generic
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric


Does this say anything to you. To me it looks like the upgrade went fine anyway. Grub was indeed the last thing it installed, I remember because I was asked if I wanted to overwrite the Grub config file. I answered yes and regret it immediately, I might I should have let the installer overwrite the Grub config file so that it would point to the new version. But it works, so it didn't really matter and I think I understand why. If I had installed another OS, Ubuntu in this case, I had to let the upgrade installer overwrite the Grub config file. Am I right?

Thanks once again for your quick reply. I've been working all day and after that I have been to my cousin's 5th birthdayparty. My eyes are crossing now. 

There is two things that doesn't work although. The OS wont suspend the computer. I had the same problem with the previous version and found an article about it, and after follow the instructions in the article it worked fine. The only difference is that it hanged/froze, this time it simply wont suspend, the computer is running at full speed all the time and draining the battery. The login screen shows immediately, so it does not use some time to wake up the computer. I'll try that tomorrow.

The other error is that the System Settings > Additional Drivers says that there is newer graphic card drivers available, but the installation fails every time and I'm directed to a log file and here is what I found. (this block is repeated through the whole log-file)
> 2011-10-16 20:51:35,019 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-16 20:51:35,020 DEBUG: nvidia_current is blacklisted, so not treating as enabled

I see that the driver is blacklisted, I found this article aobut it: [https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)
It looks like there is not a good idea to install this driver even though it is possible according to the article. Can you tell me how to see which graphic card driver that is installed?

This post is very long, but I wanted to provide you with enough information.

Thanks!

Thomas

---

### Post by 23dornot23d on 2011-10-16
> 
Can you tell me how to see which graphic card driver that is installed?


nvidia-settings

should show you your installed graphics driver - example below

[IMG]http://img406.imageshack.us/img406/7818/nvid.png[/IMG]

---

### Post by DoRullings on 2011-10-16
23dornot23d: I did run the nvidia-settings command and immediately it popped up an error message saying: > You do not appear to be using the NVIDIA X driver. Please edit your X configuration file(just run 'nvidia xconfig' as root) and restart the X server.[/QUOTE]

I did that and got this error message: > Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf

There is no "Default Device" section has no driver line. I may have installed the driver from synaptic, I can see that there is many drivers ready for installation there. But now Gedit is crashing too the first time I start it, and opens only if I click the icon twice. I think I will go for a complete new install, this time with long term support. I need a stable system, and not be the first to try out new features in Ubuntu.

Thanks!

Thomas

---

