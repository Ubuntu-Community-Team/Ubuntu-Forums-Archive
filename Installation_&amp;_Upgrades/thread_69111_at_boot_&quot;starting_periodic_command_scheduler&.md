---
title: "at boot &quot;starting periodic command scheduler&quot;"
date: 2005-09-25
forum: Installation &amp; Upgrades
---

### Post by Zikona on 2005-09-25
I have reinstalled several times with the same results. My issue is that [COLOR=DarkRed]whenever I start my box it will stop at a line "starting periodic command scheduler"[/COLOR]. :confused:  I scanned forums to seek help but many threads are answered. I have also tried to modify my xorg.conf without any luck. I should mention that I can still ssh the box or log in to it just fine by using recovery mode. I really need to find out how to go about and if someone can help me that would be fantastic.

---

### Post by mlomker on 2005-09-25
Well, the periodic scheduler is called anacron but it could be stopping on the next line instead, which is ppp (dial-up).

You could look in the /etc/rc2.d and rename the files there one at a time until you find it (I'd recommend adding an underscore as the first character).  They are executed in numerical order--first the K's and then the S's.

---

### Post by Zikona on 2005-09-25
What I have in /etc/rc2.d is:

root@ubuntu:/etc/rc2.d# ls -l
total 0
lrwxrwxrwx  1 root root 15 2005-09-25 12:17 S10acpid -> ../init.d/acpid
lrwxrwxrwx  1 root root 18 2005-09-25 09:51 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx  1 root root 15 2005-09-25 09:51 S11klogd -> ../init.d/klogd
lrwxrwxrwx  1 root root 14 2005-09-25 12:18 S12dbus -> ../init.d/dbus
lrwxrwxrwx  1 root root 13 2005-09-25 12:23 S13gdm -> ../init.d/gdm
lrwxrwxrwx  1 root root 13 2005-09-25 09:55 S14ppp -> ../init.d/ppp
lrwxrwxrwx  1 root root 16 2005-09-25 12:18 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx  1 root root 15 2005-09-25 12:24 S19hplip -> ../init.d/hplip
lrwxrwxrwx  1 root root 14 2005-09-25 12:17 S20apmd -> ../init.d/apmd
lrwxrwxrwx  1 root root 22 2005-09-25 12:20 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx  1 root root 17 2005-09-25 09:49 S20makedev -> ../init.d/makedev
lrwxrwxrwx  1 root root 16 2005-09-25 12:17 S20pcmcia -> ../init.d/pcmcia
lrwxrwxrwx  1 root root 19 2005-09-25 12:20 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx  1 root root 15 2005-09-25 09:55 S20rsync -> ../init.d/rsync
lrwxrwxrwx  1 root root 13 2005-09-25 10:36 S20ssh -> ../init.d/ssh
lrwxrwxrwx  1 root root 21 2005-09-25 12:18 S25bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx  1 root root 15 2005-09-25 09:50 S25mdadm -> ../init.d/mdadm
lrwxrwxrwx  1 root root 17 2005-09-25 12:17 S89anacron -> ../init.d/anacron
lrwxrwxrwx  1 root root 13 2005-09-25 09:55 S89atd -> ../init.d/atd
lrwxrwxrwx  1 root root 14 2005-09-25 09:55 S89cron -> ../init.d/cron
lrwxrwxrwx  1 root root 22 2005-09-25 12:17 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx  1 root root 19 2005-09-25 12:18 S99fetchmail -> ../init.d/fetchmail
lrwxrwxrwx  1 root root 19 2005-09-25 09:49 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx  1 root root 23 2005-09-25 09:49 S99stop-bootlogd -> ../init.d/stop-bootlogd


[COLOR=DarkRed]To do this correctly you want me to rename S10acpid  to _S10acpid ?[/COLOR]

---

### Post by mlomker on 2005-09-25
> 
lrwxrwxrwx  1 root root 17 2005-09-25 12:17 S89anacron -> ../init.d/anacron
lrwxrwxrwx  1 root root 13 2005-09-25 09:55 S89atd -> ../init.d/atd
lrwxrwxrwx  1 root root 14 2005-09-25 09:55 S89cron -> ../init.d/cron
lrwxrwxrwx  1 root root 22 2005-09-25 12:17 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx  1 root root 19 2005-09-25 12:18 S99fetchmail -> ../init.d/fetchmail
lrwxrwxrwx  1 root root 19 2005-09-25 09:49 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx  1 root root 23 2005-09-25 09:49 S99stop-bootlogd -> ../init.d/stop-bootlogd


[COLOR=DarkRed]To do this correctly you want me to rename S10acpid  to _S10acpid ?[/COLOR]

It'd make sense to start where the hanging begins.

---

### Post by Zikona on 2005-09-25
[COLOR=DarkRed]where is a log file that I can post here to show exactly where booting stops?[/COLOR]

---

### Post by CubanCorona on 2005-09-26
I'm having the same problem.  

I just performed a clean intall on a Sony Vaio PCG-R505 laptop.

---

### Post by Zikona on 2005-09-26
After new install did it do it again CubanCorona?


I have also tried to install on different machine with the same results. Could it be possible an issue with the most recent release of ubuntu?:confused:

---

### Post by mlomker on 2005-09-26
[QUOTE=Zikona][COLOR=DarkRed]where is a log file that I can post here to show exactly where booting stops?[/COLOR][/QUOTE]

/var/log/kernel.log is probably the relevant one.

The *latest* release is Breezy and that's a beta.  I assume if you're posting in the Hoary forum that you are running that (5.04).

---

### Post by Zikona on 2005-09-26
You have a point mlomker. I am running Breezy which then would qualify to be beta. I have downloading from the main site following download link so that must be it. Since it's in beta can you show me a way where to get Hoary ?

---

### Post by mlomker on 2005-09-26
It's on the [download]("http://www.ubuntu.com/download/") page, just select the proper country under Hoary Hedgehog.

---

### Post by Zikona on 2005-09-26
Thanks mlomker. I am going to give it a shot with Hoary Hedgehog next.:eek:

---

### Post by cosborn72 on 2005-11-15
I had this problem as well, on an server installation.  I switched over to a new console and did several thing, one of which resolved the problem (I don't know which:???: )

sudo apt-get update
sudo apt-get install x11-libs
sudo apt-get install xfce4 (a lightweight window manager)
sudo apt-get upgrade 

I believe the upgrade installed a new linux kernel - 2.6.12-8-386 - which might have been the solution.

---

### Post by shoover on 2006-02-05
Here's another tip. After my fresh install of 5.10 server, I had the same problem as the original poster. I figured I just needed to press Alt-F1 or Ctrl-Alt-F1 to get a login prompt, but it wouldn't work. Finally after banging on the keyboard for a while, I found I had to use the keyboard's **left** Ctrl and Alt keys to get Ctrl-Alt-F1 to give me a login. The right Ctrl and Alt keys wouldn't do it.

---

### Post by shoover on 2006-02-05
I might add that that was all with a fresh install. Once I did switch over, log in, and update and upgrade with apt-get, the next reboot resulted in a login prompt without me having to press Ctrl-Alt-F1.

---

