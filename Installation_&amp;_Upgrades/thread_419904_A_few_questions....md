---
title: "A few questions..."
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by jiggling_john on 2007-04-23
Ok, so this will probably make me look VERY thick, but bear with me as I've only switched to linux in the last few months...

first up, I used the beta version of ubuntu 7... my question is, if I've been doing all the updates, does this mean my system is now the same as the final release version?

The second question, and perhaps this isnt the right place to ask, but... how does linux react to hardware changes? If i changed motherboard and cpu for example, would it break it entirely like windows would break...?!

thanks in advance

---

### Post by pepsi_max2k on 2007-04-23
> **jiggling_john said:**
> first up, I used the beta version of ubuntu 7... my question is, if I've been doing all the updates, does this mean my system is now the same as the final release version?

The second question, and perhaps this isnt the right place to ask, but... how does linux react to hardware changes? If i changed motherboard and cpu for example, would it break it entirely like windows would break...?!

1. yup.

2. yup.


Actually, for 1, it potentially could break if you had a load of really old packages installed that weren't compatible with the newer ones. It's mostly a problem for upgrading from much earlier releases though, not beta 7.04's. and even then it works flawlessly a lot of the time.

And for 2, I expect a load of people to now say i'm wrong. In my experience with suse, adding any kind of new hardware or peripherals does absolutely nothing, very little auto detection like in windows, and you have to install / configure them yourself. obviously with a new mobo and cpu this would be near hell to do, if possible at all. and you don't have a load of cd based drivers that can be installed with a double click either. but you might get lucky, could be the kernel has drivers for everything and actually will auto detect it / configure it on it's own, and ubuntu could be much better than suse at it (and it does have much better guides in the help section). given that *EVERYTHING* i've installed on a pre-existing suse os has needed days or weeks to get working, and that's joysticks, sound cards, monitors, remotes, hard drives, tv cards etc etc, then i wouldn't fancy doing it myself. clean install is usually much easier to do :)

---

### Post by tommcd on 2007-04-23
1) AFAIK if you kept updating from fiesty beta it should lead you right into the final release of fiesty. Check your /etc/apt/sources.list and make sure all repositories say fiesty.
------------------------------------------


To check what version you are running, type in terminal " cat /etc/issue" You should get something like:
-------------------------------
tom@tom-desktop:~$ cat /etc/issue
Ubuntu 7.04 \n \l

tom@tom-desktop:~$ 
---------------------------------------------------------------------
I'm not sure what the "\n \l" mean.

Or try this:
--------------------------------------------
tom@tom-desktop:~$ sudo lsb_release -a
Password:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
tom@tom-desktop:~$ 
--------------------------------------------------------------




2) I have read that, even if you change your motherboard and CPU, ubuntu will often boot up just fine. Worst case option is you have to reinstall.

---

### Post by jiggling_john on 2007-04-23
ah right... it seems im all up to date then. Thats rather good.

as for the hardware issue... if I did have to do a reinstall of the os, doesnt that mean i lose all the customisations i've made and packages i've installed?

---

### Post by tommcd on 2007-04-24
Yes, if you reinstall you will have to reinstall all of your programs. If you have a separate /home partition, all the hidden configuration files (files that start with a period) will be retained, and your configuration for those programs and your desktop also, will be retained when you reinstall those programs.

---

