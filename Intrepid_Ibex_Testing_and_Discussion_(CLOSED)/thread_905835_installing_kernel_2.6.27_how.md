---
title: "installing kernel 2.6.27 how"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by monkeyking on 2008-08-30
Hi,
I have problems with the latest kernel,
and I on launchpad, that I could try the latest dev kernel,
to see if it was fixed.

Can anyone tell me how to do this.

thanks in advance,
I'm on 8.04

---

### Post by Slug71 on 2008-08-30
Go to page 2 of 'Ibex Testing and Discussion' and go to the thread 'Will kernel 2.6.27 hit Intrepid' and go to page 6 of that thread. Theres a link there to 'Ubuntu server Next' or something like that and you can install from there.

---

### Post by monkeyking on 2008-08-30
thanks,
this would be the link
[http://kernel.ubuntu.com/pub/next/2.6.27-rc3/intrepid/](http://kernel.ubuntu.com/pub/next/2.6.27-rc3/intrepid/)
and here is
[HTML][/HTML]

```

linux-headers-2.6.27-1-generic_2.6.27-1.1_amd64.deb	13-Aug-2008 23:10 	616K
linux-headers-2.6.27-1-generic_2.6.27-1.1_i386.deb	13-Aug-2008 23:16 	607K
linux-headers-2.6.27-1-server_2.6.27-1.1_amd64.deb	13-Aug-2008 23:10 	618K
linux-headers-2.6.27-1-server_2.6.27-1.1_i386.deb	13-Aug-2008 23:16 	607K
linux-image-2.6.27-1-generic_2.6.27-1.1_amd64.deb	13-Aug-2008 23:12 	22M
linux-image-2.6.27-1-generic_2.6.27-1.1_i386.deb	13-Aug-2008 23:18 	22M
linux-image-2.6.27-1-server_2.6.27-1.1_amd64.deb	13-Aug-2008 23:14 	22M
linux-image-2.6.27-1-server_2.6.27-1.1_i386.deb	13-Aug-2008 23:20 	23M
linux-image-2.6.27-1-virtual_2.6.27-1.1_amd64.deb	13-Aug-2008 23:15 	9.9M
linux-image-2.6.27-1-virtual_2.6.27-1.1_i386.deb	13-Aug-2008 23:21 	9.5M
```

I'm a little lost on which version I should try out.
And in case something goes wrong, would the backrolling be as simple as trying to install it?

---

### Post by Nullack on 2008-08-30
Assumg your on a real desktop grab all the generic packages for your platform - i.e. 32bit or 64bit

---

### Post by monkeyking on 2008-08-30
ahh ok,
I was under the assumption that I only needed to install the kernel package.
I guess I'll wait until, the alpha iso get's released then.

but thanks

---

### Post by Slug71 on 2008-08-30
Its really easy monkeyking, you click on the one you need and the box will pop up for open with or save, use the open and the default program it wants to use and click ok. 

If youre using 32bit youll need in this order

linux-headers-2.6.27-1-generic_2.6.27-1.1_i386.deb
linux-image-2.6.27-1-generic_2.6.27-1.1_i386.deb
linux-headers-2.6.27-1_2.6.27-1.1_all.deb (from parent directory)
linux-libc-dev_2.6.27-1.1_i386.deb	  (from parent directory)

Wont take you longer than 5mins to do all four.

restart, hit update manager and 2.6.27-2 will come in.

---

### Post by monkeyking on 2008-09-01
Hi I'm having troubles with the dependencies.
I looks like the package is dependent on it self...

[IMG]http://img170.imageshack.us/img170/2729/screenshotpackageinstalcd6.png[/IMG]

thanks in advance

---

### Post by alfonskunk on 2008-09-03
Hi

The correct order is:

linux-headers-2.6.27-1_2.6.27-1.1_all.deb (from ../all directory)
linux-headers-2.6.27-1-generic_2.6.27-1.1_i386.deb
linux-image-2.6.27-1-generic_2.6.27-1.1_i386.deb
linux-libc-dev_2.6.27-1.1_i386.deb (from ../all directory)

---

### Post by gelie on 2008-09-03
Thank you very much for the instructions. I want to see if it will allow me to see the full 4 gig of memory on my Dell Optiplex 745 (running Ubuntu 8.04, 32-bit). Will post back the results.

---

### Post by gustonator on 2008-10-12
i can't install it, because the system says, that libc6 is not installed.
But i have libc6 installed. (ver. 2.7-10ubuntu4)

any suggestions?


edit: OK. the problem is solved. I used the folder Hardy, and not the Intrepid folder, but now i have another problem. The new kernel won't even start up. It just start my Caps Lock and Scroll lock LED to flash, and that's all.

---

