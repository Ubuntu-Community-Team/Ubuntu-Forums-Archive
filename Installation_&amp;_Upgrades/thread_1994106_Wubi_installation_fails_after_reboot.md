---
title: "Wubi installation fails after reboot"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by Slowe on 2012-06-02
I'm having trouble with an Ubuntu installation (installed using wubi, installed latest version, installed to a data partition on my HD.)... it will install fine, but after a reboot (dual booting with windows 7)... I receive an error and the screen gets "lines" across it and never finishes booting.

I'm running on an HP machine and have an external monitor attached.
I have installed a single application inside of Ubuntu (the application is ROS). But this error doesn't occur until after installation is complete and the machine has been running Windows 7 for awhile and has had an external monitor attached.

There is an error message that flashes very, very briefly and it says something to the effect of a ntfs error. 
I would appreciate any help you can provide.

Thank you.

---

### Post by critin on 2012-06-02
> **Slowe said:**
> I'm having trouble with an Ubuntu installation (installed using wubi, installed latest version,[COLOR=Red] installed to a data partition on my HD.[/COLOR])... it will install fine, but after a reboot (dual booting with windows 7)... I receive an error and the screen gets "lines" across it and never finishes booting.

I'm running on an HP machine and have an external monitor attached.
I have installed a single application inside of Ubuntu (the application is ROS). But this error doesn't occur until after installation is complete and the machine has been running Windows 7 for awhile and has had an external monitor attached.

There is an error message that flashes very, very briefly and it says something to the effect of[COLOR=Red] a ntfs error. [/COLOR]
I would appreciate any help you can provide.

Thank you.

Wubi installs to the Windows partition, not to a separate partition.    I haven't seen it give the user a choice of where to install.  To install to another partition you'd probably have to know Wubi very well.

I suggest studying this link deciding if you've done all the steps shown.  Wubi is easy to install normally and gives few problems.   Be sure you don't hard power off unless absolutely necessary--it can corrupt the ntfs system.  

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If you find you need to reinstall Wubi, uninstall through the Windows Add/Remove programs and install again.

---

