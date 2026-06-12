---
title: "cannot boot after upgrading to Karmic"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by Fibonacci on 2010-03-19
Hello.

I've finally decided to upgrade to Karmic using the CD, and I've run into some problems.
When trying to boot the "new" kernel (2.6.31-14.48) my PC displays the message "Starting NTP server ntpd" on a console, rapidly flashing, and hangs there. Aparently, the only of breaking out of that condition is pressing Ctrl+Alt+Del to reboot the computer.
However, the old kernel (2.6.28-18.60) works flawlessly, and in fact, I'm posting from it right now.

What can I do?

---

### Post by UCSBGauchosRock on 2010-03-19
It is quite possible something went wrong during the installation process or there is corrupt data. One thing I would suggest is to create a new LiveCD with Karmic and try it with that new one.

---

### Post by Fibonacci on 2010-03-19
> **UCSBGauchosRock said:**
> It is quite possible something went wrong during the installation process or there is corrupt data. One thing I would suggest is to create a new LiveCD with Karmic and try it with that new one.

Try what, re-running cdromupgrade from the old kernel?

---

### Post by anksush on 2010-03-19
I am not an expert but I found that upgrading was causing one problem or other and then I downloaded the whole 9.10 iso and created a live CD after checking md5 etc. I used it to do a complete reinstall and all went fine. Of-course it meant taking backup and all that.

HTH !!!

---

### Post by Fibonacci on 2010-03-19
> **anksush said:**
> I am not an expert but I found that upgrading was causing one problem or other and then I downloaded the whole 9.10 iso and created a live CD after checking md5 etc. I used it to do a complete reinstall and all went fine. Of-course it meant taking backup and all that.

HTH !!!

Of course that would be the best option - that is, if I could take it. Unfortunately I cannot make a backup of my whole HD because I have nowhere to store it, so I cannot just wipe out the partition and reinstall.

---

### Post by UCSBGauchosRock on 2010-03-19
> **Fibonacci said:**
> Try what, re-running cdromupgrade from the old kernel?

Possibly, personally though I have never done that. When I first installed Ubuntu Karmic Koala it froze upon login for GNOME. After I updated though it finally let me log in to Regular Gnome, not Failsafe...

---

### Post by Fibonacci on 2010-03-19
> **UCSBGauchosRock said:**
> Possibly, personally though I have never done that. When I first installed Ubuntu Karmic Koala it froze upon login for GNOME. After I updated though it finally let me log in to Regular Gnome, not Failsafe...

How did you update it if you couldn't even log in?

---

### Post by anksush on 2010-03-19
I tried looking up about the NTP thing and there was discussion sometime back though problem was different:

[http://ubuntuforums.org/showthread.php?t=766963]("http://ubuntuforums.org/showthread.php?t=766963")

Now having said that, I think the interesting bit is that apparently there is a NTP update service and a local NTP server being discussed there. If you are up for experimenting, why not try this:

with old kernel remove the ntp server and keep the ntp update

> I'm not entirely sure what the change was, but apparently the "ntp" package in Hardy now runs a local ntp server, whereas in Gutsy it did not. The correct package to just sync time to a server is ntpdate. Anyone upgrading from Gutsy to Hardy has the ntp package, and so it gets upgraded, with the result that you are now running a server. You can uninstall ntp and keep ntpdate for syncing purposes.

The issue is slightly more complex than that, I stopped working out the details once I found removing ntp and keeping ntpdate worked. I'm actually not sure why Gutsy installed ntp, as it wasn't necessary then, either.

---

### Post by UCSBGauchosRock on 2010-03-19
> **Fibonacci said:**
> How did you update it if you couldn't even log in?

I went into Failsafe Gnome. And then upgraded to Ubuntu 10.04 :)

---

### Post by Fibonacci on 2010-03-19
Update: I have succesfully booted and logged in on recovery mode.
Normal mode still doesn't work on any kernel, though.

---

