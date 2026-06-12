---
title: "Unable to log in"
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by derrickgriffin32 on 2016-02-24
I do not know if this is the right place to post this thread, but I have a frustrating problem. I recently downloaded a [driver update]("http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64") file for my amd graphics card (which is the first download at 56 MB, more on that later), and when I installed the package on the app store it gave me a warning message saying the file is out of date or something. I didn't really pay much attention to it, nor did I write down the name of the package. I then restarted the computer and when it got to the login screen, a couple seconds after, the screen would turn black and the keyboard would be disconnected from use. Since then, I have been trying to find a way to fix the problem by searching online, but without the name of the package I am doomed from ridding myself of this headache. What I simply ask from anyone who reads this and wants to help is for you to download the file stated earlier and tell me what the application name is on the ubuntu store. I am hoping that I will be able to recover my computer once I eradicate this file from existing on it. To those who want nothing but to help others in need of a solution, I give you my thanks.

---

### Post by howefield on 2016-02-24
Are you able to boot to recovery mode ?

From there..

```
apt-get remove --purge fglrx*
```

should remove any package starting with the letters fglrx, ie the AMD drivers.

---

### Post by derrickgriffin32 on 2016-02-24
I entered the code, but it came up with a message saying:

W:Not using locking for read only lock file /var/lib/dpkg/lock
E:Unable to write to /var/cache/apt/
E:The package lists or status file could not be parsed or opened.

---

### Post by howefield on 2016-02-24
When you log in to recovery mode try this command...

```
sudo mount -o remount,rw /
```

This will mount the file system as read/write as opposed to the default which is read only. Then you should be able to run the apt-get command above.

---

### Post by derrickgriffin32 on 2016-02-24
I entered the second code and, after exiting to root mode, I was able to work the first code. I did a reboot of the computer and now things are back to normal. Thank you for your help, and for your quick response time.

---

### Post by howefield on 2016-02-24
You're welcome and congrats for following it through.

I'd recommend sticking to either the default open source driver installed by default, or the proprietary drivers in Additional drivers. The risk factor increases when you go outside of those.

---

