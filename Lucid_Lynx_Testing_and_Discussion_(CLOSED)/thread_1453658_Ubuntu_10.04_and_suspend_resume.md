---
title: "Ubuntu 10.04 and suspend resume"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ali780 on 2010-04-13
Hello,

6 month ago, when I installed Ubuntu 9.10 on my 
Laptop (Znote 6224),
I had problem with suspend resume. In fact when I closed the lid and open it again, Ubuntu could not resume. It was very bad for me, So I ignored 9.10 and I returned to 9.04.

Now my question is: 
Does this problem solved in the new version 10.04?
has anybody tried the beta version of 10.04?

Regards
/Ali

---

### Post by mperry on 2010-04-13
I'm interested in the continuing saga of suspend/resume as well; but for me with beta 2, I've done a few tests on my IBM thinkpad T60. I've closed the lid with VirtualBox running a Windows7 guest with Outlook 2007 running in it overnight. Changed network locations to a coffee shop, sprinkled my own brand new of user stupidity on things, and then resumed the next day. Not a problem at all. What I have noticed is that it takes a bit longer now for a lid close event to actually trigger something like a suspend compared to 9.10 which operated flawlessly. 

I guess I'm lucky because I have two T60 thinkpads and I can install things side by side, revert back if need be, etc because I have multiple laptop sata disks with different things on them that I can boot like Win7 native, Ubuntu 9.x...

Its always worth a try to see if something is different but you could find out that the one thing is fixed but the beta has borked another important thing. You just never know...

---

### Post by pdw on 2010-04-13
I'm running 10.04 on a full-intel Lenovo N200, but about 60-70% of the resumes I either get a black screen (sysrq+b works tho) or a plain GDM login prompt (meaning no apps = not a resume) or I do get back to my desktop but no apps again.

I can't recall recall a time I got all my apps back :)

Anyway i'm not bitching, just feels kinda lame ~2 weeks to stable...

---

### Post by ali780 on 2010-04-13
I am afraid why the Ubuntu team don't try to solve this problem.
I could not use ubuntu 9.10 for this reason.:(

---

### Post by cheapsaket on 2010-04-13
Both suspend & hibernate - resume work for me on my configuration (see sig)

---

### Post by Ric_NYC on 2010-04-13
They didn't work until I removed fglrx.


**ATI Radeon Xpress 1200.**

---

### Post by zoomy942 on 2010-04-13
I just want my laptop to respond to me closing it.

---

### Post by BrokeMahPC on 2010-04-13
Suspend / Resume worked on 9.10 for me - not so now.
Just tried a suspend / resume and I get the desktop back with this open but there is also a crash report on the task bar which says:
> Your system encountered a serious kernel problem.
Your system might become unstable now and might need to be restarted.
You can help the developers to fix the problem by reporting it.Beta 2 i386 desktop
Intel E7300 Core 2 duo
ATI Radeon HD4670
FGLRX ATI proprietary driver
Kernel 2.6.32-20

---

### Post by zengeos on 2010-04-13
I used to have occasional crashes on resume, but not frquent.  However, with the latest daily update, I not only got the same crash report as indicated above in the thread, but my logout button is now gone.


Oops!  Guess that's one way to create a captive audience!!

---

### Post by Johan Karl Johansen on 2010-04-13
Suspend works for me the first time, flawlessly, but the second time it freezes immediately after i press the power button. This happens every time i try.

as it works the first time after a reboot i assume there is only a minor bug, bt i cant find anything helpful on the net about it.

My laptop is an Acer aspire 7720G

---

### Post by ali780 on 2010-04-14
> **Chauncellor said:**
> As of Karmic for me, suspend is broken. I tested Lucid on my setup, and it works just peachy for me.

So I can be hopeful in my case:P

---

### Post by krazyd on 2010-04-14
If you're running a binary driver (nvidia or fglrx), you are lucky suspend/resume works at all. 

There is nothing anyone outside of nvidia or AMD can do to help you with this - that's the price of loading closed-source (and often buggy) modules into the kernel.

---

### Post by StuartN on 2010-04-14
Suspend and resume (and hibernate) worked great for me up until 9.10, and then was simply unpredictable.

Ubuntu 10.04 Beta 2 will appear to suspend, but has not so far resumed. If I force a hardware reboot by power-cycling then my Broadcom wireless networking has been disabled. When I re-enable it (and enter the keyring password), my mouse pointer is locked. Pressing a cursor key unlocks it.

But no, suspend and hibernate are not yet functioning.

---

### Post by julianb on 2010-04-14
Been running Lucid on a few different Asus netbooks and the suspend/resume performance seems flawless.

I also don't do suspend and resume as much on those machines because shutdown/startup are also very quick.

---

### Post by ali780 on 2010-04-14
Anybody knows why the Ubuntu team do not try to fix the suspend/resume problem? It is very important for Laptops.

---

### Post by fatleader on 2010-04-14
its quite odd, my suspend works fine up to the first time i suspend. 
then, when i resume my session, i lose my ability to use the fn key on my keyboard, which becomes quite annoying when i need to run the laptop on battery since i am not able to adjust the screen brightness. 
and its not only with 10.04, but also with 9.10, just not as frequent. 

but its nothing major.

---

### Post by MrCheese on 2010-04-15
I have an HP nc6220 laptop, power management set to blank screen when lid is closed. On opening again it will unblank but soon the display starts going off for a few seconds at a time & the whole thing slows down. This has happened since 9.10 - this was one reason I installed Lucid & I wish I hadn't bothered. I get the same issue with Linux Mint which is also derived from Ubuntu.  I'm seriously considering going to Debian Lenny which works perfectly, or back to 9.04 & risk losing support at the end of the year.

Paul.

---

### Post by autark on 2010-04-15
> **krazyd said:**
> If you're running a binary driver (nvidia or fglrx), you are lucky suspend/resume works at all. 

There is nothing anyone outside of nvidia or AMD can do to help you with this - that's the price of loading closed-source (and often buggy) modules into the kernel.

My experience is the opposite: only by using the nvidia proprietary driver have I been able to suspend/resume/hibernate properly on my nvidia-powered machines. I haven't been able to try nouveau yet, so maybe things are different now, but the open-source nv driver has never been satisfactory for me.

---

### Post by ali780 on 2010-04-15
I could suspend and resume in 9.04 without any problem but i. 9.10 I could not.

---

### Post by aethralis on 2010-04-15
I have had numerous suspend problems with T41, what worked just perfectly with 9.10. But as for now I have not encountered some pattern in failing to resume, so i have been hesitant to file a bug.

Edit: There is already one: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557224](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557224)

