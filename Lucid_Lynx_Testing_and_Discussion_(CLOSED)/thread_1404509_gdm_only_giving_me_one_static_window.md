---
title: "gdm only giving me one static window"
date: 2010-02-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmoore777 on 2010-02-11
LucidLynx 64-bit, i just upgraded all packages.
When I log in, gdm seems to start up, but I get no menu
bars, just a white window in the upper left corner, where
I am able to run commands etc. I also don't get the
orance background. It's still the brown-ish background
that exists when the login box is there.
(is it forcing me into some type of safe mode?)

I have a LucidLynx 32-bit machine, that I just upgraded,
but it's behaving normally.

I even logged in as a different user on the LucidLynx 64-bit
and gdm has the same issue. So I don't think its any of those
dot files in the home directory.

---

### Post by LKjell on 2010-02-11
when you press on your username in gdm see if it says gnome at the bottom and not xterm.

---

### Post by gmoore777 on 2010-02-11
thank you for that.
Didn't know what you meant until I looked at my 32-bit LucidLynx.
On my 64-bit LucidLynx, I am missing that "Sessions" drop down list box. That list box would have in it: "FailSafe GNOME", "GNOME" and "xterm".

So how the heck do I get that entire drop down list box to show up?
(evidently I am stuck in the "xterm" session mode with no way to change it.)

---

### Post by LKjell on 2010-02-11
> **gmoore777 said:**
> thank you for that.
Didn't know what you meant until I looked at my 32-bit LucidLynx.
On my 64-bit LucidLynx, I am missing that "Sessions" drop down list box. That list box would have in it: "FailSafe GNOME", "GNOME" and "xterm".

So how the heck do I get that entire drop down list box to show up?
(evidently I am stuck in the "xterm" session mode with no way to change it.)

rm ~/.dmrc

Should reset to default. If it does not work edit it

```
[Desktop]
Session=gnome
Language=en_GB.utf8
Layout=no
```

BTW just type gnome-session to start gnome in xterm.

---

### Post by gmoore777 on 2010-02-11
That didn't have any effect.

Even if that did work, I don't have that line:
  "Session=gnome"
on my 32-bit LucidLynx machine where I don't have a problem.

and the question remains, why am I not getting that menu to
choose which type of session I need. 


...ok, I somehow fixed this doing several things,
I noticed I was missing these 2 files on my 64-bit Lucid machine:

/usr/share/xsessions/gnome.desktop 
/usr/share/xsessions/gnome-failsafe.desktop


I ran:
sudo dpkg-reconfigure xserver-xorg

rebooted several times.


New problem: I get to the main GDM console, orange background,
I see one document on the "Desktop", but I do not see my top or bottom menu bar.

Are they gone, or is the screen resolution too large.
Right clicking on the empty space, does not show anything
interesting.
did the `sudo dpkg-reconfigure xserver-xorg` command cause this.

I have another 64-bit machine, and I don't have any of these problems.(I expected it to have the same problem as I upgrade all these machines at the same time, so as to get the same behaviour from them while I work on building them out for our developers in prepartion for the April release date.)

---

### Post by gmoore777 on 2010-02-11
ok, so i noticed many packages in a "rc" state when I ran `dpkg -l`.

rc     brasero                 2.29.4-0ubuntu3
 rc     gnome-applets            2.29.5-0ubuntu1
 rc     gnome-control-center     1:2.29.6-0ubuntu3
 rc     gnome-media              2.28.5-0ubuntu1
 rc     gnome-panel              1:2.29.6-0ubuntu2
 rc     gnome-session            2.29.6-0ubuntu2
 rc     libdbusmenu-glib0        0.2.1-0ubuntu1
 rc     libdbusmenu-gtk0         0.2.1-0ubuntu1
 rc     libgstfarsight0.10-0     0.0.17-2ubuntu1
 rc     libido-0.1-0             0.1.0-0ubuntu2
 rc     libkadm5clnt7            1.8+dfsg~alpha1-4
 rc     libpurple0               1:2.6.5-2ubuntu1
 rc     libtelepathy-farsight0   0.0.13-1
 rc     pitivi                  0.13.3-2ubuntu2
 rc     rhythmbox               0.12.6-1ubuntu6
 rc     totem                   2.29.2-0ubuntu2

I compared the state of these packages to my good 64-bit machine, then reinstalled the ones that were in the "ii" state on the good machine.
(can't explain why any of these are in the removed state)
sudo apt-get install --reinstall gnome-media brasero gnome-applets gnome-control-center gnome-panel gnome-session libgstfarsight0.10-0 libido-0.1-0 libpurple0 libtelepathy-farsight0 pitivi rhythmbox totem

rebooted

and all is fine. (although I was missing my power button in the top panel. I added it, but it doesn't have logout or lock screen. had to add that as separate icons.)

Sorry to bother everyone. What a day!

---

