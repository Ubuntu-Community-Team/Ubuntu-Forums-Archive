---
title: "Missing sound icon"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by HappyLinux on 2011-01-19
OK, this is a minor thing, so I won't expect anyone to rush to my help with this.

Usually right next to the clock, network icon etc, there is the sound icon for direct access to basic sound controls.

Well, the thing is, there was a mail icon next to it. When I clicked to remove the mail icon, the sound icon went with it. I can't find how to get the sound icon back.

If I need to adjust the volume, I have to go through System->Preferences->Sound.

Anyone got any ideas?

---

### Post by renoirbleu on 2011-01-19
hello
I have no key to solve problems, especially the one you've got there
cuz I have the same problem quite a long time.
I just found that many other users (in France) have similar problems with icons disappearing or double-presence (does it make sense?) in the top panel.
actually they concluded that this is a sort of bug when Linux doesn't configure changes in the position or the number of icons.

my problem is like.. sometimes I don't see the icon for turning off the computer, and sometimes there are two same icons, or sometimes one is missing, etc, etc. it changes every time and it restores itself from time to time. (very weird)

I tried to change the panel to default but this problem still recurs !
could anybody confirm that this was already reported as a bug in English ?
(FYI, it was already reported in dutch and french sites)

---

### Post by Frogs Hair on 2011-01-19
The volume and mail are part of the indicator applet found on the add to panel menu . I you restore the indicator applet both icons will return .

Right click the panel > add to panel > indicator applet.

---

### Post by HappyLinux on 2011-01-19
I just looked at the applet list and couldn't find anything to do with sound.

---

### Post by HappyLinux on 2011-01-19
(deleted)

---

### Post by HappyLinux on 2011-01-19
(deleted)

---

### Post by HappyLinux on 2011-01-19
(deleted)

---

### Post by HappyLinux on 2011-01-19
(deleted)

---

### Post by HappyLinux on 2011-01-19
> **Frogs Hair said:**
> The volume and mail are part of the indicator applet found on the add to panel menu . I you restore the indicator applet both icons will return .

Right click the panel > add to panel > indicator applet.

I tried looking where you said, but there isn't anything in the list that mentions anything to do with sound.

---

### Post by renoirbleu on 2011-01-19
it might sound silly but what's the height of your panel ?
some users said when they widened it from 25 to 30, all the icons have come back.
you may try that one...

---

### Post by Frogs Hair on 2011-01-19
> **HappyLinux said:**
> I tried looking where you said, but there isn't anything in the list that mentions anything to do with sound.

The indicator applet doesn't say anything about sound , but the volume and mail icons are added to the panel when you add the indicator applet.

It has been suggested by some that this should be changed because if you look for a sound or volume control on the add to panel menu you will not find it.

Add the indicator applet and the volume icon should appear.

---

### Post by Frogs Hair on 2011-01-19
If you would like to restore your panel to default run this in the terminal.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by HappyLinux on 2011-01-20
Just done it. cheers.

---

### Post by ernz on 2011-05-18
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

This worked for me too. Fixed missing sound icon on 64-bit 11.04 Natty

If the panel fails to load again you can restart X by pressing ALT + SYS RQ + K    **This will kill the session though so save anything you're working on before pressing that!**

---

