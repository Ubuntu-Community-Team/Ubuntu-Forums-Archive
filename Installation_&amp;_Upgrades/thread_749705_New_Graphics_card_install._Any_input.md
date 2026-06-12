---
title: "New Graphics card install. Any input ?"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by ryank82 on 2008-04-08
So I just ordered a Nvidia 8500GT PCIE graphics card and was wondering if I will run in to any issues. I already have my Ubuntu 8.04 install working nicely with my integrated graphics "Intel". When I turn off the machine and install the new card should the desktop load or is it going to boot me to a setup or even worse command prompt ? Just figured I would ask in advance. Thanks


Ryan

---

### Post by warp99 on 2008-04-08
There should not be a problem, but you need to install the restricted drivers modules and reconfigure your xserver just before you install your card. So you would set the card up before you installed the card so you can boot into a nice GUI desktop, otherwise you're going to boot into a command prompt. You can do it like this:

Install the Nvidia restricted drivers:

```
sudo apt-get install nvidia-glx-new nvidia-settings linux-restricted-modules
```

then issue the following:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Choose 'nvidia' as the video driver, exit and then run:

```
sudo halt
```

install your video card and everything should boot directly to your desktop with the new video drivers ready to go. If you have any customer monitor settings you will have to re-enter them through the video settings dialog.

Edit:

Remember to turn off your on-board video card in your BIOS so you don't have any conflicts.

---

### Post by ryank82 on 2008-04-09
Thanks for the help. Here is hoping everything goes smooth :)

---

