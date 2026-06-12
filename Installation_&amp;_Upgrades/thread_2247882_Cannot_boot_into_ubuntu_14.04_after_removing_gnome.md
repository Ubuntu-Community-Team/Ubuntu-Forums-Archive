---
title: "Cannot boot into ubuntu 14.04 after removing gnome desktop"
date: 2014-10-11
forum: Installation &amp; Upgrades
---

### Post by hamshan33 on 2014-10-11
I cannot boot into ubuntu. I have 14.04. The problem started after removing gnome desktop. 
I was using kubuntu or unity as desktops and it boots using kubuntu.
I have tried to install it back, and do package update with a live CD but it never worked.


It usually hangs at "Samba auto-reload Integration", or If I wait long enough at "Read required files in advance", 
or sometimes it shows this unreadable message: "anac(h)ronistic cron"???

I have also tried the method descried here: [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) but it did not work.

Thanks for any help.

---

### Post by kc1di on 2014-10-11
Hi hamshan33 and Welcome to Ubuntu,

Lets try this at the grub menu select advanced then then select ubuntu recovery mode

a dialogue box will come up select network (Let it do it's thing it will take a minute or twe) then select root
This will take you to a root prompt.
type the following command:
```
apt-get install unity
```

when it's done type ```
shutdown -r now
```
it will reboot see if it boots now.

---

### Post by ajgreeny on 2014-10-11
Try booting into a command line by hitting E when you see the grub menu.  Look for the line containing "quiet splash" and edit that to "text" then Ctrl+X or F10 to boot.  If you get to a command line login with username and password (your password will not show on screen but will be entered so just type carefully and hit Enter) then use command ```
sudo apt-get install ubuntu-desktop
```to see if that gets back everything you need to boot again properly.

---

### Post by hamshan33 on 2014-10-14
Thanks to both of you.

I have tried both methods but none worked. It still hangs with the same message. Any other ways to solve this?

---

### Post by luctor on 2014-10-14
can you boot in recovery mode ?

---

### Post by hamshan33 on 2014-10-15
> **luctor said:**
> can you boot in recovery mode ?
I can boot only into a terminal. Recovery mode, otherwise, gives a similar message.

---

### Post by hamshan33 on 2014-10-16
Anyone else with other suggestions, please?
I really don't want to re-install and wipe everything!

---

