---
title: "Mid-Upgrade window lost focus/off-screen. how to regain focus?"
date: 2012-06-24
forum: Installation &amp; Upgrades
---

### Post by silentstone on 2012-06-24
I'm in the middle of a distro upgrade to 12.04 via alternate CD.  It's running from the shellscript supplied on the CD--**/media/upgradecd/cdromupgrade**--in **gnome-terminal** on a Unity desktop session.  Everything was going fine until I tried to *ALT+TAB* to another running program while many system files were being updated.  All program windows and icons and taskbars/dash disappeared, leaving a clean view of the wallpaper.  No desktop keyboard shortcuts are functioning, including ALT+TAB, although *CTL+ALT+1* accesses a CLI that I can log in with.

Is there a way to bring up the **gnome-terminal** that's currently running the upgrade, or latch into it through the CLI?  The upgrader seems to still be running (it's listed as "**precise**" in **top** and **ps**), but resource usage has dropped so the upgrader's probably asking for input.

---

### Post by silentstone on 2012-06-24
I can run **ps** and **top** and anything in TTY1 through TTY6, so I can see that all the GUI-related processes are still open and going.  And **dpkg** and **precise** are listed as running on *TTY*'s "pts/0" and "pts/1", which seems to stand for "pseudo terminal slave N".  But no command seems to allow remote viewing or control of a pts.

Here's what I've tried with **dpkg**:
```

sudo dpkg --configure --pending  #got a message about the dpkg database being locked.
sudo dpkg --yet-to-unpack        #gets nothing
sudo dpkg --audit              #gets long list of packages

```

---

### Post by silentstone on 2012-06-24
Okay!  Apparently, the upgrade process keeps lovely logs in */var/log/dist-upgrade* folder.  They show that **sudo** was the last package to be worked on, and the upgrader  has paused on the question of keeping the */etc/sudoers* file since it was user-modified!  

But how do i interact with the process?

---

