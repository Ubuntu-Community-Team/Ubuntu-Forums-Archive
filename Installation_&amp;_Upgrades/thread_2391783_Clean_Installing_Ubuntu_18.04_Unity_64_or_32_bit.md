---
title: "Clean Installing Ubuntu 18.04 Unity 64 or 32 bit"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by rsrocha on 2018-05-13
Hello all!

Today i am going to show you how to install Ubuntu 18.04 "the clean way" with Unity. Many people dislike the fact that the standard live iso installs GNOME shell by default and after all these years they became used to Unity. Also you can install this on 64 or 32 bit systems. You will need an active internet connection because this installation method will download the most up to date needed packages from the ubuntu repos.

- Download the minimal iso (64 or 32 bit) from this page [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

- Create a usb bootable drive with the minimal iso or burn it to a cd.

- Start installation. This will take you to the alternate text mode installation. This is much the same as the tutorial on this link [https://www.howtoforge.com/tutorial/ubuntu-lts-minimal-server/](https://www.howtoforge.com/tutorial/ubuntu-lts-minimal-server/)

- When you get to the package selection screen do not select any of those options for Unity, or you may want to try the included options.

- After the installation is done, reboot your system. You will be presented with a terminal screen.

- Login with your user/password

- Type this command: sudo apt-get install ubuntu-unity-desktop

- Type your admin password, select Yes and let it install. After installing all the packages, reboot your system and you will be presented with the standard Ubuntu login screen and Unity installed.

- DONE!

---

### Post by mörgæs on 2018-05-14
Thanks for posting.
If you mark the thread solved there is a better chance that people will find it.

---

