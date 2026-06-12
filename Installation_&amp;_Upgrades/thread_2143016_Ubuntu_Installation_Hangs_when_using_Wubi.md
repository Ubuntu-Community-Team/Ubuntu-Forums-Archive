---
title: "Ubuntu Installation Hangs when using Wubi"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by paimeauu on 2013-05-07
I installed Ubuntu 12.04.1LTS using Wubi Installer. It **worked absolutely fine** and I used it for a while and installed some updates too.

For some reason I had to uninstall Ubuntu. I **uninstalled** Ubuntu 12.04.1 from Control Panel>Programs and Features>Ubuntu. It **successfully uninstalled** Ubuntu.

I then installed Ubuntu 12.10 using Wubi Installer available in the iso image. The system restarted and started installing Ubuntu 12.10. When the installation reached about **70%** it **hung** [stuck]. The message on the installer is "**Almost finishing copying files**". I waited for nearly an hour, but in vain.
I powered off the pc[by keeping the power button pressed] and booted windows [No issues with windows]. Again I uninstalled Ubuntu, and ran Wubi to install 12.04.1, but again it hangs at the same point.
I repeated the installation a couple of times, but it always fails at the same point.

**Question is whats going wrong? It worked fine the first time, after uninstalling ubuntu, its not reinstalling.**
Please help. Thank You.

---

### Post by bcbc on 2013-05-07
See [http://askubuntu.com/q/292177/14916](http://askubuntu.com/q/292177/14916)

Update either one if you want it to be answered.

---

### Post by paimeauu on 2013-05-08
Hi bcbc,
Thanks for the link. I did check the logs.

For my luck, after reverting from command line to GUI, it continued installation and installed successfully. Now I have ubuntu 12.10 **installed**.

I really dont know what caused it to hang the previous times. I just cant find a reason.

Anybody who faces similar issue, please do share it here and keep the thread alive.

As for now, the question still remains a mystery, leaving it unanswered........

---

### Post by bcbc on 2013-05-08
Paimeauu,

Did you capture the logs? If so, please attach them either here or to a bug report: [https://bugs.launchpad.net/wubi/+filebug](https://bugs.launchpad.net/wubi/+filebug)

That will help figure out the issue. Also, post your machine brand/model/graphics card etc.

Thanks!

---

