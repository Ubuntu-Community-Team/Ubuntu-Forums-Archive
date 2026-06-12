---
title: "Dell 420 SC server install"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by BDNiner on 2008-04-10
I was asked to get Linux running on one of our Dell 420sc servers at work. After searching through Google I have found a lot of posts about the XPS 420 but not the 420sc. Has anyone been able to successfully install Ubuntu on a Dell 420sc? It comes with 8 MB of video memory so X will not start when it boots. I feel that I can get gnome or kde to tun since the computer can run windows fine. There is no where in the latest BIOS where i can increase the video memory, I believe that this is what is preventing me from starting X. Any ideas?

---

### Post by dstew on 2008-04-10
> I believe that this is what is preventing me from starting X.The video memory should not make a difference. You should be able to get at least a VGA display. More likely, it is a driver problem.

If you think that X is not running, one thing to do would be to get a command line (ctrl-alt-F1 if your display is not working) and enter```
sudo dpkg-reconfigure xserver-xorg
```That gets you a text-based xserver reconfiguration program. Answer the questions the best you can (read the explanations), and when you get to the display, choose the **vesa** driver, and for the highest resolution choose the resolution you actually use. When you are done, press ctrl-alt-backspace to restart the xserver. Once you have a display, check to see if you have a restricted driver available in the System --> Administration --> Restricted Drivers Manager window.

---

### Post by BDNiner on 2008-04-10
Yes, I already tried to reconfigure the X server. I get an error message that there is not enough video memory for X to start. I am currently trying to install opensuse to see if it works. I also tried fedora this afternoon and the same thing happened. I can go though the GUI install with no problems but when I boot for the first time X will not start. I will setup another box along side the one i am trying suse on. I would rather use ubuntu than suse for this project.

---

### Post by dstew on 2008-04-10
There must be something wrong with the display memory, because 8 MB should be enough for the vesa driver. Did you try just **vga** in the reconfiguration? Please post the output of```
sudo lshw -C display
```

---

### Post by BDNiner on 2008-04-10
Yes that is what i thought since i have a Dell laptop with 8MB of memory and after some tweeks I was able to get X to start on it. I think the problem has to do with the ATI card. All this time i thought that it was an Intel video card. So i will try and install the proper drivers once i have the server up and running again. Things got busy at work so I have not had time to work on this project. I will post again this weekend if i run into any problems.

---

### Post by BDNiner on 2008-04-15
I figured out the issue. The Dell 420sc doesn't have an ATI card like i thought. It is the Intel E7221 video card, which is a server version of the Intel i915 chipset. There is an issue with the drivers for this chipset in the 2.6.22-14 kernel. I had to upgrade to Hardy which uses the 2.6.24-16 kernel where the problem has been fixed. I didn't feel like compling my own kernel since Feisty will not install the 2.6.22-14 kernel and Hardy is LTS so that works out better. 

On another note is there a lighter version of the gnome desktop in the repositories? I installed ubuntu-desktop but there is a lot of crap that i don't need and i am currently uninstalling it right now.

---

### Post by dstew on 2008-04-15
You can use the Xubuntu desktop instead, but it doesn't have the same set-up as the Gnome desktop. Some of the GUI features overlap with Ubuntu, but some don't. I am not aware of a lighter Gnome, but there might be one out there.

---

### Post by BDNiner on 2008-04-15
Well i ended up just removing all the packages that i didn't need through synaptic. I was just wondering if there was a version of a base install of gnome with just a window manager and basic applications like the terminal, gedit and firefox in the repositories because i don't feel like compling my own gnome desktop. The xubuntu-desktop package also has a lot of crap installed by default. I may have to complie my own desktop if it is not to my boss' liking. But at least it is up and running and now we don't have to replace any servers at our remote locations.

Now I need to find out if we can do an in place install of the linux server. We currently use Novell Netware servers and Netware runs on linux now.

---

