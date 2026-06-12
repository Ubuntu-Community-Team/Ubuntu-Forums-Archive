---
title: "GNOME desktop - installed but how to start ?"
date: 2021-08-19
forum: Installation &amp; Upgrades
---

### Post by syed_b_huq on 2021-08-19
I am using 21.04
I installed GNOME desktop using: sudo apt-get install ubuntu-gnome-desktop
It seems to have installed ok. After unpack and a bunch of steps, I got back my prompt.

I rebooted the PC.
1) But how do I start the GNOME desktop. What is the command ?
2) Is there an option I can set to load either GNOME or Ubuntu default desktop at boot time ? What is the command ?

Tks
Syed

---

### Post by deadflowr on 2021-08-19
Log out and in the login screen when you click on your user name, before you enter your password,
look down in the bottom right corner.
An icon should show.
Click on the icon and it should list available desktop sessions.
Choose the session you want to use and click on the icon again to close.
Then enter your password.

Edit: Also you know Ubuntu's default desktop is gnome already.
If you want a gnome desktop without Ubuntu specific branding and features install vanilla-gnome-desktop.
(The vanilla-gnome desktop session at the login screen will be named GNOME)

---

### Post by syed_b_huq on 2021-08-19
I do not see any such icon in the bottom right corner (after I click on my username, password not entered)

---

### Post by syed_b_huq on 2021-08-19
I guess I was trying to installed that version of GNOME that makes your desktop look like MAC with flashy icons on the Bottom of the screen. 
I was not aware that Ubuntu uses a GNOME desktop (must be some other version than the one I wanted).

Syed

---

### Post by deadflowr on 2021-08-19
I seemed to have edited my post while you posted.

Can you login as normal and run this command in a terminal
```
echo $XDG_CURRENT_DESKTOP
```

EDIT:
Again, sorry i seem to have edited again after you posted.
I'm not sure what version ever had the icons at the bottom.
But you can set the icons to go there by going to Settings > Appearance.
Should have an option to set the icons either on the left, right, or bottom.

---

### Post by syed_b_huq on 2021-08-19
> **deadflowr said:**
> I seemed to have edited my post while you posted.

Can you login as normal and run this command in a terminal
```
echo $XDG_CURRENT_DESKTOP
```

Output is: ubuntu:GNOME

---

### Post by deadflowr on 2021-08-19
'nother edit as you posted.
Sorry.

---

### Post by syed_b_huq on 2021-08-19
Thank you so much. This will do and this case can be closed.

---

### Post by monkeybrain20122 on 2021-08-19
I think you can put the dock at the bottom with the dock to dash extension. The version of gnome that has the dock in the bottom out of the box is gnome 40. It is not on any Ubuntu release yet.

See screenshot (Gnome-shell 40 on Archlinux)

---

### Post by deadflowr on 2021-08-19
If you feel the issue has been solved please marked this thread as such:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

