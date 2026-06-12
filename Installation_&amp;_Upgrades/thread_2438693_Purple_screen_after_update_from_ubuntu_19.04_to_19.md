---
title: "Purple screen after update from ubuntu 19.04 to 19.10"
date: 2020-03-16
forum: Installation &amp; Upgrades
---

### Post by abalone542 on 2020-03-16
Hello,

I had ubuntu 19.04 installed alongside windows on my computer. I decided to launch the update to 19.10. When i came back after sometime there was only a message along the lines of "oops something went wrong, try to login again". Now every time I try to launch I only have a purple screen. Following a comment I saw I tried to change the "quiet splash" setting to "nosplash"  in grub. Now I get the following screen at launch (first image) : [https://imgur.com/a/hDWQY3D](https://imgur.com/a/hDWQY3D) . Is there something I can do to get back to a working version of ubuntu while keeping the documents I have on my computer ?


edit : as additionnal information. When I try to enter recovery mode, whatever the version available to me, I get back to the first "something went wrong, try again and logout" screen. When I press logout, unlike the previous time an empty application bar appears on the left as well as the top bar with the shutdown option but i can't click on them.

---

### Post by Impavidus on 2020-03-17
After a failed release upgrade it's rarely worth your time to fix it. Better try a fresh install. Release upgrades tend to work better if you attempt them while the old release is still supported. Assuming your filesystem is OK, you can access your files using a live disk to create backups (but one should keep backups at all times, in particular before attempting a release upgrade or fresh install).

If you really wish to try and fix this, tell a bit more about your hardware and use [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") to create a boot info summary. Don't try the recommended repair, just the summary and show us the link.

---

### Post by abalone542 on 2020-03-17
Thank you for taking the time to respond to my post.

My config is :

CPU : intel i7-9700K 3.6GHz
GPU : Nvidia GeForce RTX 2070 SUPER
Mother board : TUF Z390-PLUS GAMING
32Go of RAM
For Storage, everything is on one Samsung ssd 970

If you need any other hardware information, please tell me. 

Here is the link for the summary of the boot repair : [http://paste.ubuntu.com/p/wZZYhRWBdX/](http://paste.ubuntu.com/p/wZZYhRWBdX/)

---

