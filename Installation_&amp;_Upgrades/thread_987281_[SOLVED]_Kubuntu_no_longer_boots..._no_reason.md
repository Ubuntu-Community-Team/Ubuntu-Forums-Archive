---
title: "[SOLVED] Kubuntu no longer boots... no reason?"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by jimhaddon on 2008-11-19
Hi All,

I've had Kubuntu installed for ~2 months now. Not problems at all, then today I come to boot.. and nothing. I've not changed any settings or installed new programs.

The system gets to the splash screen, loads the first three icons (up the the 'earth' symbol) then refuses to load any further. I've waited 20 minutes and it goes no further, and i've also tried a reboot.

Any help guys?

(p.s. I've had XP installed for 6 YEARS now, it has NEVER not booted like this!)

---

### Post by pytheas22 on 2008-11-19
It sounds like your system itself is booting, but you simply can't log into KDE.  At the screen where it hangs, if you press control-alt-F2, are you brought to a command prompt, and if so can you log in there?

If you can get to a command line, there are some things we can try to fix KDE.

---

### Post by jimhaddon on 2008-11-19
Thanks. I can indeed login after pressing ctrl+alt+f4

---

### Post by prshah on 2008-11-19
> **jimhaddon said:**
> 
The system gets to the splash screen, loads the first three icons (up the the 'earth' symbol) then refuses to load any further. I've waited 20 minutes and it goes no further, and i've also tried a reboot.


At the point where it refuses to go further, press Ctrl+Alt+F1 and logon to the Virtual Terminal presented to you (Black Command Line Mode Screen).

Now, give the command ```
cat /var/log/message | tail -22
``` and post back whatever you can, or whatever looks suspicious.

If you can post your entire /var/log/message file, it will be helpful. It's too big for a post on the forums, so you can compress it and upload it here. To compress, at the command line, use ```
tar cz -f msglog.tar /var/log/messages
``` This will create a msglog.tar file in the current directory, which you should upload here if possible.

---

### Post by jimhaddon on 2008-11-19
Hi,

Please find attached output when using the above suggestion

Cheers

---

### Post by pytheas22 on 2008-11-19
> Thanks. I can indeed login after pressing ctrl+alt+f4 

Since you can get to a command-line, you can try creating a new user by typing:
```

sudo adduser newuser
```

It will ask you for a password (and some other information that you can skip).  Once the new user is created, press control-alt-F7.  This should bring you back to the graphical screen where KDE is hanging.  Press control-alt-backspace, and it should kill KDE and bring you to a graphical login screen.

At the graphical login, try logging in with the username 'newuser' and the password that you set earlier.  Does this get you logged in?  If so, you can probably fix the problem with your real user account by simply deleting your KDE configuration files.

---

### Post by jimhaddon on 2008-11-19
Well, I can certainly give that a try.. but why should I have to? It's only been running two months - I've not done anything out of the ordinary!

---

### Post by pytheas22 on 2008-11-19
> Well, I can certainly give that a try.. but why should I have to? It's only been running two months - I've not done anything out of the ordinary!

It's of course hard to say what could have gone wrong, but I suspect that KDE just got messed up somehow.  I don't think it's a system-wide problem because nothing looks out of the ordinary in the log screenshot that you posted above.  It's probably just some kind of misconfiguration with your user account and/or user-specific KDE configuration files.  How it happened is impossible to say, but it shouldn't be too difficult to fix.

Also, you're not out of hard disk space, are you?  Because that could cause problems like this.

---

### Post by linux_tech on 2008-11-19
Do you see any clues in the log files or dmesg?
Ctrl+Alt+F1, to get to CL
(you can post output)

```
dmesg | tail
```
```
less /etc/kdm.log
```
```
less /etc/syslog
```
```
less /etc/Xorg.0.
```

Also try to start in recovery mode and then use startx or kdm

```
kdm
```

```
startx
```




do anything?

---

### Post by prshah on 2008-11-19
Do you have a hardware switch for wireless? Try toggling it (if it's off, turn it on, and if it's on, turn it off) and then booting. If it boots, you can put the switch to whatever you usually use (on / off), this maybe only a one-time issue.

The error messages posted in the screenshot are similar to eeePC issues with hardware wireless switches (specific cases, non-default configuration). Apparently, to save power, many disable the wireless, but the wireless configuration and components remain.

Also, if the above doesn't work, choose an older kernel from the GRUB menu (Tap ESC repeatedly _after_ the BIOS screen to get the GRUB menu), and check if that works.

---

### Post by jimhaddon on 2008-11-19
Hi Guys,

This looks out of the ordinary!

Appeared after logging in.

I tried the suggestion of adding a new user then logging in as them. However, when I did this, I was simply returned to the login screen.


I also tried using recovery mode, then starting kdm, but I was then unable to use my keyboard or mouse.

Thanks... James

---

### Post by prshah on 2008-11-19
> **jimhaddon said:**
> 
This looks out of the ordinary!


Just delete (or preferably, move) the .ICEAuthority file; it will be recreated automatically on the next login.

---

### Post by pytheas22 on 2008-11-19
Try logging in on the command line, then type:
```

rm ~/.ICEauthority
```

Then try logging into KDE again.  Any luck?

Also, are you sure you're not out of disk space on /home?  If you type:
```

df -h
```

it will tell you if you are.  These problems seem strange so I wonder if a lack of disk space is what's going on.

---

### Post by jimhaddon on 2008-11-19
I deleted the ICEauthority file, and all is now well. Thanks for your help guys.

No idea what caused this though!

And no - i'm not out of space, 3.5GB free.

---

### Post by pytheas22 on 2008-11-19
Glad it's fixed.

You may want to delete that user account that you created earlier, just for security reasons.

---

### Post by prshah on 2008-11-19
> **jimhaddon said:**
> 
No idea what caused this though!


Corrupted .ICEAuthority files are _usually_ traced to an improper shutdown.

If that can't be it, maybe you should check for bad blocks on the hard disk (When you have a lot of time on your hands); boot off a live CD, unmount any mounted HDD partitions, turn off swap, and run an fsck```
sudo swapoff -a
sudo fsck -c /dev/sda
```

And if it's not that either, then it's just gremlins...

---

### Post by jimhaddon on 2008-11-19
Thanks for that guys. I have removed the extra user created earlier.:guitar:

---

