---
title: "pending problems after lts upgrade"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by gnorb on 2010-08-24
Hi All,

I upgraded from 8.04 to 10.04 a few weeks after the release. Overall the upgrade went quite well, considering it is my mythtv backend server and that created some excitement, a few issues came up. I have two left that I haven't been able to solve.

1. Login screen never became lucid. Actually it isn't even like 8.04.
So the login theme seems very fossil, basically a grey box with a blue pc-icon. I tried gdm2 setup but all the changes doesn't seem to stick. Only the login wallpaper can be changed. I would really like to see the default lucid login here.

2. Keyring password trouble with empathy. This has come up for many users. Asking for that keyring password at login. Following all the instruktions, I changed the old keyring password to be the same as my login password. But it keeps comming back. I even deleted all ./gnome2/keyring... Also changed the keyring name from 'default' to 'login'. But the password question keeps comming back if empathy is started automatically.

Any help would be appreciated !

---

### Post by gnorb on 2010-09-12
Got around the (2) Keyring trouble here by installing libpam-gnome-keyring which was missing from the upgrade. 


Still trouble with the (1) login screen. Tried:
gksudo -u gdm dbus-launch gnome-appearance-properties

... which gave the following in terminal:
(gnome-appearance-properties:3560): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

---

### Post by gnorb on 2010-09-12
Removed mythbuntu-gdm-theme which seems to override GDM theme and now finaly the gdm2setup works. Mythbuntu was installed in a later stage but must have made some trix that later disturbed the lts uprade. 

Now just to find that lucid icon in the greeter instead of the PC looking icon...

---

### Post by ParadoxBlue on 2010-09-19
I just upgraded from 9.10 to 10.04. I have the same problem with the password thing. It's quite annoying considering I have my system set up for no login password at all. But on the bright side from the looks of this thread you have already addressed most of your own issues. Go Ubuntu Community!

---

