---
title: "After upgrade to 20.04 notebook goes to sleep after login"
date: 2021-01-31
forum: Installation &amp; Upgrades
---

### Post by equi000 on 2021-01-31
Hi,

I'm new to the Forum. I switched from Win7 to Bionic Beaver about one year ago and installed 20.04 today. I know how to open the terminal, but I am just a user with little Linux knowledge. Now I have 2 severe problems. The most strange is this:

After entering the password in the log in screen my Fujitsu notebook immediately goes to sleep - like pressing the on/off button.

I can wake it up by pressing the HW on/off button. After that WiFi is always switched off. I can switch it on in the settings, this works until next login.

(The other problem is, that the audio (internal head phone jack) does not work... I guess this is not related, or could a driver problem lead to the going to sleep??)

system: Fujitsu Lifebook S761, Ubuntu 20.04.2 LTS 64-bit

Any ideas? Thanks a lot.

---

### Post by CelticWarrior on 2021-01-31
I suggest updating BIOS/UEFI before anything else.

---

### Post by equi000 on 2021-01-31
Thanks for the hint. I&#8216;ll check if there is a new one, but I think I have the latest. The notebook is 8 years old and got the last updates from Fujitsu quite some time ago.

---

### Post by equi000 on 2021-02-07
Found the solution here: [https://askubuntu.com/questions/85705/stop-laptop-from-suspending-when-closing-lid-in-lightdm](https://askubuntu.com/questions/85705/stop-laptop-from-suspending-when-closing-lid-in-lightdm) The closed lid lead to an immediate sleep when logging in. How strange...

---

