---
title: "Customization Madness!"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by Xgates on 2005-04-11
Well I must admit that Ubunt is a nice easy distro to use as long as you don't want to strip it down to the bare essentials, in packages, and stripping down the kernel and recompiling it just to meet youur hardware requirements, and not every other piece of hardware out there under the sun.

6 years in Linux 5 of which where in Slackware, and let me say Ubuntu is not suited for a power user. Why is it distros like these can't be easy to use, but also allow the ease of customization to those that want to run a lean trimmed down system.

Ubuntu should work towards this goal, ease of use and customization. Try stripping down the kernel just to meet your hardware requirements, as say you could do in Slackware, the same in Ubuntu and you will soon see what I mean, this takes quite a bit of effort. Well 6 years, and 8hours later working on the kernel 2.6.10 stripped to the bone for my system, and just 2 errors to go, one keyboard and one network, which the network one should not be brought on by the kernel, but some how was.

Has anyone successfuly compiled a stripped down kernel, vanilla kernel in Ubuntu, if so, could you PLEASE share with us, what things must stay in Ubuntu if any, or the biggest concern is just having "cramfs" compiled in, which by the way took some time to figure out about cramfs, which was the first hurdle to over come.

We need the Ubunt team to put up a "Kernel" section on the website showing what options must be left in the kernel, if any like "cramfs" for example, and that you also need to use a kernel source from apt-get thats patched as well.

Ok my problems, "dpkg-reconfigure xserver-xorg" says I have a 104 keyboard, but in configuring xorgconfig I used 101, and this works with the default kernel, but when I compile a  new kernel 101 keys does not seem to work, and this should not happen, so is this a kernel issue, or I guess I might need to reconfigure xorgconfig? The reason I'm asking is I've always used 101 in Linux for the past 6 years in Linux without a problem and the default Ubuntu kernel works fine as 101 also, but when I recompile a new kernel it doesn't, which makes no sense since it worked fine before.

By the way dpkg-reconfigure xserver-xorg does not work for me on my box, and I can't change the monitor resolutions in Gnome, it only gives 640x480 and I have all the correct settings in it, but when I run "xorgconfig" everything works fine, and I change them in Gnome this way, I have seen many others are having problems with this too, and needed to setup X with xorgconfig instead.

I have this error at boot up as well:

*ror* Temporary name resolution failure

Now how can a kernel bring about this, when I had all the default network options in the kernel, and in the default Ubuntu kernel I don't have this problem. The deafult kernel works, but a new compiled one does not. Name resolution from what I gather is not a kernel issue, but rather DHCP, DNS, etc... So then how is this happening when the netowrk options are compiled in correct?

For 2 days running Ubuntu I had not network issues and as soon as I recompile the kernel I get this, with all the correct Network options compiled.

---

### Post by jobezone on 2005-04-11
About dpkg-reconfigure xserver-xorg:
This command, will not make any changes  to /etc/X11/xorg.conf if you have manually or otherwise changed it with other programs (with xorgconfig, for example, which is x.org native configuration program). In the xorg.conf file itself are instructions (right on top of the file) on how to reset the file to be able to be configured with debconf.
debconf is what I call Debian Configuration System.

---

### Post by Xgates on 2005-04-11
[QUOTE=jobezone]About dpkg-reconfigure xserver-xorg:
This command, will not make any changes  to /etc/X11/xorg.conf if you have manually or otherwise changed it with other programs (with xorgconfig, for example, which is x.org native configuration program). In the xorg.conf file itself are instructions (right on top of the file) on how to reset the file to be able to be configured with debconf.
debconf is what I call Debian Configuration System.[/QUOTE]

Thanks, but I know about all this, but it still doesn't solve the problems.

---

