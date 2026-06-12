---
title: "Kernel updates and nvidia driver woes"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by nowhere@cox.net on 2008-12-02
Hey all,

I have my system running but I don't like the way kernel updates are handled. I had a quirky nvidia card that the default install driver just doesn't like (every distro from Feisty on has had this problem). So I installed the server version of 8.10 which is nice too since I get all the servers installed by defaults. Then I did and apt-get install ubuntu-desktop and watch the paint dry ;) Lastly apt-get install build-essential.

I change the xorg.conf file to user driver "vesa" then install the restricted drivers via the Hardware Drivers (formally know as restricted package manager).

Now, the problem is that the build-essential installed the generic kernel source and the nvidia driver install requires that the source for -server be installed specifically (which I did to get the driver install to work).

Now, any kernel update and reboot requires me to load in low graphics mode (very slow), install the new kernel's -server source package, then re-enable the restricted drivers. 

There has to be a better way. What is it?

Thanks a ton for any help!

---

