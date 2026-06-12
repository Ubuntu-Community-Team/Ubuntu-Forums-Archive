---
title: "PANIC: CPU too old"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by gomisute on 2008-02-02
I installed the latest server version of UBUNTU on a laptop.  Using it as a development LAMP server locally.  But, it seems that the CPU is too old for the kernel.
How can I fix this?

Thank you.:confused:

---

### Post by Whiffle on 2008-02-02
You'll need to install a generic or 386 kernel, i'm pretty sure the server kernel is compiled for 686 machines.  I did this once, but I can't remember how I did it.  If I do, I'll post.

---

### Post by Rocket2DMn on 2008-02-02
What make/model cpu are you using?  Also, do you know the kernel version?

---

### Post by Pumalite on 2008-02-02
Post:
lshw
uname -a

---

### Post by gomisute on 2008-02-03
It's and old Fujitsu Loox Notebook.
Up till recently it was on debian but decided to refresh it with a format and a clea install after 4 years.

The cpu  is a transmeta crusoe ...all I know.
---------
The install went fine, though.
---

Thanks and more help please.

PS.
I'm not that savvy with installs, kernels and upgrades...but can use the command line no problem, your detailed commands will / shall guide me well.
:popcorn:

---

### Post by WillyP on 2008-02-03
[http://cedartech.blogspot.com/2007/12/panic-cpu-too-old-for-this-kernel.html]("http://cedartech.blogspot.com/2007/12/panic-cpu-too-old-for-this-kernel.html")

After several tries, and some googling, this worked for me.

---

### Post by oscar615 on 2008-03-08
Ok everything I see on the forums talks about 686 vs. 586.  I am having the same problem. I don't want to use an old kernel.  It should work.

Here are my specs
AMD 64 2800+, 1.8ghz.
1.25 Gig ram
120 Gig HD
Geforce fx5200 256 meg
MSI K8t Neo
Samsung dvd writer

Also I am trying to run Ubuntu server 7.10 in virtual box from within Vista.

So anyway I don't think my problem is that the computer architecture is to old.  It should run.  Any thoughts on what the problem is here?

I am going to try the same setup with Ubunto desktop and see what happens.  Will I have the same problem?

Robert

---

### Post by soydeedo on 2008-03-10
> **oscar615 said:**
> Ok everything I see on the forums talks about 686 vs. 586.  I am having the same problem. I don't want to use an old kernel.  It should work.

Here are my specs
AMD 64 2800+, 1.8ghz.

It's a problem with virtual box, not your cpu.

[http://virtualbox.org/ticket/212](http://virtualbox.org/ticket/212)

---

