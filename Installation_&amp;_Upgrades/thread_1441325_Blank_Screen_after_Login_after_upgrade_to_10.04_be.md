---
title: "Blank Screen after Login after upgrade to 10.04 beta"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by anjanesh on 2010-03-28
I just upgraded from 9.10 to 10.04 beta and now I get the login screen - but after logging in, all I get is a blank screen with a black bar on top showing just the time on the top right hand corner.
If I CTRL+ALT+F1 and reboot using the command line, it restarts showing mythbuntu on shutdown.
Im have nVidia GEForce 8600 - is this due the X crashing ?

I tried all these - no change
```
sudo dpkg --configure -a
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install -f
```

---

### Post by ericesque on 2010-03-28
Got the same thing with a clean install-- if it makes you feel any better.  I guess those Beta tags are worth something after all! ;)

---

### Post by G@B0 on 2010-03-28
I have the exact same problem but mine shows Mythbuntu on the boot splash also I can' t enter commands after Ctrl Alt F1 not even login prompt. It seems that there was a recent update that broke all.

---

### Post by rgutierrez on 2010-03-28
Are you all using Nvidia video cards? What version drivers are you using? I have seen similar errors since I ran all the updates this morning. But, I've been having Nvidia driver issues since I installed.

---

### Post by G@B0 on 2010-03-28
ATI here

---

### Post by ExileAmongYou on 2010-03-28
I got the same thing. I'm now back on a semi-functional desktop, not sure how to fully fix it though. To get it working again, I had to boot to recovery mode, drop to the shell with networking (this is the only way I could get a connection, for some reason) then "apt-get install xubuntu-desktop".
Does mythbuntu run on xfce? I kept seeing hints of that whenever I tried doing anything to fix it, which is what led me to try installing xubuntu.
Hope this works for others!

---

### Post by ExileAmongYou on 2010-03-28
Ah, just rebooted after getting into xfce the first time, and now I'm back in Gnome where I belong!

Other things I did to get here that might have helped:
-Removed the mythbuntu packages that got installed for some reason, I think mythbuntu-default-settings and mythbuntu-gdm.
-Deleted config files from my home folder left right and centre while I was panicking, to try and get back to a default set up (seems to have worked, somewhat).

---

### Post by ericesque on 2010-03-28
As I stated above, I was in the same boat. Stuck in Mythbuntu after the update.

I dropped to tty2 (ctrl+alt+f2) and removed the mythbuntu default settings as Exile mentioned:

```
sudo apt-get remove mythbuntu-default-settings
```

After I rebooted, I was back in gnome.  This might not be an ideal fix, but it gets most people back to a familiar environment where we can clean up.

Thanks Exile for reporting your fix and offering suggestions!

---

### Post by anjanesh on 2010-03-28
Thanks Exile & Eric - I removed mythbuntu-default-settings & Im back !

---

### Post by G@B0 on 2010-03-28
I solved the problem removing the mythbuntu usplash and default settings. I don't know why it was installed. That will solve the problem.
Just do another update-manager -d  just in case.

---

