---
title: "Hibernate does not work after update from 13.10 to 14.04?"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by ziegler-g on 2014-04-26
I have just updated my Xubuntu 13.10 to 14.04. Did not change  anything.  Suspend-to-ram (standby) and hibernate (suspend-to-disk) both worked  well in  13.10.

  Now hibernate does not work any more (suspend-to-ram still works).   The machine seems to suspend to disk, but after a restart, I just get a   black screen and nothing happens any more. The power LED and the WiFi LED are lit; apart from that, my laptop does not show any sign of life. Then I have to push the power button for some seconds to force a complete restart. When I then log into Xubuntu, it says "system error detected".

I still can trigger a suspend how I could do it in 13.10:

On the logout dialogue, I still have the two  options "standby" and "suspend". When I click  "suspend", it does this incorrect hibernate, but does not  wake up  correctly. 

*sudo pm-hibernate* does exactly the same: tries to go  into hibernate, but does not wake up.

Everything worked fine with 13.10. What can I do?

Greetings.

---

### Post by ziegler-g on 2014-05-01
Any hints from anyone? Please help me!

---

### Post by LastDino on 2014-05-01
Maybe, you can try to re-install fresh copy. I know it is slightly troublesome but it will save you lot of agony.

Don't forget to take back-up.

---

### Post by ziegler-g on 2014-05-01
Thank you. As a last resort, I could try this (even it is not guaranteed that hibernate will work again then). But if so, what is an update worth? Sould this not be fixed in an LTS??? I mean, it was working before, so there must be something wrong with the hibernating software now...

---

### Post by bapoumba on 2014-05-01
May be here : [http://ubuntuforums.org/showthread.php?t=2219403](http://ubuntuforums.org/showthread.php?t=2219403)

---

### Post by ziegler-g on 2014-05-01
Thank you, but no, the thread you mention is about how to get a "hibernate" button on the logout dialogue, under the premise that "sudo pm-hibernate" already works on the command line. My pm-hibernate does not work any more since the upgrade and I do not know how to find out the reason why. My laptop is definitely able to hibernate. I have been doing this for years...

---

### Post by Ralph L on 2014-05-01
It been a long time since I have used xubuntu.  I currently run ubuntu 12.04.  Hibernate was omitted on it supposedly because it had bugs.  Here are my notes on getting hibernate to run on ubuntu 12.04.  Don't know if this will work on xubuntu.

 19  Enable Hibernate.  See [http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html](http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html) .
 19.1  Open Terminal and enter following command: 
sudo gedit /var/lib/polkit-1/localauthority/50-local.d/hibernate.pkla 
 19.2  copy and paste the following code in file:
[Re-enable Hibernate]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
 19.3  Restart to see hibernate option.

---

### Post by ziegler-g on 2014-05-01
Thank you, but the problem is not to enable hibernating in the GUI. I already have got the "hibernate" button in the logout dialogue. The problem is that the hibernating process itself is broken since the update. A
```
$ sudo pm-hibernate
```
worked correctly under 13.10. Now it "hibernates down" the laptop, but it does not wake up correctly any more. I have no idea how to debug the problem.

What I mean is this:
```
$ if pm-is-supported --hibernate; then echo "SUPPORTED"; fi
SUPPORTED
```
Nevertheless, a [FONT=courier new]pm-hibernate[/FONT] fails since the update.

---

### Post by bapoumba on 2014-05-01
Not sure these will help you ..
[http://ubuntuforums.org/showthread.php?t=2111580](http://ubuntuforums.org/showthread.php?t=2111580)
[http://ubuntuforums.org/showthread.php?t=1981271](http://ubuntuforums.org/showthread.php?t=1981271)
[http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/)

---

### Post by Branimir_Maksimovic on 2014-05-01
Try to remove cryptsetup package. I had same problem and after removing this package waking from hibernate worked again.

---

### Post by ziegler-g on 2014-05-10
cryptsetup is not installed.

This problem drives me crazy. After the updates of the last days (I think there was a new kernel, too), hibernate suddenly started to work in a magical way without me having changed anything (I already had given up). Now I have just noticed a failure on wakeup again and then tried several hibernates/wakeups in a series: It sometimes works, sometimes it does not work and I have to reboot.

There are so many problems after the update that I must declare this 1-click-update process as failed: Hibernate does not work correctly anymore, I always get a "system problem detected" dialogue on login, the logout dialogue has disappeared (i.e., I cannot switch user or directly shut down the machine, I can only logout and then shut down), pidgin always pops up on login without me knowing how to stop that, xfburn and brasero crash when trying to burn a CD, the notification area is empty, ...

I think the only clean solution is to install 14.04 from scratch. Unfortunately.

---

### Post by ziegler-g on 2014-06-01
A fresh install of 14.04 did not help either. The problem remains... What can I do?

---

### Post by ziegler-g on 2014-06-19
After two months of investigation (no one could solve the problem so far), I found that under the newest Debian (XFCE) with kernel 3.2.0 hibernation works correctly. The same holds for Linux Mint Debian Edition (LMDE-201403), which is based on Debian. 

Hibernation does *not* work under the newest Linux Mint 17 "Qiana", which is based on Ubuntu, nor under the newest Fedora 20, nor under Xubuntu 14.04. They all have a kernel version around  3.13.0.

So my conclusion is that there is something wrong or misconfigured with the newest kernels, and since the distributions that are not directly based on Debian use the newest kernels, their hibernation does not work correctly, whereas the Debian kernels do work.

---

### Post by bapoumba on 2014-06-19
If you have spare space on your machine, maybe you could try Utopic which comes with the 3.15 kernel [http://packages.ubuntu.com/utopic/linux-generic](http://packages.ubuntu.com/utopic/linux-generic)
Or try a live boot ? The devel Ubuntu version is subject to bugs.

---

