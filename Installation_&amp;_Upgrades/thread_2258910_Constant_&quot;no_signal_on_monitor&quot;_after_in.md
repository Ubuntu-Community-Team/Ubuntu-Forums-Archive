---
title: "Constant &quot;no signal on monitor&quot; after installing updates. 14.04 Lts."
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by Darkhaund on 2014-12-31
OK GUYS.. I tried to research here in these forums and at some other places, and I am sad to say I HAVENT found a solution for answer for my problem.
I like ubuntu alot and I use it on my desktop at work. I have been going solid for 2 years now. And despite that , I still consider myself a below average user.

Anyhow, i have had to reinstall my system from scratch like 4 times after this update that my system suggest. The last time I did a little more resarch and I was able to get into the GRUB menu, boot from an "older" kernel version, and then in terminal erased the "new kernel". Every SINGLE time I have done this update after my machine reboots i see the UBUNTU purpleish creen with the orange dots, and then after that my monitor goes TOTALLY BLACK like it is unplugged and it says no signal.

Problem is that now i am affraid to update this again, and everytime I login it promts me if i want to install
This is what it is suggesting I install

I would greatly appreciate feedback
Here is the link to the screenshot with that it is me suggesting to install.
What of this updates is breaking my system and what can i do to avoid this?

[http://www.darkhound.net/pics/ubuntu.png](http://www.darkhound.net/pics/ubuntu.png)

---

### Post by ibjsb4 on 2015-01-02
Simple way to update without upgrading the kernel is manual update.
```
sudo apt-get upgrade
```
What old kernel works?  Is the new kernel a version upgrade?

---

### Post by grahammechanical on 2015-01-02
First of all, we are not forced to install updates. We can decline the offer and we can even instruct Update Manager not to notify us of any updates at all. Just click the button labelled Settings. We can set Automatically check for updates from Daily, to Every 2 Days, or Weekly or Every fortnight or even Never.

Secondly, we can disable the download of individual packages. You will see in your image a tick mark against those packages that will be installed. Remove the tick mark and the package will not be downloaded and installed.

If a kernel upgrade is breaking the desktop then it is, in my opinion, a conflict with a proprietary video driver. I would not recommend removing the newer kernel as Update Manager will simply want to install it again. This is what is happening is it not? You remove the new kernel and Update Manager installs It. You re-install and Update Manager installs a newer kernel. Well, it would, would it not? It is programmed to do that.

We need to change our programming to get out of situations like this. Simply do not use that kernel. Keep loading the old kernel. And keep updating as an update will most likely fix what was wrong with the kernel. And maybe try another video driver. 

Regards.

---

### Post by Darkhaund on 2015-01-14
Thank you
For the time being i will not make any upgrades AT ALL.
I am trying to learn LINUX/UBUNTU and every single time i do this update it breaks my system.

---

### Post by efflandt on 2015-01-14
What video card/chip are you using and are you using default video drivers, Ubuntu packages from normal repositories or a ppa, or drivers from another source? If you use packages compatible with Ubuntu, things should properly update automatically. But if you install video drivers using a script from the manufacturer's site, Ubuntu's package manager may not know about them, so you may need to run that script again after any kernel updates. Or such drivers might not be compatible with something else.

---

