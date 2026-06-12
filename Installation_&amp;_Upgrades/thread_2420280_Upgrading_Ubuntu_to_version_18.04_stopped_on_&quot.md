---
title: "Upgrading Ubuntu to version 18.04 stopped on &quot;Installing the upgrades&quot; / grub"
date: 2019-06-02
forum: Installation &amp; Upgrades
---

### Post by jj.wauters on 2019-06-02
The Distribution Upgrade had no problems running "Preparing to upgrade", "Setting the new software channels" and "Getting new packages".
But under "Installing the upgrades" / popup window "Configuring grub-efi-amd-64" / selecting "Start a new shell to examine the situation"
the program hanged. 
So I needed to close the popup,window, but now "Installing the upgrades" does not continue the installation.
How to solve ???

---

### Post by cruzer001 on 2019-06-02
You can try to kick back into a upgrade with:
```
sudo dpkg --configure -a && sudo apt -f install


```

---

### Post by jj.wauters on 2019-06-02
The terminal part of "Distribution upgrade" is still open and prompting. But when entering any command nothing is happening.
When entering the dpkg command in a separated terminal, I got the message "dpkg: error: dpkg frontend is locked by another process".
So I assume "Distribution upgrade" must be closed. How to do the cleanup afterwards?

---

### Post by cruzer001 on 2019-06-02
The lock can be manually removed, but if it was me, I would just cross fingers and reboot.  But I have backup and would do a system reinstall if it failed.  Since your upgrade hung on EFI, it may not even reboot.  Your in a tough spot :(

---

### Post by jj.wauters on 2019-06-02
I was lucky! 
The only command accepted in the "Distribution upgrade" terminal window was "exit". 
And believe it or not, now the installation was continuing and ended up with a new attempt to solve the grub issue.
Thanks for helping.

---

