---
title: "VirtualBox can't operate in VMX root mode"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Arabiest on 2008-11-08
Dears,

I am struggling with Virtualbox to work after clean installation. The below error message pops up and have done what I possibly can do, but without success.

Please help

---error message---

VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot.
VBox status code: -4011 (VERR_VMX_IN_VMX_ROOT_MODE).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

---------------------

P.S.
My laptop (Fujitsu T4210) is dual core and of Intel chipset that support KVM.

Awaiting your prompt response.

Thanks in advance.

-----------------------------

[SOLVED]
I managed to get it from this link:

[http://ubuntuforums.org/showthread.php?t=766463&highlight=VBox+status+code%3A+-4011]("http://ubuntuforums.org/showthread.php?t=766463&highlight=VBox+status+code%3A+-4011")


the command used is:

sudo /etc/init.d/kvm stop

---

### Post by motin on 2008-11-20
Thanks man. Here is the bug report with the workaround: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/292588](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/292588)

---

