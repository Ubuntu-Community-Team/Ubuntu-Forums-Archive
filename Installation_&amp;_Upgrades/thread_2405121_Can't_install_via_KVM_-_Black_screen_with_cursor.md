---
title: "Can't install via KVM - Black screen with cursor"
date: 2018-11-01
forum: Installation &amp; Upgrades
---

### Post by Frank_Snyder on 2018-11-01
I have a server with Proxmox and up until now, I've been using containers for everything. I need to run a instance of an application that does not support headless systems. I initially tried using xpra within a container running Ubuntu 18.04 but ran into a bunch of issues. Long story short, I've decided to switch over to a VM as I know the application isn't demanding. With something like Lubuntu, it should take up the same resources as if I ran it in a container and still be okay.

The issue is that Lubuntu won't install. I boot into the VM with the Lubuntu 18.10 media and am greeted with the first screen, where I select "Start Lubuntu". After this I am left with a black screen and a cursor blinking. **[This ]("https://askubuntu.com/questions/554399/how-to-fix-blank-screen-with-mouse-pointer-on-ubuntu-install-reboot")**seems to be a good start, however the OS isn't even installed so none of this actually takes effect. I've also tried running a Ubuntu 18.04 VM with the same settings. I do get the black screen with the cursor for a slight bit but it eventually leads into the start/install section like I would expect.

---

