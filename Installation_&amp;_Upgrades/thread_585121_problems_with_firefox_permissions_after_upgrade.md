---
title: "problems with firefox permissions after upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by buster65 on 2007-10-21
I am having problems with firefox after upgrading to Gutsy. my problem i can only run it by using the terminal an using "sudo firefox". when trying to launch as a user it show the "start firefox" box ont he panel but fails to start. i have tried "sudo chmod 755 firefox" but it says the file doesn't exist. 
Thanks in advance for the help.

---

### Post by buster65 on 2007-10-21
I managed to get a window that tells me firefox is already running and to stop the proccess or restart the computer. well i couldn't find the proccess running so i rebooted and tried to start firefox up and it can up with the same error message. 
Any ideas:confused:

---

### Post by C4nc3l on 2007-10-21
same problem...
i dont try sudo firefox, but firefox with normal user doesn't start:(
now i'm on win when i return on ubuntu i try some like this:
```
which firefox
```
then chmod ...(dont remember code now) in that adress
i hope this can go

---

### Post by 0live on 2007-10-21
> **buster65 said:**
> I managed to get a window that tells me firefox is already running and to stop the proccess or restart the computer. well i couldn't find the proccess running so i rebooted and tried to start firefox up and it can up with the same error message. 
Any ideas:confused:
Go to ~/.mozilla/firefox  (ctrl+H to see .hidden folders in gnome) and verify that there's a folder which name ends with .default
For some reason mine had been renamed to whatever.default.bak

---

### Post by buster65 on 2007-10-21
Thanks. It wasn't renamed but the permissions weren't correct for user access.

---

