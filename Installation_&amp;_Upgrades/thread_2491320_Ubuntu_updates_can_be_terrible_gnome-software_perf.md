---
title: "Ubuntu updates can be terrible: gnome-software performing like a Windows PC"
date: 2023-10-04
forum: Installation &amp; Upgrades
---

### Post by w-sky on 2023-10-04
Using Ubuntu 22.04 LTS, there are two options in the GUI for software updates: In addition to the well-known "Software Updater" (update-manager), you can also have the updates installed using "Software" (gnome-software).
Sometimes I use one method, sometimes the other, but I actually feel safest with the "sudo apt update/upgrade", "sudo snap refresh" and "flatpak update" methods in the shell.

The update method with gnome-software is the most opaque method of all. For many types of updates it won't tell you which updates are installed, it just says "OS Updates". Then there is no way to see what is happening. Instead, a restart is forced, and then you see a screen with just a slowly progressing percentage display, which is just as stupid as the ones with Windows computers because it sometimes stops at one value for tens of seconds, then a big jump ahead, then continues counting in steps of 1 and stops again - and even restarts again at 0 with a new heading. So in short, a pretty useless display for the user because it will tell them nothing useful, like what's happening or how much time until finished. And sometimes the updates fail too.

I just had the update from kernel 6.2.0-33 to 6.2.0-34 installed and thought I would be brave today and use gnome-software and soon regretted it. In the process described above it stopped at 97% and I waited for many minutes but nothing happened, only the dot animation kept running steadily. Because nothing else worked I had to reboot and then have apt run again, new kernel was installed but it was missing the post-installation triggers.

gnome-software is a terrible tool for updates, I won't use it again if possible. I even prefer to have the Flatpak and Snap updates installed automatically rather than with gnome-software.

---

### Post by Rubi1200 on 2023-10-04
Perhaps consider disabling unattended upgrades and only running updates/upgrades when you want in the terminal.

```
sudo systemctl status unattended-upgrades

sudo systemctl stop unattended-upgrades
```

You can also choose to disable the service from running at boot time:


```
sudo systemctl disable unattended-upgrades

```

Try it for a few days and see if it works out better for you.

You can always start it again.

Disabling the service only means you are stopping automatic updates, including security ones. You would need to be proactive and run updates in the terminal to keep the system updated and secure.

---

### Post by w-sky on 2023-10-04
Thanks @Rubi1200 but the unattended updates are fine for me. Especially since there is a warning before Snap updates are automatically performed when the app is running. (Before Snaps were updated while it was running which usually caused the app to fail, that happened for me with Chromium several times.) Flatpak also can update an app while it is running but it gives a notification after the update, so if running I can close and restart the app to use the new version.

Nevertheless, in my experience, I absolutely cannot recommend to perform the "OS updates" offered by Gnome Software. Better use apt or the Software Updater tool.

---

