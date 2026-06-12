---
title: "Problems installing Xubuntu Hardy on IBM Thinkpad 390"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Jonathan.Lebreux on 2008-11-08
Hi everyone,

I searched the forums for a possible answer to my problem and i saw a couple of thread that look like my problem but doesn't get close to my prob, so here i go with mine!

I got an IBM Thinkpad 390 a couple of days ago wich was running on Windows 2000. I decided to get ride of this and to install Xubuntu.

The laptop specs are : Intel Celeron 300mhz something. 64mb of ram, and a 5gig hdd. 

Now, i downloaded the alternate cd version of Xubuntu and started the install after formating the beast.

Now the problem is : When i reach Installing package en-base the installation stay there for ages stuck at 1% and i know it will go forward but after several hours only...

I just reed a post about turning ACPI or something like that off in the menu at the begining of the installation. I'm doing it now and i'll keep you up to date with the result. 

So if anybody as an answer or a similar problem, your feedback are welcome!



Jonathan

---

### Post by Jonathan.Lebreux on 2008-11-08
***Update*** 


I plugged my Laptop to internet and to the home network. If it fails again (because it didn't worked with the ACPI off. Now will see what happen. 

If it doesn't work, I'll try a network install. Can someone give me the main guideline on how to do that or link me the thread about that?

Thank you!

I'll keep you up to date.

---

### Post by Jonathan.Lebreux on 2008-11-08
Well...since no one answered i'll post another update on the problem i am having.

I took a first chance with installing Hardy Heron wich = Failed

I took another chance with Intrepid Ibex... = Failed

Now, i'll try with Dapper Drake to see if it could work. 

I know that i could get a lighter Linux like puppy or etc but i am used with Ubuntu and i would like to keep going with this so this is why i am so "desperate" to get Xubuntu.

Jon

---

### Post by tyk on 2008-11-11
I would really look at Puppy or something.
On my Thinkpad T23 (perhaps same generation as yours), Xubuntu Hardy and Intrepid worked alright but were hardly quick enough. Dapper might actually be light but I can't say..
Other things:
Did you do MD5 checksum of burnt discs? (check CD for defects in installer menu)
What is the filesystem you are trying to install to? hope its ext3 or reiserfs formatted. and definitely make a swap partition of methinks 200-300 MB range.
AFAIK the acpi thing helps very few people.
hope this helps, all the best
:)

---

