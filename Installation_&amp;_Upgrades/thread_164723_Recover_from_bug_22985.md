---
title: "Recover from bug 22985"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by lenehey on 2006-04-23
During install, computer (Acer 8100 series) gave black screen.  I diagnosed from ubuntu wiki that the problem was a mis-selection of the external monitor rather than laptop screen.  This is the bug report:

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/22985](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/22985)

I edited xorg.conf as described and logged in using username and password, and got as far as the gui.  However, I don't think the installation ever completed.  Network is not setup and I don't know the default root password.  Is there any way to resume the installation?  
:confused: 

Thanks for any help you can provide.

---

### Post by Sef on 2006-04-23
> However, I don't think the installation ever completed.

If it didn't complete, then I would reinstall the os.  If it did complete, then I would go into System > Administration > xxxx and fix your problems.

> I don't know the default root password.

Root is not set up on purpose.  Instead use sudo, which is a fake root, but it works well.  Just use your password that you need to log in with.

---

### Post by lenehey on 2006-04-23
> If it didn't complete, then I would reinstall the os. If it did complete, then I would go into System > Administration > xxxx and fix your problems.

To what end?  It would simply repeat the same error.  I have tried installing several times.  I am fairly new to Linux but I know my around the shell ok.  I have to say that I am completely soured on Ubuntu, and that is too bad, because I think it is really great in a lot of ways, but the installer is in serious need of a major overhaul. 

The installer does not give you an opportunity to edit the xorg.conf file prior to attempting to load X.  Even in expert mode, which I just tried.  The problem is, if you reboot before the installation process is complete, (e.g., in order to correct the xorg.conf file) it breaks the installation and never resumes.  The installer goes directly from installing X to *attempting* to boot X.  That prevents any work-arounds for the inevitable problems like I am experiencing.

> Root is not set up on purpose. Instead use sudo, which is a fake root, but it works well. Just use your password that you need to log in with.

That is just stupid.  At least in expert mode, I noticed, you can set a root password.  You should be at least given the option of setting up root during the normal setup.  I don't like my computer to make decisions like that for me.  If I did, I would just stick with Windows. :-#

---

