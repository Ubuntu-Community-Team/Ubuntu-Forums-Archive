---
title: "Trouble Installing Ubuntu Desktop"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by KoolAidJunkie on 2012-03-10
Trying to install Ubuntu on a Dell Desktop computer. I'm stuck on the "Splash Screen" for the last 45 min. (The screen with the 5 dots under "ubuntu".)  The dots are changing from While to Red, but its been on this screen for 45min. I've rebooted the computer several times, and it still stays locked on the screen.

I can not use CTRL+ATL+F2


I was able to install Ubuntu Server without issue, but the Desktop version will not seem to install.

---

### Post by raja.genupula on 2012-03-10
[http://ubuntuforums.org/showthread.php?t=1526522](http://ubuntuforums.org/showthread.php?t=1526522)

---

### Post by Bucky Ball on 2012-03-10
The important part from the thread raja has given you is this:

> add before quiet splash --

nomodesetDoesn't matter if before or after 'quiet splash'. It is generally after. 

I'm presuming you have already installed? If so, when you get to the grub list (where you choose OS, if you don't get there but go straight to the dot screen then press 'shift' or 'escape' after BIOS, depending on release, and that will take you there) choose the kernel you are wanting to boot then hit 'e'.

Then follow the instructions above; add 'nomodset' to the kernel line. If that doesn't work, try 'acpi=off'. You don't need to add all the options outlined in that link (in fact, it could be a bad idea to do that).

If you haven't yet installed, easier still. As the link suggests, when you boot from the CD to install and get to the screen with 'Try Ubuntu, Install Ubuntu' etc. hit F6 and choose 'nomodset'. Continue with the install. 

Good luck. ;)

---

### Post by KoolAidJunkie on 2012-03-10
> **Bucky Ball said:**
> The important part from the thread raja has given you is this:

Doesn't matter if before or after 'quiet splash'. It is generally after. 

I'm presuming you have already installed? If so, when you get to the grub list (where you choose OS, if you don't get there but go straight to the dot screen then press 'shift' or 'escape' after BIOS, depending on release, and that will take you there) choose the kernel you are wanting to boot then hit 'e'.

Then follow the instructions above; add 'nomodset' to the kernel line. If that doesn't work, try 'acpi=off'. You don't need to add all the options outlined in that link (in fact, it could be a bad idea to do that).

If you haven't yet installed, easier still. As the link suggests, when you boot from the CD to install and get to the screen with 'Try Ubuntu, Install Ubuntu' etc. hit F6 and choose 'nomodset'. Continue with the install. 

Good luck. ;)

Nothing in installed. Ubuntu Server was installed on the machine but I formatted the HDD so I could install Ubuntu Desktop. But i can NOT INSTALL Ubuntu Desktop because it hangs at the loading screen

---

### Post by Bucky Ball on 2012-03-10
Try the 'nomodset' option I have outlined in my last post. Hit F6 when you get to the first screen and choose it.

Or are you not getting to the screen which gives you the options to try Ubuntu or install when you boot from the CD? Is that the issue? It hangs even before that???

---

### Post by 2F4U on 2012-03-11
Did you verify the checksum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

