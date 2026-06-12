---
title: "Software properties"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-08-30
Why is it that on a new installation of Ubuntu Dapper Drake 6.06.1 whihc I just completed, that when I go into software properties that I see 2 instances of **"CD disk with Ubuntu 6.06 LTS (Binary) Officially supported Restricted copyright"**, one of which is check and the other is NOT checked ?

Why is this same listing being shown twice ?  Is this a bug in the installation ?  Should I just remove one of these listings or should I check both of them.

On another matter, when I do a search in Synaptic for "FGLRX" I get 3 listings found (including 1 for **control** and another for **dev**).  If I want to add the fglrx driver for my video card, do I install all 3 of these or just the driver ?

Thanks.

---

### Post by whizbaby on 2006-08-30
For your first problem, look at your /etc/apt/sources.list (e.g. by typing "less /etc/apt/sources.list" in a terminal) if there really is a double entry (this would be the case if two lines EXACTLY match). If so, remove it with an editor (e.g. "sudo nano /etc/apt/sources.list") and "sudo apt-get update".
While editing the file you should uncomment all other repositories.
On to the next:
the driver - drives
the control - is a graphical interface to the driver
the dev - is usefull only if you want to help to develop the next version of the driver or want to write your own driver ...

---

### Post by wpshooter on 2006-08-30
Thanks for your reply.

But I am more interested in WHY these 2 entries are duplicated in the first place.  

This has to be either a flaw in the install process or some type of hardware problem.  This is a brand new install, and I just opened the software properties under administration, so I don't think there is anything I could have done to cause this.

I am beginning to believe that they have a lot more work that they need to do on the installation process of this O/S in particular and on the O/S in general.  Things like this make me wonder if this O/S can be trusted with any fairly critical business applications or if it is only good for home/entertainment use. 

Thanks.

---

### Post by whizbaby on 2006-08-30
First thing, do not get confused about OS and graphical toys, these are different things.
Second, if you had looked into your /etc/apt/sources.list you would have seen that for every repository there's two entries, one normal (prefix deb) and one for the security updates (deb-src). I guess that on a cd repository both are the same, but apt needs two entries, so you only have the impression to 
have a double entry.(if there REALLY was a double entry it would be gone after doing "sudo apt-get update")
Third, Ubuntu is a make_user_friendly(debian) which makes it the most modern and professional OS ever made.
So:
relax and watch den blinkenlight

---

