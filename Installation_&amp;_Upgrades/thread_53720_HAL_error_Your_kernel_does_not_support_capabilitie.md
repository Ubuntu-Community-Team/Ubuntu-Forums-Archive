---
title: "HAL error: Your kernel does not support capabilities."
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by sk545 on 2005-08-01
I have installed a cutom kernel, however i get this during bootup:

* Starting system message bus:
Mon Aug  1 21:44:19 2005: ^[[A^[[122G[ ok ]
Mon Aug  1 21:44:19 2005:  * Starting Hardware abstraction layer:
Mon Aug  1 21:44:19 2005: 21:44:19.695 [W] hald.c:302: Your kernel does not support capabilities; some features will
not be available.


What do i have to enable in the kernel to get rid of the error?  Thanks.

---

### Post by The Cockroach King on 2005-08-28
ya, me too?

---

### Post by sk545 on 2005-08-29
Yeah, i did figure out how to get it to work.

Just do this:

$ sudo gedit /etc/modules

And write these in that file (in addition to whatever is there already):

commoncap
capability

Save /etc/modules, and reboot.  At least thats what i remember doing, let me know if it works out.

---

### Post by The Cockroach King on 2005-08-30
nope, that didn't do it, but thank you for trying...

I will eventually persevere!!

---

### Post by The Cockroach King on 2005-08-30
WHOO HOO!!!

I manually patched my source code with the evms-bd-claim patch from the Ubuntu source and, Whallahh...

It's fixed :grin: 

Though it may have only worked because I still have that in my modules file??

I'll have to test that on my next reboot and let you know...

Thanks again..

---

### Post by The Cockroach King on 2005-08-30
Bummer....

It worked after the first reboot, then it blew up again...
It has worked right only once sonce then, and that time it somehow didn't load my wireless (ipw2100) module..

Maybr there is a connection?

---

### Post by The Cockroach King on 2005-08-30
It's definatly the ipw2100 module, anytime it's loaded when I log in HAL blows up, but if it's not then HAL works fine...?

Time to do some more searching.... ](*,)

---

### Post by The Cockroach King on 2005-08-30
My Solution....

Stop using the 2.6.13-rc6-ck1 kernel source!

2.6.12-ck6 works fine, no problems with anything yet... Thanks for you're post, it at least got me looking in the right direction to find my answer..

---

### Post by sk545 on 2005-08-31
sorry if i wasn't clear, but you need to have commoncap and capability modules enabled in your kernel configuration, or they wont load even if you put them in /etc/modules.  Try doing 'sudo modprobe commoncap' and then the same for capability.  See if you get any errors.

This is what my kernel config looks like for the security section:

#
# Security options
#
# CONFIG_KEYS is not set
CONFIG_SECURITY=y
# CONFIG_SECURITY_NETWORK is not set
CONFIG_SECURITY_CAPABILITIES=m
# CONFIG_SECURITY_ROOTPLUG is not set
# CONFIG_SECURITY_SECLVL is not set
# CONFIG_SECURITY_SELINUX is not set

I am using kernel 2.6.13 right now.

---

### Post by The Cockroach King on 2005-09-01
Yeah, I got that part, but for me, with the ipw2100 module loaded and any version of the 2.6.13 kernel HAL crashes at login.

I've done alot of compiles, trying different things and it always happens, but it does work fine with 2.6.12 so I'll just stick with it for now, maybe someone will eventually put out a patch for my problem, or it may get fixed with the next version of ipw2100, or maybe I'm just missing some library that I don't know about, but anyway I'm pretty happy with just getting everything to work with any kernel so I'll probably just let it go for now :)

Thanks again...

---

