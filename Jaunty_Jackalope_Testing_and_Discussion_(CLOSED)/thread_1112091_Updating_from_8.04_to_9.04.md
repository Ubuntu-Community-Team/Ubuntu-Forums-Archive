---
title: "Updating from 8.04 to 9.04"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by alexham on 2009-03-31
Hi, folks,

I am running Ubuntu 8.04 and the update instructions on 9.04 website do not work on my system - i.e. <Alt><F2> does not bring up update manager and when I start it from System/Admin it does not show that an upgrade is available.

So, how do I upgrade to 9.04?

Thanks,

Alex

---

### Post by Therion on 2009-03-31
Jaunty is still in Beta so the process is a little different...  My suggestion would be to do a clean install using a daily build CD.

If you insist on doing a dist-upgrade, you use ALT+F2 and type in **update-manager -d**.  Follow the prompts from there.

---

### Post by James_Lochhead on 2009-03-31
> **Therion said:**
> Jaunty is still in Beta so the process is a little different...  My suggestion would be to do a clean install using a daily build CD.

+1

I first installed using the Internet from my then current install and it was very buggy. A clean install fixed everything.

---

### Post by James_Lochhead on 2009-03-31
If you still want to do it:

Press alt+f2. In the box that pops up type:

update-manager -d

Then press enter.

---

### Post by drs305 on 2009-03-31
Additionally, to do the update online you would first have to upgrade to 8.10 and then to 9.04. Skipping versions is not supported or recommended.

---

### Post by alexham on 2009-04-01
> **drs305 said:**
> Additionally, to do the update online you would first have to upgrade to 8.10 and then to 9.04. Skipping versions is not supported or recommended.

Thank you drs305.  I did not know how to update, so I downloaded a copy of 8.10 and burned it to CD.  Whilst I was doing that I read the instructions and found how to update.

Will the CD give me the option to upgrade or is it better to use the Update Manager?

Thanks,

Alex

---

### Post by drs305 on 2009-04-01
The CD will give you a 'fresh' install, meaning that unless you have a separate /home partition (which you would have had to take special steps to create), it will make a new install and keep nothing of the older one. 

Since you have just installed the system and probably haven't spent much time configuring it, I would recommend just installing from the CD rather than updating what you already have on your machine.

Here is the ubuntu guide on installing 8.10:
[https://help.ubuntu.com/8.10/installation-guide/i386/index.html]("https://help.ubuntu.com/8.10/installation-guide/i386/index.html")

---

