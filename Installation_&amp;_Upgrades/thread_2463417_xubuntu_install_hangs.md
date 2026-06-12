---
title: "xubuntu install hangs"
date: 2021-06-10
forum: Installation &amp; Upgrades
---

### Post by jvglynnjr on 2021-06-10
I am trying to install Xubuntu on a Toshiba Satellite laptop. I initially tried to install 18.04 from a USB flash drive, but the installer would hang no matter what parameters I set. I read a suggestion about trying an earlier version and then upgrading from that, so I then installed 16.04 from a USB drive. 

That seemed to work fine, and the computer worked well for several hours. I then attempted to upgrade but all attempts failed. The GUI became unstable. That is, it would work for a few minutes but then the mouse and keyboard would stop responding. 

Thinking that my software updates had caused this problem, I tried reinstalling 16.04 from scratch, but the problem persists. Now I can't get it to do anything for more than a few minutes before the mouse and keyboard quit. 

Did I do something to mess up the firmware? Is there a way to fix this without installing Windows?

---

### Post by ActionParsnip on 2021-06-10
Why 18.04 ? Why not 20.04 which is newer and supported for longer ?
Did you SHASUM / MD5SUM the ISO you downloaded to make sure it was complete and consistent ?

---

### Post by guiverc on 2021-06-10
Are you aware that *flavors* of Ubuntu only come with three years of supported life (*five years applies to Ubuntu Desktop, Ubuntu Server but not flavors*),

- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
-  UWN - [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses) highlights the EOL notices for Lubuntu/Ubuntu-MATE/Kubuntu/Ubuntu-Budgie

Xubuntu didn't announce EOL but refer [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) you'll see it's EOL was 29 April 2021.

From your description, it reads to me like

- hardware issues (*did you run ram tests, visually scan motherboard looking for swollen caps, check PSU, drive health etc*), or 

- lack of validation of the system (*no clues were given that you verified your ISO, or write to installation media, checked logs for clues, did SysRq commands work to direct kernel to cleanly reboot/shutdown or was it frozen which implies hardware issues are more likely; SysRq commands work even on a locked GUI session where mouse/keyboard (excluding SysRq) don't work*).

You also didn't provide any specs, did you go for 18.04 because your box is i386? or 32-bit x86? and that's why you're opting for *unsupported* software over supported releases?

FYI:  All of 16.04 is out of *standard* support (not just *flavors*).  See [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/) but does have ESM support, see [https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm](https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm)

---

