---
title: "Simple-ccsm installation problems"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by pottsiex5 on 2011-07-31
Hi, 
I am using the the command "sudo apt-get install simple-ccsm" to install simple ccsm, but when i run it, it says there is something wrong with the packages:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 compiz-core : Breaks: simple-ccsm (< 0.9) but 0.8.2-0ubuntu1 is to be installed
E: Broken packages
```

Any advice?

---

### Post by pottsiex5 on 2011-07-31
If it helps, at the moment i have Compiz Fusion at the moment, but when i open up the Settings Manager and stuff and choose something like Wobbly Windows or Rotate Cubes, and then i close the Setting manager, but the effects dont work...
Thanks :)

---

### Post by coffeecat on 2011-07-31
My guess is that you are running Natty/11.04, but you do not say so. Please, when posting requests for help, **always** state which version of Ubuntu you are running. It is important.

If you are running 11.04, you cannot install simple-ccsm. It is incompatible with the version of compiz-core used in Natty. The package simple-ccsm is not maintained by Ubuntu and I guess that it has been neglected by its upstream developer(s). Why is it still in the Natty repository when you can't use it in Natty? I think a simple oversight and this bug has requested its removal from the archive:

[https://bugs.launchpad.net/ubuntu/+source/simple-ccsm/+bug/795212](https://bugs.launchpad.net/ubuntu/+source/simple-ccsm/+bug/795212)

Use compizconfig-settings-manager instead.

---

### Post by pottsiex5 on 2011-07-31
Hey, 
I am actually using LinuxMint, I just switched from using Ubuntu (i figured since it was ubuntu based, i could still get help here :) ), sorry. I allready have the compizconfig-settings-manager. However i still cant get any of the settings to work... none of the effects work after i set them.
Do you have any advice?

---

