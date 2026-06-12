---
title: "Installation type screen empty"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by nicholas9 on 2014-04-23
So, I was attempting to install Ubuntu alongside Windows 7 on a laptop, but the "installaton type" screen was empty (showed no partitions and only presented /dev/sda as device for boot loader installation). I googled around a fair amount, and found out that it probably had to do with dmraid being outdated and not handling the newest Intel technologies, which the Windows 7 partitions use.

I then removed dmraid using Ubuntu Live, and then tried to install. Now it did show the partitions, and everything was ok. I hadn't made any space for Ubuntu yet though, so I went back to Windows and shrinked its partition. Then when I booted into Ubuntu again, the "installation type" screen was empty again, exactly like it was in the beginning, even though dmraid was still removed.

Anyone know what the problem is and/or know how to fix it?

---

### Post by nicholas9 on 2014-04-23
Ok, I managed to fix it by removing mdadm (which I had installed when trying to fix the first problem), and rebooting. Now I have a different problem.

I installed Ubuntu, and it said the installation was successful. Then, I rebooted, but it would boot me straight into Windows. I booted up Ubuntu Live again and installed boot-repair, and used it to fix the booting problems. When I rebooted the computer again, the grub menu appeared and I chose to boot into Windows. The new problem arose when I rebooted the computer after that.

Right now, the computer does not boot into the grub menu or any of the operating systems, but simply loops the first loading screen when you turn it on over and over. I get the DELL Inspiron loading screen with F2 to Setp and F12 for Boot Options, and when it finishes loading (takes a couple of seconds), the screen goes black for a very brief moment, and it just does the same again. This makes the computer unusable for the time being, so would love it if anyone out there has any knowledge on it and/or knows how to solve it. Have tried booting into Ubuntu Live and doing boot-repair again, but to no avail...

---

