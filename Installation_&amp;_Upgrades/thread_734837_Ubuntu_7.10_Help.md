---
title: "Ubuntu 7.10 Help"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by Redbaron111 on 2008-03-25
Hi, 
I'm a complete newby at using Ubuntu (i am learning though, just slowly) and i need some help with removing Ubuntu, This is my current setup at the moment,
1st HDD - Windows XP installed
2nd HDD - Windows formatted, 
3rd HDD - Ubuntu 7.10 installed. 
these are all internal hdds
What i am hoping to do is remove the 3rd hdd with Ubuntu on it and whack that drive into a different computer for a dedicated Linux PC.  After i tried removing the hdd from my computer i continually got a error from GRUB when trying to boot my computer.  i plugged the 3rd hdd back in my computer and now it works fine.
My question to you is, what do i have to do to remove my Ubuntu hdd from my computer without losing any information on that hdd and leaving XP on the computer.  
Sorry if theres already a thread about this, i had a quick look around but didn't see anything.
Thanks,

---

### Post by forestpixie on 2008-03-25
You'll need to reinstall the win boot to the XP pc using the XP disc - boot with it and use recovery console to fixmbr.

For the buntu pc - you need to install grub - it can be done with the livecd. These pages will help, but I would download supergrub, burn it as an iso and boot with it - if you haven't got the xp disc - supergrub can also deal with the win boot as well.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-4e903f414fbe7a46a48c7b1ff7ee29c069841a5b](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-4e903f414fbe7a46a48c7b1ff7ee29c069841a5b)

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Redbaron111 on 2008-03-25
All fixed, Thanks so much!
Now just gotta dig up this other computer :D

---

### Post by forestpixie on 2008-03-25
No problem - gald to help

Can you mark thread solved please

---

