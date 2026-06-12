---
title: "Graphics Unknown"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by djmuirhead on 2014-10-13
I took an SSD loaded with Ubuntu 12.04 out of a desktop computer running and AMD CPU and Nvidea grapgics card, and put it in an HP Elitebook 2560p notebook with an Intel i7 cpu. I expected to have to reinstall Ubuntu and start from scratch, but to my surprise, when I turned it on, Ububtu booted right up and I have been using it for over a year without problem. Updates have been accepted and installed and all was copacetic, until I tried to upgrade to Ububtu 14.04. After the upgrade tool loaded I got a message that the graphics system is not supported and a link to 

[https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D)

Since it's a fairly new computer that warning didn't sound right. I went to the System Details page which confirmed I have 8 GiB or RAM, and Intel i7 CPU at 2.70 GHz x4, and a 256 GB SSD, but for Graphics it simply says Unknown.

I expect that is a result of not reinstalling Ubuntu when I changed computers. My question is, how should I now proceed to get 14.04 installed properly? Do I need to reinstall 12.04 to get the graphics properly recognized before I upgrade? Do a clean install of 14.04 which would require a lot of backing up and saving profiles? Or, I hope, will the upgrade to 14.04 do a system check and recognize the graphics card in this computer, and install itself correctly. Sorry if it's a really stupid question. I did search and couldn't find any threads that really seemed on point.

---

### Post by grahammechanical on 2014-10-13
Graphics Unknown is a common sight in the Details page and has been there for years. Especially in 12.04. How do you know that 14.04 has not been installed properly? Or have you not yet upgraded to 14.04?

When taking a hard disk with Ubuntu installed from one machine to another machine we should revert to using an open source video driver because the new machine might have a graphic adapter by a different manufacturer and so the installed proprietary video driver would not be appropriate.

I always recommend that for upgrading to a newer version of Ubuntu we revert to an open source video driver because we will be getting new kernels and newer proprietary video drivers and I think that upgrading with a proprietary video driver installed is the reason why so many get a broken desktop on the first re-boot after upgrading. That is just my opinion.

So, can you get to a desktop? Can you open Additional Drivers and revert to open source drivers? What graphics does this new machine have? What does the manufacturer's specification say? Does it have integrated graphics? Did the upgrade complete?

Regards.

---

### Post by coffeecat on 2014-10-13
As grahammechanical says, the "graphics unknown" message is a well-known bug, but it doesn't mean that the system is not recognising the card. It shouldn't prevent you from upgrading. You can fix it by installing the package mesa-utils.

---

### Post by djmuirhead on 2014-10-13
Thanks for the helpful response. I cancelled the upgrade to 14.04 when I saw that message because I didn't want to be stuck in a slow graphic enviroment as the warning claimed. I'll look at switching to the open source video driver and try again.

---

### Post by djmuirhead on 2014-10-13
Thanks, coffecat. I'll look at the mesa-utils package.

---

