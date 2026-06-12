---
title: "Installtion Error - Power Manager"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by mastermarcus355 on 2008-09-09
So...I finally established a working wireless connection and the update manager said I had quite a few packages to download. I downloaded all of the packages and went to install them when it said it was going to a while. So naturally I left my laptop. When I came back to my laptop, it had frozen on the screen saver. I did a cold reboot and when it came to, Ubuntu wasn't quite the same. Meaning it looked like windows in safe mode. The update manager said there was an error with dpkg and told me to run a command in terminal to fix the problem. I did this and all seemed well when I rebooted again except when it came to the main screen an Installation Error popped up saying installation of configuration files for GNOME Power Manager were installed incorrectly and to contact the computer administrator for help. Oh and the mouse wouldn't work..it was stuck right in the middle of the screen. I know the cursor worked before it got to the main screen. I haven't found anyone else with this problem so therefore I'm stuck! HELP!

---

### Post by Pumalite on 2008-09-09
Get into Recovery Mode and run:
sudo dpkg --configure -a
swudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by mastermarcus355 on 2008-09-09
Thanks for the quick respponse! I should add that the error actually said...configuration of gnome power manager instalation files. I don't know if this makes a difference or not. I did try what you had suggested and an error came up after the first command. The error said...manager is in a very bad unstable state try to reinstall before configureing. I did go through the rest of the commands and then rebooted my machine but when ubuntu fired up it did that same thing again...only slower this time. lol I am able to use keyboard functions..just not my touchpad. Any other sugestions?? Thanks again

---

