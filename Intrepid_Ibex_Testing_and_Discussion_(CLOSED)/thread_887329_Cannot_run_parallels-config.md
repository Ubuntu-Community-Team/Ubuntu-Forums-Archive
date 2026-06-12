---
title: "Cannot run parallels-config"
date: 2008-08-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Robertjm on 2008-08-12
Not exactly sure if this is the right forum, or not. However, since it deals within installing a program in Intrepid that's why I am posting to the development forum.

I am trying to reinstall Parallels Workstation v2.2. It installs fine, but after doing a new install you have to run parallels-config to config/link drivers. When I attempt to do that it bombs out with the msg:
[COLOR="Purple"]
[B]
     Compiling Parallels Workstation 2.2 drivers...

Can not compile and/or link drivers. Read /usr/lib/parallels/doc/INSTALL
	and follow instructions specified in this document.

	Compilation log is available at /usr/lib/parallels/comp.log.7127.error
root@robertjm-desktop:/home/robertjm# [/B]
[/COLOR]

I've attached the error log it refers to in case that helps.

Using Parallels Parallels-2.2.2234-lin-en-parallels.deb to install, which is the latest version built for debian systems. Not sure if it means anything, but when I try and view the INSTALL file its not there. In fact, the entire docs folder doesn't exist on my system. I have attempted to install a couple of times, with the same result.

Thanks,

Robert

---

### Post by ounas on 2008-10-13
Did you find a solution to this problem??

:(

---

### Post by Robertjm on 2008-10-13
Unfortunately, not as of yet. However, I haven't checked the Parallels forums either to see if they have posted anything.

I'll do that later tonight and if there's anything new I'll let you know.

Robert

> **ounas said:**
> Did you find a solution to this problem??

:(

---

### Post by Robertjm on 2008-10-14
Unfortunately, it's still busted. Of course perhaps the fix they had in their forums fixed for an earlier kernel, but as we all know Intrepid has had several new kernels included in the alpha/beta stage.

The price of dabbling with development software, I guess.

Robert

---

### Post by tonyric on 2008-10-14
And for using software form a company that pays lip service to the Linux community. Go with KVM, VMware or VirtualBox, and ditch parallels.

---

### Post by ounas on 2008-10-17
Well have to wait then

:confused:

---

