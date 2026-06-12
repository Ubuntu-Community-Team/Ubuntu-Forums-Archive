---
title: "Gnome fails to start after software update"
date: 2020-08-11
forum: Installation &amp; Upgrades
---

### Post by riverfr0zen on 2020-08-11
I was already running ubuntu 20.04 with the default desktop environment. 

After running a software update today, upon a (required) reboot I get a pretty useless "Oh no something went wrong" screen when I log in to Gnome.

Here are what I think are relevant lines from /var/log/syslog:

```

Aug 11 11:48:56 metroplex gnome-shell[2959]: JS ERROR: Error: No valid stylesheet found for 'Yaru/gnome-shell.css'#012loadTheme@resource:///org/gnome/shell/ui/main.js:433:15#012_loadDefaultStylesheet@resource:///org/gnome/shell/ui/main.js:378:5#012_initializeUI@resource:///org/gnome/shell/ui/main.js:175:5#012start@resource:///org/gnome/shell/ui/main.js:146:5#012@<main>:1:47
Aug 11 11:48:56 metroplex gnome-shell[2959]: Execution of main.js threw exception: Script <main> threw an exception
Aug 11 11:48:56 metroplex systemd[2596]: gnome-shell-x11.service: Failed with result 'protocol'.
Aug 11 11:48:56 metroplex systemd[2596]: Failed to start GNOME Shell on X11.
Aug 11 11:48:56 metroplex systemd[2596]: gnome-shell-x11.service: Scheduled restart job, restart counter is at 3.
Aug 11 11:48:56 metroplex systemd[2596]: Stopped GNOME Shell on X11.
Aug 11 11:48:56 metroplex systemd[2596]: gnome-shell-x11.service: Start request repeated too quickly.
Aug 11 11:48:56 metroplex systemd[2596]: gnome-shell-x11.service: Failed with result 'protocol'.
Aug 11 11:48:56 metroplex systemd[2596]: Failed to start GNOME Shell on X11.
Aug 11 11:48:56 metroplex systemd[2596]: gnome-shell-x11.service: Triggering OnFailure= dependencies.
Aug 11 11:48:56 metroplex systemd[2596]: Reached target GNOME Session is initialized.
Aug 11 11:48:56 metroplex systemd[2596]: Reached target GNOME session X11 services.
Aug 11 11:48:56 metroplex systemd[2596]: Reached target GNOME Session (session: ubuntu).
Aug 11 11:48:56 metroplex systemd[2596]: Started GNOME Session Failed lockdown screen (user).
Aug 11 11:48:56 metroplex systemd[2596]: Reached target GNOME Session Failed.

```

Looks like the update has broken something with Yaru? Any tips on fixing  this?

---

### Post by cg-152 on 2020-08-15
I am experiencing the same issue, after updating the following packages:

```
gnome-shell-common/focal-updates,focal-updates 3.36.4-1ubuntu1~20.04.1 all [upgradable from: 3.36.3-1ubuntu1~20.04.2]
gnome-shell-extension-prefs/focal-updates 3.36.4-1ubuntu1~20.04.1 amd64 [upgradable from: 3.36.3-1ubuntu1~20.04.2]
gnome-shell/focal-updates 3.36.4-1ubuntu1~20.04.1 amd64 [upgradable from: 3.36.3-1ubuntu1~20.04.2]
```

My syslog is very similar to yours:

