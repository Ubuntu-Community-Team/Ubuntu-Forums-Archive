---
title: "Google Earth on Linux"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by Dome1223 on 2011-07-15
I am following this guid how-to install google earth on linux [http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)


in terminal i write cd '/home/mara/Radna površina/GoogleEarthLinux.bin'
and it says Coud not display "/home/mara/radna površina/GoogleEarthLinux.bin".
The file is of an uknown type 


how do i start it?!?

---

### Post by Dome1223 on 2011-07-15
PS: i am on ubuntu 9.10

---

### Post by sikander3786 on 2011-07-15
Why not try an easier approach?

[http://ubuntu4beginners.blogspot.com/2011/06/easy-installation-of-popular-apps-that.html](http://ubuntu4beginners.blogspot.com/2011/06/easy-installation-of-popular-apps-that.html)

---

### Post by sikander3786 on 2011-07-15
> **Dome1223 said:**
> PS: i am on ubuntu 9.10
You realize that 9.10 isn't supported any longer and you won't be receiving any security updates/patches etc thus resulting in a compromise on your security?

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by sikander3786 on 2011-07-15
[QUOTE=Dome1223]I am running on 9.10 and when i am going to install a new version with wubi i don t get a newer version why?!?[/QUOTE]

With Wubi, you might need to do more than some simple things to upgrade it.

First, lock your Grub packages by following the 'Permanent Fix' near the bottom of the guide here.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Then, change your sources.list to be able to talk to the repositories (which have been shutdown/moved whatever you call).

[http://ubuntu4beginners.blogspot.com/2011/01/access-repositories-on-eol-end-of-life.html](http://ubuntu4beginners.blogspot.com/2011/01/access-repositories-on-eol-end-of-life.html)

Now, go to Applications > Accessories > Terminal and run:

```
sudo apt-get update && sudo apt-get upgrade
```

```
update-manager -d
```

Update Manager should pop up with the offer to upgrade to 10.04, hopefully.

Remember: Version upgrades are known to break the OS at times and with Wubi, the chances are even higher. You might end with a non-bootable PC which isn't either capable of booting Windows without some additional efforts. You'd be following at your own risk ;)

It is recommended to gain access to a working Ubuntu Live CD or USB in order to repair the damage, if their is any.

---

