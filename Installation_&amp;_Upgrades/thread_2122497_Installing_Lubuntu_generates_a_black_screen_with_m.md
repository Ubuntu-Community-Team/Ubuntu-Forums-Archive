---
title: "Installing Lubuntu generates a black screen with mouse pointer"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by user_of_gnomes on 2013-03-05
I am trying to install Lubuntu 12.10 on a Compaq Presario 5BW154 (P3 / 384MB RAM) and although the live CD seems to work, Ubiquity seems to crash and I just can't get Lubuntu to install. 

The following error is displayed before Ubiquity launches: I/O space for GPIO uninitialized (judging from the search results, that means Ubiquity has crashed) after which I'm treated to a black screen with a mouse pointer. I can switch terminal and execute commands, though.

I have tried disabling the framebuffer and a few other things related to the videocard but this has had no impact whatsoever.

Is there another way to install Lubuntu or a way to troubleshoot Ubiquity?

---

### Post by carl4926 on 2013-03-05
Has the media checked as good?
Are you running the install without first going to the live session? This frees up RAM

---

### Post by user_of_gnomes on 2013-03-05
> **carl4926 said:**
> Has the media checked as good?
Are you running the install without first going to the live session? This frees up RAM

Thanks for the fast response, Carl4926.

I just did a check of the media and no errors were found.
I tried to both run the installer after the live CD had loaded and by selecting the installer from the boot menu. They both yield the same result.

---

### Post by carl4926 on 2013-03-05
The alternate cd lets you install in text mode I think

---

### Post by user_of_gnomes on 2013-03-05
> **carl4926 said:**
> The alternate cd lets you install in text mode I think

Carl4926, 

I have found the alternate CD and will let you know if it works.

---

### Post by sudodus on 2013-03-05
> **carl4926 said:**
> The alternate cd lets you install in text mode I think
+1
This works with less memory.

Lubuntu will run with 384 MB ram, but there is not much space for applications before swapping is needed. Try it, but be prepared to test some really tiny linux distro too, for example Puppy Linux. Puppy Wary may be a good choice for old hardware, but you can also try some newer Puppy version.

---

### Post by cortman on 2013-03-05
Check out the [SliTaz]("http://www.slitaz.org/en/") live CD for super lightweight as well.

---

### Post by user_of_gnomes on 2013-03-06
> **carl4926 said:**
> The alternate cd lets you install in text mode I think

That did the trick! 
Turns out the system only had 192MB of RAM (minus 16MB allocated to the videochip!). Not sure if that caused the problem but the alternate installer worked well regardless.

To everyone else; thanks for recommending the other distributions. I will look into these at some point when I have got more experience under my belt. I was preparing this computer for someone else and using a distribution I am unfamiliar with would make it hard for me to explain how to use it.

---

### Post by user_of_gnomes on 2013-03-06
Any way to mark a thread as solved?

---

### Post by mörgæs on 2013-03-06
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by user_of_gnomes on 2013-03-06
> **mörgæs said:**
> [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

Thank you.

---

