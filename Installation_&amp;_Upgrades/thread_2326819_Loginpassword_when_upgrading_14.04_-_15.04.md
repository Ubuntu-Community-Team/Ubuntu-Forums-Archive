---
title: "Login/password when upgrading 14.04 - 15.04"
date: 2016-06-05
forum: Installation &amp; Upgrades
---

### Post by rune4 on 2016-06-05
Hi all,

I have been trying to update from 14.04 to 15.04 and I now receive these three images (attached) when booting. I have had Ubuntu for many years but never used login (only password) so I do not recall the login. Do you have any advice on how to proceed?

Best Rune

---

### Post by grahammechanical on 2016-06-05
You login with your user name and then enter the password. But it will only get you a Linux command line.

First, Linux loads. Then at some point Ubuntu logs into to Linux using our user name and password. Then, if all is well with our installation, the Light Display Manager will load the usual graphical login screen. Unless we have the system set to login automatically. In that case the desktop environment should load.

That is the normal procedure but in your case the normal procedure is broken.

You say you are upgrading from 14.04 to 15..04. But 15.04 has reached end of life and the prompt in image #3 says "Ubuntu 15.10." Are you sure that it is 15.04 and not 15.10? In which case 15.10 will reach end of life in July 2016. That means you will have to upgrade to 16.04 about that time.

These are your options as far as I can tell

1) At the Linux command line log in and run these commands

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

2) Back up any important data and do a fresh install of 16.04. It is supported for 5 years.

3) At the boot menu select Advanced options for Ubuntu. Then select a recovery mode kernel to load. At the recovery menu select Resume. See if that gets you to a working desktop environment. If it does, then change video drivers.

4) At the recovery menu select Network to set up an internet connection. The select Root shell prompt. Then run

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

 
Afterwards. type exit to get back to the recovery menu and then select Resume. If that does not solve this, then I have no more options. I would re-install.

Regards.

---

### Post by Impavidus on 2016-06-05
I understand you cannot recall your username. Have a look at this tutorial: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword). It tells not only how to change your password, but also how to check your username (you can skip changing the password).

The 14.04&#8594;15.10 upgrade seems to give problems often. In my opinion, it shouldn't have been offered, as it's not a normal upgrade to the next version, nor an LTS-to-LTS upgrade. But this upgrade is offered, so we deal with it. In case of an upgrade gone wrong, the thing to do is running graham's apt-get commands. If that doesn't work, the situation is often so bad that a fresh install (of 16.04, as 15.10 is nearly end of life) is the fastest way out of your problems.

---

