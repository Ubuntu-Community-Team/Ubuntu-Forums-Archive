---
title: "After update, can't boot into Ubuntu unless after booting into Windows and restarting"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by iknik on 2010-07-29
Well, this is an interesting one. I’ve been using Ubuntu for some months now (started with 9.10, upgraded to 10.04 a while ago) on a dual boot system (Windows XP being the other OS) I have encountered a number of bugs and errors already. Most were only slightly annoying and easy to fix, one was a severe problem caused by a bug in GRUB. But this is the most exotic error I’ve encountered so far.

After installing updates in Ubuntu yesterday, the update manager told me to restart. As I needed to do something in Windows, I chose restart and rebooted into Windows. When I was finished, I shut down my computer. After that, I couldn’t boot into Ubuntu anymore.

Back when everything was fine, I used to get a simple start-up screen giving me the option to boot into Ubuntu or Windows XP. And after that, I got the GRUB screen giving me a number of options: Ubuntu, Ubuntu recovery mode, Ubuntu using an older kernel, etcetera. Now I don’t get the GRUB menu anymore. I just a black screen saying ‘(hd 0,0) NTSF5:’ for a split second, then the system reboots. This happens no matter how often I try to boot Ubuntu.

Here’s the interesting part: if I boot into Windows, choose restart, and then boot into Ubuntu (i.e. without shutting the system down) it works fine. But when I’m in Ubuntu and choose restart, the problem is back. So right now the only way for me to start Ubuntu is to start Windows, restart and boot into Ubuntu. I tried repairing packages in recovery mode, but that didn’t work. I tried booting into Ubuntu using kernel 2.6.32-23 (instead of the default 2.6.32-24) but it behaved exactly the same. 

I guess the cause of the problem is me rebooting into Windows instead of Ubuntu after the update, though I don’t understand how it’s possible that a mistake made so easily is allowed to cause such severe misbehavior. I have no idea how to fix this, apart from a complete reinstall. And if that’s the only option, I’m pretty sure I don’t want to reinstall an OS that can break beyond repair after an update. Any ideas?

---

### Post by Jahid65 on 2010-07-29
I think updating grub will solve the problem. Boot into Ubuntu & run the command in terminal
```
sudo update-grub
```

---

### Post by iknik on 2010-07-30
That worked, thank you!

Edit: well, it worked temporarily, now the problem's back. I'll reinstall Grub later on to see if that works.

---

### Post by iknik on 2010-08-05
Nope, that didn't work either. Is there an easy way to roll back the last updates (one of these is definitely the cause of the problem) and then apply them one at a time, to see which one of them causes this behaviour? This is the log of the latest update:
> 
Upgraded the following packages:
apt (0.7.25.3ubuntu9) to 0.7.25.3ubuntu9.1
apt-transport-https (0.7.25.3ubuntu9) to 0.7.25.3ubuntu9.1
apt-utils (0.7.25.3ubuntu9) to 0.7.25.3ubuntu9.1
base-files (5.0.0ubuntu20) to 5.0.0ubuntu20.10.04.1
eclipse-platform-data (3.5.2-2ubuntu4.1) to 3.5.2-2ubuntu4.2
eclipse-rcp (3.5.2-2ubuntu4.1) to 3.5.2-2ubuntu4.2
firefox (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) to 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
firefox-3.5 (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) to 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
firefox-branding (3.6.7+build2+nobinonly-0ubuntu0.10.04.1) to 3.6.8+build1+nobinonly-0ubuntu0.10.04.1
gdm (2.30.2.is.2.30.0-0ubuntu2) to 2.30.2.is.2.30.0-0ubuntu3
icedtea-6-jre-cacao (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
icedtea6-plugin (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
libdbusmenu-glib1 (0.2.9-0ubuntu3) to 0.2.9-0ubuntu3.1
libdbusmenu-gtk1 (0.2.9-0ubuntu3) to 0.2.9-0ubuntu3.1
libequinox-osgi-java (3.5.2-2ubuntu4.1) to 3.5.2-2ubuntu4.2
linux-generic (2.6.32.23.24) to 2.6.32.24.25
linux-headers-generic (2.6.32.23.24) to 2.6.32.24.25
linux-image-generic (2.6.32.23.24) to 2.6.32.24.25
linux-libc-dev (2.6.32-23.37) to 2.6.32-24.38
openjdk-6-jre (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
openjdk-6-jre-headless (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
openjdk-6-jre-lib (6b18-1.8-0ubuntu1) to 6b18-1.8-4ubuntu3
software-center (2.0.5) to 2.0.7
sreadahead (1:0.100.0-4.1) to 1:0.100.0-4.1.2
thunderbird (3.0.5+build2+nobinonly-0ubuntu0.10.04.1) to 3.0.6+build2+nobinonly-0ubuntu0.10.04.1
ubuntu-system-service (0.1.20) to 0.1.20.1
ureadahead (0.100.0-4.1) to 0.100.0-4.1.2
xulrunner-1.9.2 (1.9.2.7+build2+nobinonly-0ubuntu0.10.04.1) to 1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1

Installed the following packages:
linux-headers-2.6.32-24 (2.6.32-24.38)
linux-headers-2.6.32-24-generic (2.6.32-24.38)
linux-image-2.6.32-24-generic (2.6.32-24.38)


---

### Post by confused57 on 2010-08-05
Dell has a program called DataSafe, which can cause this behaviour:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
Some other manufacturers have similar programs to protect the mbr.

---

### Post by iknik on 2010-08-05
Thanks for the help. However, my problem is pretty much the opposite: Grub fails *unless* I boot and restart Windows first. So if there is a Windows program writing to my mbr, it's what keeps Grub alive. However, I doubt that I have such a program: I built my computer myself (so it's not a pre-installed Dell or HP or somesuch) and I have no recovery tools installed.

---

### Post by oldfred on 2010-08-05
While this is not exactly your problem it may be related. If grub sees an error on booting it sets a flag. After grub updates or boots from windows then grub does not see flag??

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail)

---

### Post by iknik on 2010-08-05
Thank you for the tip. Unfortunately, it doesn't change the computer's behaviour. I also reinstalled all the linux-something packages that came with my latest update, which didn't help either. And I've tried to narrow it down a bit:

1. When I log into Windows and restart, Grub works most of the time.
2. When I reinstall grub or linux-headers (and possibly anything else) in Ubuntu and then restart, Grub works.
3. When I boot Ubuntu (after booting into Windows & restarting) and do a hard reset before I get Ubuntu's login screen, Grub works.
4. When I do none of the above, Grub resets spontaneously before showing the startup menu.

I'm too much of a Linux-noob to make any sense of this. It almost looks like it's not Windows but Ubuntu that somehow messes up the mbr (on logging in).

---

### Post by iknik on 2010-08-05
I also tried to [replace wubildr]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10"), but that didn't work.

---

### Post by oldfred on 2010-08-05
While I do not expect this to show anything, it does show everything related to booting. But since you boot sometimes, I do not expect this to highlight any issues:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by ghaspias on 2010-08-19
> **iknik said:**
> I also tried to [replace wubildr]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10"), but that didn't work.

I seems you are using wubi - ubuntu installed inside windows - is that true?

That would be a totally different issue than for a regular install...

---

### Post by iknik on 2010-08-22
> **ghaspias said:**
> I seems you are using wubi - ubuntu installed inside windows - is that true?
That was true, yes (I've made a fresh install of Linux Mint a few weeks ago).

---

