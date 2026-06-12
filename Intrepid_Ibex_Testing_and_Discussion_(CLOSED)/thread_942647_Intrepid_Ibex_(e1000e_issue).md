---
title: "Intrepid Ibex (e1000e issue)"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by k2chris1983 on 2008-10-09
Hello,

I was wondering if the e1000e issue is still a risk on Linux 2.6.27-4? I had ubuntu 8.04.1 installed with no problems but when I went to install a clean version of 8.10 Beta for Gnome 2.24 which I wanted to test drive it. 

After the installed went FINE and everything came up (beside the NIC) I noticed I couldn't connect to the Internet... So I did a search for "ubuntu 8.10 e1000e" and found some things I wish I found out before installing this... 

So I may just F my motherboard (NIC) over now... Awesome... \\:D/

*Not Mad just: yeaaaaahh*

---

### Post by Elfy on 2008-10-09
> Update 3: The e1000e driver is DISABLED on the upcoming Intrepid Beta. Following the beta, all daily CD spins and subsequent releases incorporate a fix for this bug and reenables the driver (safely). There is still no update on how to reverse this problem once you've been bitten, though it seems like that is in the works.There is a sticky on the interpid forum - [http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

If you've had the problem with the beta then I would look there, it should have been blacklisted on the beta.

It might be that that it will work - as it was blacklisted and didn't get affected - but as it is blacklisted you can't connect as yet

---

### Post by dabl on 2008-10-09
You don't want that 2.6.27-4 kernel, or any kernel before 2.6.27-5, if you have an Intel Gigabyte ethernet chip.

Get an ISO from the daily build [[COLOR="SeaGreen"]**here**[/COLOR]](http://cdimage.ubuntu.com/daily/current/) and you'll be fine (at least on that subject) -- they have the kernel patch.

---

### Post by k2chris1983 on 2008-10-09
> **dabl said:**
> You don't want that 2.6.27-4 kernel, or any kernel before 2.6.27-5, if you have an Intel Gigabyte ethernet chip.

Get an ISO from the daily build [[COLOR="SeaGreen"]**here**[/COLOR]](http://cdimage.ubuntu.com/daily/current/) and you'll be fine (at least on that subject) -- they have the kernel patch.

Hey thanks, I will download the current ISO and give that one a try. I just hope I didn't F my motherboard up already... 

Also Thanks for the URL forestpixie. I will check that out!

---

### Post by k2chris1983 on 2008-10-09
Ok it finally works with the newest current build which I think ubuntu should put a "Warning" note on the beta but we have like 21 more days until the finally one comes out... Just a thought

Thanks again dabl and forestpixie.

---

### Post by bash on 2008-10-09
> **k2chris1983 said:**
> Ok it finally works with the newest current build which I think ubuntu should put a "Warning" note on the beta but we have like 21 more days until the finally one comes out... Just a thought

Thanks again dabl and forestpixie.

Umm ... you know before advising that Ubuntu should put out a warning on the beta, I would advise you to actually read the release notes for the beta. Take a guess what you will find there.

---

