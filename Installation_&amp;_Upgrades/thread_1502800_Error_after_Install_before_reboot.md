---
title: "Error after Install before reboot"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by ttd82 on 2010-06-06
Hi all,

Just done my first ubuntu 10.04 install on a hp pavilion a320a, the install seems to have went well, though while it is shutting down and before rebooting the following error appears across the screem:

[16866.760778 end_request: I/O error dev sr0 sector 504392]

Before this error appears at the bottom of the screen the error scrolls on the screen with a different number at the beginning of the error where 16866 etc (different number each line) remainder of the error remains the same maybe different sector number but not sure, there is way too many to write down in the time they are on the screen.

What is the problem, is it important can anyone help please?

Thanks
Tom

---

### Post by MedianMajik on 2010-06-06
You should run a md5sum of the Ubuntu image you're using as it might be bad.

---

### Post by wilee-nilee on 2010-06-06
Also confirm the type of install you did, and want, a wubi=installing from a live MS environment dualboot=booting a cd then installing.

---

### Post by ttd82 on 2010-06-06
> **MedianMajik said:**
> You should run a md5sum of the Ubuntu image you're using as it might be bad.

Ok here is the output for my md5 of the iso sitting on my MacBook.
I downloaded the iso image from the ubuntu website.

md5 ubuntu-10.04-desktop-i386.iso
MD5 (ubuntu-10.04-desktop-i386.iso) = d044a2a0c8103fc3e5b7e18b0f7de1c8

---

### Post by dtfinch on 2010-06-06
I think I've gotten this on my last few installs. I haven't noticed any actual problems following it though.

---

### Post by ttd82 on 2010-06-06
> **wilee-nilee said:**
> Also confirm the type of install you did, and want, a wubi=installing from a live MS environment dualboot=booting a cd then installing.

I downloaded the iso from ubuntu on my macbook, burnt it to disc per the instructions and booted it on the computer and chose install at the question where it asks to install or try it.

---

### Post by wilee-nilee on 2010-06-06
So everything is working but you see this error? If this is the case there is error I see on my opening screen and closing as well I don't worry about it as the computers runs fine.

---

### Post by ttd82 on 2010-06-06
> **wilee-nilee said:**
> So everything is working but you see this error? If this is the case there is error I see on my opening screen and closing as well I don't worry about it as the computers runs fine.

Correct.
It appears to be running ok, I just wondered if it was important or not.
I now have to get it connected to the internet!

---

