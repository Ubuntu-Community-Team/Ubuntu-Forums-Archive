---
title: "Is updating from cd vs net possible?"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by skew on 2006-09-01
I'm starting to get the feeling Ubuntu isn't worthwhile for dial-up users.
Please show me i'm wrong... 

I installed Ubuntu from a cd onto one of two home computers then updated one of them over the net, which took over 14+ hours to complete on my dial-up account. (no asdl here)
  
  I now want to update ubuntu on the other system but can't afford to go through another long connection to do so. I burned all the updated (.deb) files from the first install onto a dvd but am going through dependency hell trying to install them one by one. Is there any easier way to do this? It seems ridiculas to already have all these files available and not be able to easily install them. ](*,)

 Is it possible to have *dpkg* look for a packages dependecies in the same directory as it being installed from? **ANY** help would be greatly appeciated!

---

### Post by gsdefender on 2006-09-01
> **skew said:**
> I'm starting to get the feeling Ubuntu isn't worthwhile for dial-up users.
Please show me i'm wrong... 

I installed Ubuntu from a cd onto one of two home computers then updated one of them over the net, which took over 14+ hours to complete on my dial-up account. (no asdl here)


I perfectly now what this means; some colleagues here at the University of Palermo have the same problem. :sad: 

>   
  I now want to update ubuntu on the other system but can't afford to go through another long connection to do so. I burned all the updated (.deb) files from the first install onto a dvd but am going through dependency hell trying to install them one by one. Is there any easier way to do this? It seems ridiculas to already have all these files available and not be able to easily install them. ](*,)


It's true.

> 
 Is it possible to have *dpkg* look for a packages dependecies in the same directory as it being installed from? **ANY** help would be greatly appeciated!

dpkg -i just installs the packages you specify to, so dpkg -i /media/cdrom/packagename.deb does what you want. Or maybe you're referring to other utilities, like apt-get or aptitude?

---

