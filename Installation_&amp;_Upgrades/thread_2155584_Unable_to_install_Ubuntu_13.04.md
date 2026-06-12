---
title: "Unable to install Ubuntu 13.04"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by DiamondBoy1979 on 2013-06-18
Im trying to install Ubuntu 13.04 but i keep getting this error message.Cannot install into C:\ubuntu
There is another file or directory with this name.Please remove it before continuing.
For more information, please see log file:
c:\users\fred\appdata\local\temp\wubi-13.04-rev279.log

so my question is how do i fix all this?Im new to ubuntu.

---

### Post by cincinnatus13 on 2013-06-18
This...just doesn't seem right at all.

Since you have 13.04 it can't be Wubi right? It seems like you are trying to install Wubi but 13.04 IIRC doesn't have a Wubi exe anymore.

---

### Post by claracc on 2013-06-19
Yes, ubuntu 13.04 has not wubi support: [http://ubuntu-with-wubi.blogspot.com.es/](http://ubuntu-with-wubi.blogspot.com.es/)

However, as the previous link point:

> **Update April 25 - Release date**
With the release of Ubuntu 13.04, no change was made to the decision to discontinue support, despite a patch being provided by me for all three bugs. However, a signed, patched (all except the UEFI issue) version of wubi.exe is currently available at [http://releases.ubuntu.com/13.04](http://releases.ubuntu.com/13.04) so it's unclear what's up. 

So you can try the wubi.exe patch but there is not garantee of success.

I instead, recommend dual boot installation windows/ubuntu

---

### Post by fantab on 2013-06-19
WUBI (**W**indows **UB**untu **I**nstaller) has been dropped in 13.04. WUBI installs Ubuntu 'inside Windows'. It was meant for Windows users to TRY Ubuntu.
To do a real Dual-Boot you MUST install Ubuntu to its own partition.

---

### Post by grahammechanical on 2013-06-19
What is the error message telling us? I guess that it is saying that there is already a Wubi install of Ubuntu in C:\ubuntu. The answer is to remove the folder C:\ubuntu or direct the new installation into another folder such as C:\ubuntu1304 (if that is possible). Whether it is possible to use wubi.exe with 13.04 is another argument. I can tell you this, I have an ISO image of Saucy Salamander (13.10) and that has a wubi.exe file in it.

I think the issue is with wubi.exe being usable with Windows 8 and the hardware it is installed on. There is even less assurance than usual of getting a positive result.

[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

> [SIZE=2]Windows installer is not compatible with Windows 8 or UEFI firmware, and is not available for Ubuntu 13.04.[/SIZE]



The last part is not accurate but is the Windows installer (wubi.exe) effective? That is the question.

@diamondboy1979

Have you made more than one attempt to install Ubuntu using wubi.exe? Did you get this error messages after trying to install ubuntu using wubi.exe a second time? You need to delete the C:\ubuntu folder. But as already noted the failure to get a working ubuntu install with wubi.exe may be due to incompatibilities with Windows 8 and the hardware it is installed on.

Regards

---

