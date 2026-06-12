---
title: "Problem with upgrading from 14.04 LTS to 14.10"
date: 2015-07-25
forum: Installation &amp; Upgrades
---

### Post by hrvoje2 on 2015-07-25
Hello good people! ):P I'm kinda new to linux, so I realy need help. I've been using linux for 6 moths now, and I had no issues with it. I had 14.04 LTS on my laptop, and I realy loved it! :p Few days ago I wanted to upgrade my system to 15.04. So I tried downloading the upgrade but computer said that I had small amount of space on /boot. So I cleaned my /boot, without cleaning that newest kernel that computer uses. Then I went to system upgrade and started donwloading the upgrade. The upgrade that I was offered wasn't 15.04, it was 14.10. So I said to myself why not. Let's try that 14.10 first. Then when it was about a half on the process my laptop froze. I couldn't do anything. I turned it off. Then when I turned it back on, it didn't want to boot up to the main screen. It only showed me a message box for few seconds, that says something like this: " Computer can't boot: do you want to : CANCEL, or REPORT UBUNTU?" I'm  not complitely sure about that part, and I  can't come to that point anymore. ):P Next thing I did, was went to BIOS. There I've changed BOOT MODE from UEFI to LEGACY. Now when I turn my laptop on, it shows me the GNU GRUB menu. Then if I write "boot" it says "Kernel must be loaded befote booting." If I write "kernel"  then it says "Filename must be either an absolute pathname or blocklist". What should I do to fix it? Is there any possible way of fixing it? I hope that everything I said makes some sense to you guys.  p.s. Sorry for the grammar and the long post, english is not my native language. :p Thanks in advance! ):P

---

### Post by dino99 on 2015-07-25
Sadly you have made what is the worst idea: shutting down a broken system; never do that, but try to fix it.
Now the only solution for you is to install Vivid, as utopic is now closed.

---

### Post by kansasnoob on 2015-07-25
Yikes :eek:

14.04 is an LTS version, supported until April 2019. But 14.10 is an interim release and just reached EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You really have only two choices now:

(1) Reinstall 14.04 which is supported until April 2019

(2) Install 15.04 which is supported until January 2016

If you choose option #2 the installer (live DVD/USB) may give you the option to upgrade from the older version to 15.04 but I'd only select that option if Ubuntu is the only OS on that system - NOT if it's a dual-boot with Windows!

Regardless of which option you choose **[COLOR="#FF0000"]you should always back up any important data before reinstalling any OS![/COLOR]**

---

### Post by Bucky Ball on 2015-07-25
> **kansasnoob said:**
> 
(1) Reinstall 14.04 which is supported until April 2019

(2) Install 15.04 which is supported until January 2016

That's about the size of it.

---

