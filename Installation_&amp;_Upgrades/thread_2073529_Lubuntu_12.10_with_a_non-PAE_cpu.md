---
title: "Lubuntu 12.10 with a non-PAE cpu"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by stafio on 2012-10-19
With the release of Quantal Quetzal, I decided to run the distribution upgrade on my Dell Latitude D600. I hadn't read up on the kernel changes and didn't realize that this meant 12.10 wasn't suitable for this laptop. The upgrade kind of worked, but gave me some errors. After some troubleshooting, I was able to get things sorted out and thought I would provide some guidance for anyone looking to do the same. This guide is assuming you're still on Lubuntu 12.04. 

**Step 1 - Update your packages**
Install all of the updates for 12.04 using Update Manager (or another method, if you prefer)

**Step 2 - Pin your kernel**
Since 12.10 only includes the pae kernel, we'll need to stick with the kernel from 12.04. To do this, you'll need to make use of apt pinning. This will allow you to specify some packages and hold them to a specific version number. In this case, kernel packages. 

Create the file /etc/apt/preferences. Hit alt-F2 and then enter
```
gksu leafpad /etc/apt/preferences
```
This file will likely not exist/be empty, unless you've done some pinning in the past. Within this file, place the following
```
Package: linux-generic linux-headers-generic linux-image-generic
Pin: version 3.2.0.32.35
Pin-Priority: 1001
```
The version noted above should be correct, assuming you've run all the updates for 12.04

**Step 3 - Start the update**
Open Synaptic and go to Settings -> Repositories. Click on the Updates tab and change "Notify me of a new Ubuntu version:" to "For any new version". 

Exit synaptic and run Update Manager. You should see "New Ubuntu release '12.10' is available" Hit the Upgrade button

You will see some errors throughout the upgrade related to the new kernel failing to install. Just ignore/dismiss these. 

**Step 4 - Clean Up**
After rebooting, I got an error that said "System program problem detected. Do you want to report the problem now?" Click Cancel, as the developers really don't need to know about you trying to install 12.10 on an old machine that they're not supporting. 

There are a couple of packages that will attempt to be updated during the upgrade process that aren't necessary. To fix this...

From a terminal:
```
sudo apt-get --purge remove linux-virtual linux-image-virtual
```

Just to clean up some other stuff:
```
sudo apt-get autoremove
```

Reboot and you should be all set on 12.10 with the latest 12.04 kernel.

---

### Post by Master One on 2012-10-20
Thanks stafio, so it is possible after all. All we need now is someone with the knowledge, time and a PPA to offer the latest 12.10 kernel without pae enabled, and we are set to go (there should not be a need to stay stuck with the 12.04 kernel).

Anyone?

---

### Post by SteveDee on 2012-10-20
> **stafio said:**
> With the release of Quantal Quetzal, I decided to run the distribution upgrade on my Dell Latitude D600....

Many thanks Stafio for taking the time & trouble to post this.

I have taken a copy & filed it, because I have not yet decided whether to update my old D600 from 11.04 (a version the D600 seems happy with) to 12.10.

---

### Post by Master One on 2012-10-23
So I proceeded as described starting with a fresh installation of lubuntu 12.04, but something seems to have gone wrong.

The final "apt-get autoremove" removed quite some packages, mostly python stuff, then after the reboot the external USB mouse was not working any more, the screen resolution was set at 1024x768 (VESA instead of ATI driver) and I got the error message "System program problem detected. Do you want to report the problem now?" again.

I am trying this on an IBM ThinkPad T42p. Any ideas?

---

### Post by stafio on 2012-10-23
I'm not sure about the issues you ran into. apt-get autoremove shouldn't remove any packages that are still necessary, but perhaps something got removed that had an impact on your mouse and resolution.

I have modified the original post a bit. I don't believe linux-virtual or linux-image-virtual are necessary for most installs, so I just changed the post to remove those and not revert them to older versions. linux-virtual is described as a "Complete Linux kernel for virtual machines" the [ubuntu packages site]("http://packages.ubuntu.com/search?keywords=linux-virtual&searchon=names&suite=precise&section=all"). Based on that, I think it's safe to remove in most cases.

---

### Post by just_jeepin on 2012-10-29
I also have a Dell Latitude D600 and followed the instructions and everything seems fine except I keep getting the system error message every time I reboot.

---

### Post by stafio on 2012-10-29
I was also getting the error message on every reboot. I didn't take note of what the prompts say, but click the button to submit the bug report when you get the warning. On the following prompt, there will be a checkbox with a label that says something about submitting the bug report. Un-check the checkbox and click to proceed and you should not see the warning again.

---

### Post by sudodus on 2013-05-11
Have a look at this wiki page, where you can test the new Lubuntu 13.04 fake-PAE, that can cooperate with most Pentíum M CPUs :-)

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

