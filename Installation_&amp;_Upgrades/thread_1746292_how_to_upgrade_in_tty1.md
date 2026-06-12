---
title: "how to upgrade in tty1?"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by neba on 2011-05-01
I'm having issues with my graphic drivers so during boot up I only can get to tty1-6 I am hoping if I upgrade from 10.10 to 11.04 that that will fix it. I can not get passed tty1, I have the new distro on my a iso cd. can I upgrade through the cd? 
Thank you 
neba

---

### Post by MAFoElffen on 2011-05-01
> **neba said:**
> I'm having issues with my graphic drivers so during boot up I only can get to tty1-6 I am hoping if I upgrade from 10.10 to 11.04 that that will fix it. I can not get passed tty1, I have the new distro on my a iso cd. can I upgrade through the cd? 
Thank you 
neba
What problems are you having now, with the 10.10 version on what hardware?  

11.04 may have some graphics updates that may help or not-- depends.  

Upgrading from a CD versus from apt-get or aptitude?  If you wanted a fresh install and didn't care if you lost data or previous settings, then a fresh install may be an option...

But it really still depends on the original questions I asked you... doesn't it?

Seems to me, if you can boot a LiveCD and see graphics, then there is a way to fix your graphics problems.

Something you might want to read before answering those questions is this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by MAFoElffen on 2011-05-01
Still tap-dancing... let me backup a litlle.

Since you are tty, I could have just told you to type into the commandline:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```which would update your resource list, apply all pending updates/upgrades... before it upgraded your system to a new distribution release-- **BUT...**

That would upgrade your system to the previous configurations and driver types... which it sounded like you are not happy with and think are "broke." (The same problems may and most likely will exist)

A clean install off a LiveCD-- Well there have been improvement in drivers and the install process.  It would be a fresh install.  It may still have the same problems...

So learning more about your problems and what you want to "resolve" may be a precursor to jumping into something too fast and making them worse.

---

### Post by neba on 2011-05-01
Thank you for the fast reply.  i tried:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
And it said that there is nothing to update or my system is fully updated. I don't want to do a fresh install because I have a lot of information I can't lose and I have dual boot set up. I don't know grub2 enough to find the codes for win7. I know that I am having issues with my nvidia drivers. 
should sudo apt-get dist-upgrade upgrade me to 11.04? or is there more I need to type?
thank you for your help
neba


This is exactly what I get when I type  'sudo apt-get dist-upgrade':
w: unable to read /etc/apt/preferences.d/ - directory exists

---

### Post by neba on 2011-05-07
bump

---

### Post by foresto on 2011-05-07
You'll want to follow the [Network Upgrade for Ubuntu Servers]("https://help.ubuntu.com/community/NattyUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20%28Recommended%29") instructions.

---

### Post by neba on 2011-05-07
Thank you foresto. That did it. I tried that command before but I didn't change the prompt to normal. Everything is working again. ahh Its nice to have ubuntu back and working. Thanks again

---

### Post by MAFoElffen on 2011-05-07
> **neba said:**
> Thank you foresto. That did it. I tried that command before but I didn't change the prompt to normal. Everything is working again. ahh Its nice to have ubuntu back and working. Thanks again
(LOL) So your "Chief Complaint" or what you "said" you wanted, was to upgrade from the command line... You are now upgraded and are up-to-date.

Like I suspected, what you "needed"--> Was to have your graphics work correctly... which is why in post 2, I asked you some questions, about... no matter.

Please read this sticky:
 [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
and please tell us: 
1. What is working and what is not.
2. What make and model computer.
3. What Video hardware.
4, Describe your graphics issues.

---

