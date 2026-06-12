---
title: "XSplash issue during shutdown."
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hotstovejer on 2009-10-01
I am loving Karmic and all the new bells and whistles. Been using it since Alpha 2, after upgrading from Jaunty. Loving the look. Nice and clean... only one problem for me.

When I go to shutdown my home machine, the pretty white Ubuntu logo doesn't stay in one place. It scrolls like something move the vertical hold on my monitor. I had a similar issue with Jaunty, where when I would restart or shutdown, instead of having the Ubuntu logo lookin at me, I would get orange bars streaking down the screen. I made sure that usplash is installed, and I am not sure that there is a residual issue from upgrading from Jaunty, or if there is just an issue with my video device. 

I have an uptodate machine at work with Karmic, and the usplash logout works just fine. 

Home machine's hardware is 02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200] (rev a2)

Thanks!

Jeremy

---

### Post by Jay_Bee on 2009-10-01
that sounds like a bug, you should report it, and btw it's not xsplash (that is shown during boot up), it's good old usplash.

---

### Post by hotstovejer on 2009-10-09
Hmm, interesting. I reinstalled Karmic Beta completely, and everything was hunky dorey, until I installed the Nvidia driver. I wonder if that is the issue.

---

### Post by Longinus00 on 2009-10-09
> **Jay_Bee said:**
> that sounds like a bug, you should report it, and btw it's not xsplash (that is shown during boot up), it's good old usplash.

Both xsplash and usplash are shown during bootup. Only usplash is shown during shutdown, however.

---

### Post by Jay_Bee on 2009-10-09
Yes, that is true now, but at the time when I wrote that, only xsplash was shown on bootup.

---

### Post by Longinus00 on 2009-10-10
> **Jay_Bee said:**
> Yes, that is true now, but at the time when I wrote that, only xsplash was shown on bootup.

Sorry, I didn't realize how old this thread was. :(

---

