---
title: "236 Upgrades stuck"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by talto2 on 2008-07-29
I have successfully installed Ubuntu and have printers, internet, and other peripherals working. The updates window doesn't seem to install any of the updates. I have tried just selecting 1 item, all of the items, 1/2 of the items. Even let the machine run all night to see if it was just taking so long due to all the updates and nothing works. I have also searched the forums and tried recovery mode, but I was getting a different screen. I would appreciate any assistance with this.

---

### Post by mordak13 on 2008-07-29
Try this, open a terminal:

sudo aptitude update
sudo aptitude full-upgrade

See how this works and let us know.

---

### Post by talto2 on 2008-07-29
I will try this, but I haven't had to open the terminal window before with Ubuntu, can you provide additional info?

Additional Info: I open the terminal window, and the first line you gave me (sudo aptitude update) was unsupported, I entered the 2nd line and the password was requested, then gave me a list of item -s, etc to select from. None of these seem to match what I want to do.

---

### Post by mordak13 on 2008-07-29
> **talto2 said:**
> I will try this, but I haven't had to open the terminal window before with Ubuntu, can you provide additional info?

Additional Info: I open the terminal window, and the first line you gave me (sudo aptitude update) was unsupported, I entered the 2nd line and the password was requested, then gave me a list of item -s, etc to select from. None of these seem to match what I want to do.
Try sudo -s hit enter then enter your password hit enter again You will then be in a root terminal. then enter aptitude update then aptitude full-upgrade

---

