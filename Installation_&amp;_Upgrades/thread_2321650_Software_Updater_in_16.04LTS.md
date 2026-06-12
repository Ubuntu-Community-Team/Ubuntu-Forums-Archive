---
title: "Software Updater in 16.04LTS"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by ronlewis7 on 2016-04-23
Just upgraded from 14.04lts to 16.04 lts and everything ran ok from a dvd install.
When i tried to run the software updater to see if any new items were available then updater has a message that states: "you stopped the check for updates". The three buttons available at the bottom of the dialog box are "OK", "TRY AGAIN", and "SETTINGS".
When i select TRY AGAIN it does nothing. If i select SETTINGS it clocks and returns the message "THE SOFTWARE ON THIS COMPUTER IS UP TO DATE". It has been doing this for two days. Will i eventually get updates or is there something that needs to be reset?
I have never received the message on 14.04 that i stopped the check for updates.
Any thoughts on this.
Thanks in advance.
Ron

---

### Post by ajgreeny on 2016-04-23
Have you tried running ```
sudo apt-get update
sudo apt-get upgrade
``` in terminal to see if that gives you any clues?

---

### Post by ronlewis7 on 2016-04-23
hi ajgreeny
I did exactly that and found out that when i first attempted to install the system76 drivers after the update i did not do the install properly and that was the cause of the error message.
I went back into terminal and entered the correct parameters and then it updated ok.
After that the software updater worked ok and it searched for additional updated without a problem.
Thanks for the input and help.
Ron

---

### Post by ajgreeny on 2016-04-23
Great.

Please mark as SOLVED from the Thread Tools menu up-top.

---

