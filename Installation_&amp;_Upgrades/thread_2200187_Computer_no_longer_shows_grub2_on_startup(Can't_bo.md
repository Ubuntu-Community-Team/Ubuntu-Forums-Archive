---
title: "Computer no longer shows grub2 on startup(Can't boot to Windows anymore)"
date: 2014-01-17
forum: Installation &amp; Upgrades
---

### Post by aaron20 on 2014-01-17
I have an older computer that dualboots Xubuntu and Windows XP. Everything was fine, with no problems at all, until recently after the computer was unplugged and unused for about a month, but now it no longer shows grub2 at startup, and thus it boots into Xubuntu directly every time.
I have run a program I found on here called Boot Repair but it did nothing.

Any help is greatly appreciated!

---

### Post by egeezer on 2014-01-17
Does Gparted still show your Windows partition?  If so, you might try

```
sudo grub-install /dev/sdX

sudo update-grub
```

where X is the drive where both systems live.

This is one way to re-order the entries in the grub menu.

---

### Post by aaron20 on 2014-01-17
Gparted shows the partition, and I even have access to all the files through Xubuntu(There's an icon to directly access the "157GB Filesystem" which goes directly to that partition).

I ran those commands in the terminal and rebooted but it still boots directly to Xubuntu.

One thing that I forgot to mention. When booting the monitor displays an error for about 5 seconds that says "The frequency is out of range", and I don't remember it ever used to doing that. I've been testing it with CRT monitors.

---

### Post by jp734 on 2014-01-18
I can't remember what key you had to press and hold while booting to show grub boot option... Try the shift key. If not, you can do some research on it.

---

### Post by oldfred on 2014-01-18
Post link to BootInfo report.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

The video issue is not directly related to XP issue. It could be grub has wrong video or install has wrong video. Did you set or have system set it with one monitor and now using one with less capability? If you still have that post separate thread with that issue in title and details on monitor & video card.

---

### Post by aaron20 on 2014-01-19
Here the the URL from the report: [http://paste.ubuntu.com/6778166](http://paste.ubuntu.com/6778166)


I also tried booting with a sidescreen LCD monitor. During boot it goes through a phase for about 5 seconds where it says "Input not supported" then continues to work fine.

---

### Post by oldfred on 2014-01-19
Perhaps the monitor issue is causing it to somehow skip grub menu as menu looks normal and shows both Ubuntu & XP as boot choices. With both choices menu should show by default.

Grub does try to use system video, so if not correct may be an issue.

You could try this.
 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply

I think it changes this  setting in /etc/default/grub, so you can reset to size monitor supports.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

---

### Post by aaron20 on 2014-01-20
Oldfred, I took out the graphics card and booted using the VGA port on the motherboard, same issue. It kept having that weird monitor issue with both CRT monitors and the widescreen LED.
But, after ticking that option in Boot Repair it now works like a champ. Grub shows up correctly.

Thank you so much!

---

### Post by oldfred on 2014-01-21
Glad you got it working.

If video mode of 640x480 gives too large grub menu, you can change to whatever your monitor(s) support.
You can at grub menu go to grub terminal and use the vbeinfo to see what your system supports.

---

