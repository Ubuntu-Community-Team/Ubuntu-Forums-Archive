---
title: "GeForce 7900 GS Drivers"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by linuxsyst on 2013-02-10
First I had this problem, I couldn't get the login screen it brought me to tty so I installed other drivers and did ```
apt-get -f install
``` And now I can get to Ubuntu but its very slow and games lag alot right at the menu. The driver is NVIDIA accelerated graphicexperimental 304. Now I want to install a older driver that will work good. Can anyone help? :( :confused:

When I try to install nvidia-current-updates it says this

```
admin@blackhat:~$ sudo apt-get install nvidia-current-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current-updates : Depends: xorg-video-abi-11
                          Recommends: nvidia-settings-updates
E: Unable to correct problems, you have held broken packages.
```

Thanks

---

