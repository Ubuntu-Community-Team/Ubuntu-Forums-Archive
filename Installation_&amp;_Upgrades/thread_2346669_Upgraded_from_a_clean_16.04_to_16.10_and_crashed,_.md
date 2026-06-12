---
title: "Upgraded from a clean 16.04 to 16.10 and crashed, now stuck at plymouth logo"
date: 2016-12-17
forum: Installation &amp; Upgrades
---

### Post by davmanypsp on 2016-12-17
Hi, sorry if my English is not correct. 

I installed Ubuntu 16.04 Unity a few months ago (a clean install), and today decided to upgrade it to 16.10. So I enabled the "Notify me for any Ubuntu version" option in Software & updates settings, and I started the upgrade through the Software Updater application. It started to download the new packages, so I left it alone for 4 or five hours. When I returned, the window was frozen (greyed out) and I did a hard reset (REISUB). Now the computer doesn't boot, it stays forever at the Ubuntu plymouth logo.

How can I try to fix this? I don't mind if I have to reinstall it (I'm already downloading the 16.10 iso), but I would like to give it a try, and maybe learn something new in the process.

Thanks in advance.

---

### Post by davmanypsp on 2016-12-17
I learned how to solve it: Recovery mode, sudo dpkg --configure -a, sudo apt-get install -f, sudo apt-get update, sudo apt-get upgrade, sudo apt-get dist-upgrade. 

That fixed it. However, the Ubuntu Software Center was gone, so I had to install the package software-center.

Is there any way to check if all the default packages are installed?

Thanks.

---

### Post by ian-weisser on 2016-12-18
Try: 'sudo apt install --reinstall ubuntu-desktop'
All packages in an Ubuntu Desktop system, directly or indirectly, depend upon that metapackage.

Though if you can login to a Unity desktop and apt is not complaining about missing or unconfigured packges, you probably have everything you need.

---

### Post by davmanypsp on 2016-12-21
Ok, thanks!

---

