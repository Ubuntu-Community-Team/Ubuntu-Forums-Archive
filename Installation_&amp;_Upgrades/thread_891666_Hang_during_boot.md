---
title: "Hang during boot"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by the-larch on 2008-08-16
two days into a dual boot with XP.

got the wireless working. everything going well.

this morning, after a reboot the desktop background and the mouse pointer are all that loads.

just prior to this, I had succeeded in installing skype and I had tried out suspend which resumed fine except for wireless.

not sure what to do next, searching the forum, I can't find any issues regarding a hang that proceeds to this point.

any suggestions are very welcome.

specs:
HP 6715b
2gb ram
BCM4312
AMD turion 64

---

### Post by the-larch on 2008-08-25
ok.
not having any success with this.

I've updated.
i've tried adding and removing the resume entry to the kernel section in the grub.
I also reinstalled and purged gdm.

However, in moving to the prompt, there are the lingering boot messages which state:

"Kinit: name_to_dev_t(/dev/disk/by-uuid/..(swap digits)... sda6(8,6)
Kinit: trying to resume from /dev/disk/.../...(swap digits)..
Kinit: No resume image, doing normal boot..."

do these messages give any further clues?

---

### Post by pastalavista on 2008-08-25
You might try:
```
sudo gedit /etc/usplash.conf
```

(change gedit to the text editor for Xubuntu.. what is it.. Vim?)

and make sure the screen resolution is set correctly. That being wrong made mine hang for a long time at boot-up when I first installed Ubuntu from a live CD.

---

### Post by the-larch on 2008-08-25
the resolution is the same as in the Windows partition.
1680 x 1050.

any other thoughts?

---

### Post by pastalavista on 2008-08-25
Sorry, I'm a relative noob. Kinit would seem to be a KDE issue and wouldn't run on Gnome. Possibly [this post]("http://ubuntuforums.org/showthread.php?t=277028&highlight=restore+desktop-manager") will help. Since the install is fresh, you might also just re-install Xubuntu.

---

### Post by the-larch on 2008-09-21
Bumping this as I'm yet again experiencing this issue.

Since I originally posted I have reinstalled Xubuntu.
Bumping this as I'm yet again experiencing this issue.

Since I originally posted I have reinstalled Xubuntu.

I was sure the issue was with the Suspend function, so I removed this button from the Quit menu. This worked a treat.

But while logging out this evening I think I managed to suspend again using alt+ctrl & del and I am practically back at the above stage:
the difference being that I do not reach the login stage, so I get the loading screen with the status bar in the centre then I arrive at the prompt with similar messages to above re "no resume image, etc".

I would appreciate further suggestions on this one as I am reluctant to reinstall again. Cheers.
I was sure the issue was with the Suspend function, so I removed this button from the Quit menu. This worked a treat.

But while logging out this evening I think I managed to suspend again using alt+ctrl & del and I am practically back at the above stage:
the difference being that I do not reach the login stage, so I get the loading screen with the status bar in the centre then I arrive at the prompt with similar messages to above re "no resume image, etc".

I would appreciate further suggestions on this one as I am reluctant to reinstall again. Cheers.

---

### Post by the-larch on 2008-09-22
i managed to fix this in the recovery mode in the grub menu using the "fix X" function

---

