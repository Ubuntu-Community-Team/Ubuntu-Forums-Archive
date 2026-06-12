---
title: "Ubuntu 14.04 LTS login-loop after installing NVIDIA driver .run file"
date: 2016-04-11
forum: Installation &amp; Upgrades
---

### Post by samrroyall on 2016-04-11
So I have a Dell Inspiron 15 7559 (NVIDIA GeForce GTX 960M) running Windows 10 and Ubuntu 14.04 LTS. I was able to install Ubuntu off of a live USB after having added the kernel parameters "quiet splash nomodeset acpi=off" in grub. After using the system for a week or so, I would get random freezes (keyboard, mouse, and screen) which would force me to hard reset. After a this happened a few times, I got the "low graphics warning" and through the command-line I was able to follow the instructions posted by @jempa333 here ([http://ubuntuforums.org/showthread.php?t=2263316](http://ubuntuforums.org/showthread.php?t=2263316)). These worked perfectly except for the fact that I was put into a login loop. I tried "sudo chown user:user .Xauthority" and "sudo mv .Xauthority .Xauthority.bak" to no avail. I then added the kernel parameter "intel_idle.max_cstate=0" and "...=7" (updating grub both times) and still no fix. Does anyone have any suggestions? Thanks.

down vote [favorite]("http://askubuntu.com/questions/756319/14-04-login-loop-after-installing-nvidia-driver-run-file#")[COLOR=#777777][/COLOR]

---

