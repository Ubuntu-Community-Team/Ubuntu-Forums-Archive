---
title: "Where's /usr/src/linux?"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by folkers on 2005-03-12
Today, I decided to finally install my sound card driver (which had to be compiled from source). One of the instructions was to change directory to /usr/src/linux and do some make commands there. However, the only directory in /usr/src was rpm. Where can I find the kernel in Ubuntu?

---

### Post by -DomiNator- on 2005-03-12
The kernel you are using atm is just a standard kernel that was made during the install of ubuntu on your system. When you want to compile your kernel from source (what you're referring as "doing some make commands in /usr/src/linux) you'll have to download a kernel from kernel.org or download one using apt-get

---

### Post by Seandq on 2005-03-12
[QUOTE=-DomiNator-]The kernel you are using atm is just a standard kernel that was made during the install of ubuntu on your system. When you want to compile your kernel from source (what you're referring as "doing some make commands in /usr/src/linux) you'll have to download a kernel from kernel.org or download one using apt-get[/QUOTE]
 Not necessarily. I had to originally compile my wireless's drivers when I started Ubuntu. Open up Synaptic in the Computer > System Adminstration Menu and then search for 'linux-headers-....'. 
Download those files to have "/usr/src/linux" appear.

---

### Post by -DomiNator- on 2005-03-12
[QUOTE=Seandq]Not necessarily. I had to originally compile my wireless's drivers when I started Ubuntu. Open up Synaptic in the Computer > System Adminstration Menu and then search for 'linux-headers-....'. 
Download those files to have "/usr/src/linux" appear.[/QUOTE]
So when you just take the normal linux-headers in synaptic, without the appropriate kernel version behind it, you get the headers that match your running kernel?

---

### Post by az on 2005-03-12
No.  linux-image-2.6 will point to the most recent linux image 2.6 package.  

If you only updated your system a month ago, you may still be running linux-image-2.6.8.1-3-386 but today, the stable (Warty) linux-image-2.6 will point (depend on) to linux-image-2.6.8.1-4-368.  So you will only be correct if your system is completely up to date.  The same goes for linux-headers.

If you still do not understand, just read the long description of the linux-image and linux-headers packages (the different versions)

---

