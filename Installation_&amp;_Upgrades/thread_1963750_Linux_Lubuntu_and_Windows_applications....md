---
title: "Linux Lubuntu and Windows applications..."
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by blackfoot on 2012-04-22
I have Lubuntu on my netbook - just that OS. 
Is there a way to install Windows software on that Linux computer? If so, how?

---

### Post by whatthefunk on 2012-04-22
You could run the programs in Wine.
[http://www.winehq.org/](http://www.winehq.org/)

Wine is in the repos so you can install it through your package manager.

---

### Post by tmaranets on 2012-04-22
Use Wine to run the software. Or use Bloodshed to install software the isn't available in the Ubuntu depository.

---

### Post by blackfoot on 2012-04-22
Something is wrong...hum. :confused:

---

### Post by whatthefunk on 2012-04-22
> **blackfoot said:**
> Something is wrong...hum. :confused:

Whats wrong?

---

### Post by blackfoot on 2012-04-23
> **whatthefunk said:**
> Whats wrong?

I'm clueless.

I do have another idea though. Can I install Windows XP on this same Linux-only netbook? Netbook [specifications]("http://usa.asus.com/Eee/Eee_PC/Eee_PC_1018P/#specifications").

That'll be better I think, I hope. 

Do I have enough capacity to install both operating systems in this system with enough memory left over to work without any slow downs?

---

### Post by whatthefunk on 2012-04-23
What applications are you trying to run??  Did you install Wine?

Yes, dual booting Windows XP is another option.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Mark Phelps on 2012-04-24
> **blackfoot said:**
> ... Do I have enough capacity to install both operating systems in this system with enough memory left over to work without any slow downs?

I think you're confusing memory with hard disk space.  Since each OS runs by itself, each one uses ALL the memory when its running.

Disk space is different in that each OS is installed into its own separate partition, so they don't reuse each other's disk space.

And yes, dual-boot is a MUCH better solution than Wine -- since Wine will only run some Windows apps.

---

### Post by Rex Bouwense on 2012-04-24
While WINE will only run some Windows applications, it does run some and some quite well.  I dumped Windows several years ago and have never looked back but there are some programs that are just not available for Linux (Garmin map updates for one).  You have to weigh the pros and cons of maintaining Windows for one or however many programs you just have to run.  I think it is a toss up when there is only one or two programs that have no Linux equivalent that you need.  Just my two cents.

---

