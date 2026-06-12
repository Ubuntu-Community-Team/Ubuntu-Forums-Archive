---
title: "Login failed after upgrade to 14.04"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by martin73 on 2014-04-25
Hello, i upgraded Ubuntu from 12.04 to 14.04. After restart it says with red letters login failed. I have tried CTRL-ALT-F1 to get a terminal but there my password is not accepted either.
Does anybody have a clue?
I noticed that during installation the 12.04 desktop disappeared at some stage, leaving only the background image and the terminal from which i ran the upgrade.

---

### Post by John Jason Jordan on 2014-04-25
> **martin73 said:**
> Hello, i upgraded Ubuntu from 12.04 to 14.04. After restart it says with red letters login failed. I have tried CTRL-ALT-F1 to get a terminal but there my password is not accepted either.
Does anybody have a clue?

That happened to me, although only an update, not an upgrade to 14.04. I was able to get to a command line from the login screen with Ctrl-F1, and fortunately for me my password still worked there. 

If you can't get your password to work from the command line the best solution is to boot to a rescue CD, then (as root on the rescue CD), mount your root partition, then (as root) first make a copy just to be safe, and then open /etc/shadow in gedit or nano or your favorite text editor. You should find a line with your username followed by a bunch of colons and a hash. Replace everything after your username with eight colons ::::::::. Save the file and reboot. You should be able to log in to your account without a password.

Assuming that worked and you are logged in, you will need to reset your password.

---

### Post by martin73 on 2014-05-01
Unfortunately it did not work, I still could not log on after I had deleted my password in etc/shadow. However, with Ubuntu 14.04 on a USB stick I could re-install Ubuntu without loss of data. Now the problem is solved.

---

