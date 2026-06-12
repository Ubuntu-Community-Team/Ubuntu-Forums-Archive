---
title: "[SOLVED] displayconfig-gtk (Screens and Graphics) doesn't apply changes"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by dragonfyre13 on 2007-10-26
For some reason, I can't apply a single change I make in the application.

I'm trying to change to ANYTHING from the vesa driver with 800x600 or 640x480. I can click the test button, and it's fine. It shows up, and shows that it can handle that resolution. However, I then hit OK, and it gives me nothing. No "please logout" message, or "Please reboot" or anything. So I restart the X server (Both by restarting GDM and by pressing Ctrl+Alt+Backspace and neither of these apply any changes.

Also, when creating an xorg.conf manually, it doesn't get any changes from there either. It always goes to "your X Server is not configured correctly" and I can't get any of the data I'm used to when it goes into this state, as it doesn't give me the choice of the blue screen for X failures.

Please help, this is 2 different PCs that it's happening on, and they are the only ones I've upgraded to Gutsy.

---

### Post by dragonfyre13 on 2007-10-26
Got this working. About half an hour after I gave up.

I went in and said "screw it!" and I removed everything from the directory. Then I played a bit. It worked!

I repeated on the other computer in a more controlled manner. Here's how to reproduce.

we delete all xorg.conf files that the program looks for, I think. Then, we move xorg.conf to your home directory in case you want to restore later

```
sudo -s
cd /etc/X11
mv xorg.conf ~ && rm xorg.conf~ && rm xorg.conf.?
/etc/init.d/gdm restart
```

This should get you to a usable desktop. If you want to use a particular driver (if you have an nvidia card, this is what I did on my first box) replace vesa with that driver in the xorg.failsafe file in the same directory.

From that usable desktop, the "screens and graphics" (displayconfig-gtk) works fine! You can choose any resolution, any monitor, and any card, without problems!

This is what I did, and it actually worked after hours and hours of working on this.

---

