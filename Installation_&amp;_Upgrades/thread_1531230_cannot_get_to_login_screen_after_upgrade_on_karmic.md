---
title: "cannot get to login screen after upgrade on karmic"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2010-07-14
HI All,
I did an upgrade on my system yesterday. After the completion of the upgrade on restarting the system the computer enters tty1  mode straight without giving me the GUI login screen making it difficult for me to work.
The question  does now is what could have caused this to happen ?
Have i gottten something wrong somewhere?

To switch to tty7 mode i hit the key crtl+alt+7 but it gives an error message about an unknown user even after login in with my username and password on tty1.
Start the computer on recovery mode and selected the option correcting broken packages and it produced a result requiring me to download some new packages.
I have a huawei e1550 modem  which i use to browse in Nigeria.
I want to know how i can connect to the internet on the tty1 after insertion of the modem so i can download the necessary packages it requested on issuing dpkg command for that maybe that would help resolve this problem.

---

### Post by 10ghost on 2010-07-15
sudo dpkg safe upgrade
This was the command i entered on a lucid system.
The system was already a lucid system.
Is it wrong to do an upgrade(safe) on a system that is already on the highest version already?
How can i solve the problems in the first thread?

---

