---
title: "Re-installing Natty to recover damaged filesystem"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by datoff on 2011-07-21
I have a current installation of 11.04. Recently, I updated the kernel, using the latest 2.6.38-10 update that I found via the normal update channels in Ubuntu. Lately, I've been experiencing som serious issues, however. My hard drive's S.M.A.R.T. status is saying it has a few bad sectors, and when I boot, now and then I'm seeing issues where it shows my hard drive has errors, and it refuses to autofix. I now cannot boot the *-10 kernel, and still have issues when booting using the "older versions of Linux Ubuntu with Linux 2.6.28-8 (generic)" option in my GRUB2 splash screen. I know that I haven't experienced any system errors when logging in as root. **"NOTE: I am aware that loggin in as root is not recommended, however, Linux is my ONLY OS on my machine, and I need to have access to the system to perform my work for my CST class."**
 
I've decided that perhaps I need to reinstall Natty to correct the issue, but before I do, I want to be certain that I can rescue my personal documents, etc. without backing up to external media, as I do not have the budget to afford an external hard drive, or dvd's. Can I, using the 2GB Live USB I have, re-install my os, and still preserve ONLY my user's Home folder?
 
**_[COLOR=red](NOTE: I HAVE SINCE RESOLVED THIS ISSUE. FOR THOSE OF YOU WHO WOULD LIKE TO KNOW, HERE IS HOW I DID IT:)[/COLOR]_**
[COLOR=#000000][/COLOR] 
First, I logged in as root, and copied the contents of my /home folder to root's home folder. Then, using the "userdel" command, deleted my user. Then, I deleted the /home folder with "rm -r /home//". Once that was done, via terminal, I used the "aduser" command to re-create my usual user account. Once that was done, I copied the files I needed most back to my home folder, and did a hard shutdown to force the computer to run fsck at boot. When it completed successfuly, and I logged in as my regular user, everything seemingly has returned to normal, and I'm no longer having any issues. As a sidenote, I am aware that Linux can, at times, get a virus or other type of malware, usually due to lack of experince on the part of the stupidest user using your box. I'm wondering, for purely academic reasons, if perhaps anyone might know of a virus or issue that could have caused this, so as to prevent it from happening again?

---

