---
title: "Failed &quot;read cd/dvd capacity&quot; packet command on Emachines t6520"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by YelmleNoBrainer on 2005-10-20
Trying to install ubuntu breezy 64-bit on my emachines with an AMD athlon 3400+. I want to keep the pre-installed windows (more for comfort than anything, but I'm sure that will change). I put in a new 200G hard drive for ubuntu, so the setup is now:
200gig hd (master) for windows
200gig (slave) ubuntu. 

I had to run the initial install with the noapic nolapic parameters to get past a problem with recognizing the front usb/media reader ports on the machine. I am able to install ubuntu (breezy) onto the machine, but when the machine reboots to install the remaining packages, it comes up with a 
```
failed "read cd/dvd capacity" packet command was:
[xxx.xxxxxxxx]  (reserved error code) -- (asc=0x3a, ascq=0xfe 
``` 
at around 72%. I find this strange because there is not any kind of media in the machine. The "x" is just a string of numbers that changes with each failed packet command. I assume they are different packages, but I am very inexperienced outside of the M$ world. The packages look like language packets. The installation continues to what seems to be completion, but when ubuntu boots, gnome won't get going. It seems that the hard drive only holds so much of the install packages. 

What do I need to do to have a GUI on ubuntu? I've seen some people use apt-get, but I'm a novice and don't know how to use the text-based command screen well. Though if someone shows me the steps to take, I would be comfortable inputting the commands

---

