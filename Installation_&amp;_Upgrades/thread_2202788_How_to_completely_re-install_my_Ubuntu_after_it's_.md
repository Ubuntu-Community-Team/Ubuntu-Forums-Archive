---
title: "How to completely re-install my Ubuntu after it's broken?"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by 95kreaninw95 on 2014-01-31
My setup is Ubuntu 12.04 LTS 64 bit and Windows 7 64 bit (dual-boot). Yesterday, I tried to install new AMD GPU driver (13.12) on my laptop (Intel + Mobility Radeon HD5650). After reboot, my screen gone dark. I had tried to fix it but fail (wiki.cchtml.com methods and Boot-Repair).

Now I want to re-install Ubuntu while keep my data in /home. I setup separate partitions for /root , /home , /boot , and swap. I want to know that, if I format /root , /boot , and swap (to make sure I have clean system files) and left /home untouched, will I be able to access my files in /home? Will my file in /home lost?

Thanks in advance.

---

### Post by Bucky Ball on 2014-01-31
*Thread moved to **Installation & Upgrades**.*

Easy. Choose 'Something Else' at the partitioning section of the install. You don't need to format /swap (you can't). Install to / and make sure the other partitions apart from / and /boot are unticked and marked 'Do not use'.

That's it. Good luck.

PS: Did you actually post a thread here to try and fix your problem before deciding to reinstall??? Boot-repair is not going to fix a graphics problem. You might want to post in ***Multimedia & Video*** about your graphics issue before taking such drastic measures as a reinstall. Sounds like if you simply remove the driver things will be as they were. A reinstall is a huge leap for what seems like it is a minor problem. ;)

PPS: These two commands should get rid of the offending drivers:
```

sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```

You just need to get to a terminal to input them.

---

### Post by 95kreaninw95 on 2014-01-31
Hi, thanks Bucky Ball. I just want to make sure, I can format / and /boot without losing my data in /home right?

I read it from here [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) It says, "...[COLOR=#333333][FONT=Ubuntu]select Ubuntu system partition, set its mount point as "/" (keep the same format type, the same size, and **untick the "Format" checkbox**)". I'm quiet confuse here. [/FONT][/COLOR]:-k

PS: I'm quiet new in Ubuntu and I don't know if I will cause more further damages to the system. But I had tried to re-install the driver in tty both open source and proprietary one without success.

---

### Post by ajgreeny on 2014-01-31
Don't re-install any drivers; just remove the ATI fglrx as BB said and you should get back to the open source driver only.  You can then decide if you want to try perhaps installing another version of the ATI driver.

---

### Post by 95kreaninw95 on 2014-01-31
I removed fglrx driver as BB said before install a new one. In fact, this problem happens only after AMD driver 13.1. I have upgraded from 12.4 > 12.6 > 12.8 > 12.10 > 13.1 without fail. But fail to install 13.4 and also 13.12 driver. And this time with 13.12, remove(purge) 13.12 and revert back to open source driver doesn't work. That's why I'm thinking about this method.

When I look into 13.4 release note ( [http://support.amd.com/en-us/kb-articles/Pages/amdcatalyst13-4linreleasenotes.aspx](http://support.amd.com/en-us/kb-articles/Pages/amdcatalyst13-4linreleasenotes.aspx) ), I found that there's a known issues. One of that is, [373909]: Driver install via .deb package will cause OS desktop corruption. I don't know if it's fixed in 13.12 yet. ( wiki.cchtml.com recommends users to build .deb packages first then install the driver via the packages. ) Even though, I tried install using .run script, it also fail. I have to re-install Ubuntu many times because of this issue.

In fact, before I tried to install 13.12 driver myself yesterday, there's AMD driver updates from Update Manager (pre-release update). After reboot, I can't use Ubuntu anymore.

---

### Post by Bucky Ball on 2014-01-31
Ah! 13.04!!! It's not supported anymore. Wrong way, go back. You won't get far with this as you are running an unsupported release and may be backed into a corner. Forget what the release notes say. You can keep running this if you like but it will become more and more of a security risk if it is online and expect continued breakages ...

You're right. A fresh install (12.04 or 13.10 are both directly upgradeable to 14.04 LTS when it is released in April) may be the path of least resistance.

---

### Post by 95kreaninw95 on 2014-01-31
I'm running Ubuntu 12.04 LTS 64 bit and tried to install AMD driver 13.4 and 13.12 but fail. I'm not running Ubuntu 13.04.

---

### Post by Bucky Ball on 2014-01-31
[QUOTE=95kreaninw95 ] But fail to install 13.4[/QUOTE]

My mistake. Misread. ;)

---

### Post by oldfred on 2014-01-31
> I read it from here [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) It says, "...[COLOR=#333333][FONT=Ubuntu]select Ubuntu system partition, set its mount point as "/" (keep the same format type, the same size, and **untick the "Format" checkbox**)". I'm quiet confuse here. [/FONT][/COLOR]:-k

That is for those who do not have a separate /home, but a /home that is inside / (root). It often is called a "dirty" install since you do not reformat. But it will replace all the normal install files and will also replace/overwrite all configuration files. Any files you added then are not overwritten so it preserves your data in /home, but not necessarily all settings. 

If you have a separate /home, probably better to reformat / (root), but when you mount your /home you MUST NOT tick the format box or you lose all your data and settings that are in /home.
If you added a lot of applications, and can still get to command line best to make a list of installed apps to make it easy to reinstall. Also if you configured hardware, you may want those settings from /etc. Also custom grub configuration or scripts that my be in system. If all that is well backed up then it is easier to restore everything.

---

### Post by 95kreaninw95 on 2014-02-04
[COLOR=#ff0000]**WARNING!!! MOBILITY RADEON HD 5000 SERIES USERS!!! DO NOT INSTALL LATEST AMD DRIVER!!! ANYTHING BEYOND 13.1 WILL NOT WORK!!!**[/COLOR]

It's a bug. [http://ati.cchtml.com/show_bug.cgi?id=831](http://ati.cchtml.com/show_bug.cgi?id=831)

You have 2 choices. 1. Stick with 13.1 driver and 3.5 kernel. 2. Use open source diver with latest kernel but over heating issue.

Please note that, in Ubuntu additional driver - post-release updates driver also is not support your card. [COLOR=#ff0000]**DO NOT INSTALL!!!**[/COLOR]

---