---

### Post by scaine on 2010-04-15
> **ali780 said:**
> I am afraid why the Ubuntu team don't try to solve this problem.
I could not use ubuntu 9.10 for this reason.:(

Sorry - had to laugh at this, given your signature.

If you want to troubleshoot suspend/resume, you really can't do it in a forum, sadly.  There's too many variables - motherboard, graphics card, bluetooth, wifi card, etc, etc.  And that's just hardware.  Then you have to ask are you free or proprietary drivers, do you have any extra kernel modules loaded, like omnibook.  Finally, external factors come into play, like what USB devices are you using that could interfere.  It's a minefield. 

This is the only link I could find on the official documentation to get people started :
[https://wiki.ubuntu.com/specs/KernelLucidSuspendResume](https://wiki.ubuntu.com/specs/KernelLucidSuspendResume)

Anyone know of a better one?

---

### Post by krazyd on 2010-04-15
> **autark said:**
> My experience is the opposite: only by using the nvidia proprietary driver have I been able to suspend/resume/hibernate properly on my nvidia-powered machines. I haven't been able to try nouveau yet, so maybe things are different now, but the open-source nv driver has never been satisfactory for me.

You are lucky. And the open-source nv driver was so badly obfuscated by nvidia that no-one really was able to work on it.

At least with nouveau if there are any problems you can report bugs to the developers.

---

### Post by krazyd on 2010-04-15
> **ali780 said:**
> I could suspend and resume in 9.04 without any problem but i. 9.10 I could not.

Do you use a proprietary graphics driver?

---

### Post by sgage on 2010-04-16
I don't have a laptop, but on my desktop running an 8500GT, the nvidia (proprietary) drivers work perfectly, allowing smooth resume from suspend. The nouveau drivers suspend, but it's more like death - it never resumes. It's been this way from the beginning.

---

### Post by julianb on 2010-04-16
I have been using several different eeePC netbooks, and suspend / resume has so far performed flawlessly in Ubuntu Lucid.

In Karmic, I was never able to get suspend/resume to work.

---

### Post by ali780 on 2010-04-22
No more test?

---