```
Aug 15 13:14:54 Thonkpad-E495 /usr/lib/gdm3/gdm-x-session[2468]: (II) AMDGPU(0): EDID vendor "CMN", prod id 5332Aug 15 13:14:54 Thonkpad-E495 /usr/lib/gdm3/gdm-x-session[2468]: (II) AMDGPU(0): Printing DDC gathered Modelines:
Aug 15 13:14:54 Thonkpad-E495 /usr/lib/gdm3/gdm-x-session[2468]: (II) AMDGPU(0): Modeline "1920x1080"x0.0  152.84  1920 2000 2060 2250  1080 1086 1094 1132 -hsync -vsync (67.9 kHz eP)
Aug 15 13:14:55 Thonkpad-E495 gnome-shell[2777]: JS ERROR: Error: No valid stylesheet found for 'Yaru/gnome-shell.css'#012loadTheme@resource:///org/gnome/shell/ui/main.js:433:15#012_loadDefaultStylesheet@resource:///org/gnome/shell/ui/main.js:378:5#012_initializeUI@resource:///org/gnome/shell/ui/main.js:175:5#012start@resource:///org/gnome/shell/ui/main.js:146:5#012@<main>:1:47
Aug 15 13:14:55 Thonkpad-E495 gnome-shell[2777]: Execution of main.js threw exception: Script <main> threw an exception
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: gnome-shell-x11.service: Failed with result 'protocol'.
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: Failed to start GNOME Shell on X11.
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: Dependency failed for GNOME Shell on X11.
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: Dependency failed for GNOME X11 Session.
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: Dependency failed for GNOME X11 Session (session: ubuntu).
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: gnome-session-x11@ubuntu.target: Job gnome-session-x11@ubuntu.target/start failed with result 'dependency'.
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: gnome-session-x11.target: Job gnome-session-x11.target/start failed with result 'dependency'.
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: gnome-shell-x11.target: Job gnome-shell-x11.target/start failed with result 'dependency'.
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: gnome-shell-x11.service: Scheduled restart job, restart counter is at 1.
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: Stopped GNOME Shell on X11.
Aug 15 13:14:55 Thonkpad-E495 systemd[2377]: Starting GNOME Shell on X11...
```

---

### Post by riverfr0zen on 2020-08-15
@cg-152: I managed to fix it on my end, but it was a strange journey. I'll try to provide some pointers, but I'm also not sure exactly what it was that I did which fixed it.

Basically my Ubuntu installation was an upgrade to 20.04 from a previous version of Ubuntu. In that time, I had also tweaked the theme with Gnome Tweaks.

Pointer #1:
I cleared all the extensions from ~/.local/share/gnome-shell/extensions/

Pointer #2: 
Purge and reinstall packages as shown in post #5 here:
[https://bugs.launchpad.net/ubuntu/+source/yaru-theme/+bug/1798984](https://bugs.launchpad.net/ubuntu/+source/yaru-theme/+bug/1798984)

Pointer #3:
I also tried purging and reinstalling gnome-shell, gdm, ubuntu-desktop (Note that I was able to log into Unity & also had lubuntu-desktop installed and at hand -- useful in case you mess up gnome and want a GUI to work with).

Pointer #4:
I think this is what finally got my installation working. When in a CLI, I ran `snap list`, I found that there were some GNOME related packages installed in there. I'm not sure how they got there -- maybe at some point in the past I had tried to use snap to install GNOME, or it was something else. Anyway, I removed those packages using snap, and as I said, I think this is what did it.

Generally, you should reboot the system after trying any of the above to check results.

Sorry I can't give you a more definitive answer, I was working pretty frantically to get it fixed and didn't keep good notes. Hope this helps.

---

### Post by cg-152 on 2020-08-16
I had customized my system a bit and removed most of the bloatware, so I didn't really want to completely reinstall all those packages. I went looking for a different way, and I think I've found it. It seems that during the upgrade process to gnome shell 3.36.4, one of the packages refers to gnome-shell.css, which is [deprecated]("https://github.com/ubuntu/yaru/blob/c083339f2d113cbe60da3bf505d78c4741fec466/debian/yaru-theme-gnome-shell.prerm#L11") and wouldn't be in a 20.04 install. Ubuntu 20.04 seems to use compiled .gresource files to hold the css, but the package doesn't recognise it. I took the following steps to resolve the issue:

- Navigate to /usr/share/gnome-shell/theme/Yaru

- Install the package libglib2.0-dev to work with .gresource files

- Run the command ```
gresource extract /org/gnome/shell/theme/gnome-shell.css gnome-shell.css
``` to extract the css

- Restart my computer

Those steps worked to fix the crash; As for the older gnome snap packages you found, it seems snap [automatically keeps the last three package versions]("https://askubuntu.com/questions/803275/system-keeps-older-snap-packages").

---

### Post by riverfr0zen on 2020-08-16
That's great, thanks for posting the solution you found.

---

### Post by bing2 on 2020-08-23
cg-152's elegant solution saved my week and my sanity.  thank you!!

and thanks to  riverfr0zen for getting the issue out there a few days before it bit me.  

yeehaa!

---

### Post by cg-152 on 2020-08-27
I found a bug report of what seems to be the same bug from last year, I've marked it as affecting me and here's the link: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1809092](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1809092).

---

