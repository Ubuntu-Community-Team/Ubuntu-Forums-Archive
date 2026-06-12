---
title: "Jaunty WiFi strange Failure"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Greg Xix on 2009-04-07
I downloaded & installed Jaunty Beta on my laptop last night to play with: a CQ50-139wm(I know, its a cheap laptop). Jaunty looks pretty nice. But if I 'Activate' the "madwifi" in the Hardware Drivers screen and reboot the internet goes away and any attempts at reinstalling it via Synaptic are futile.

Now right after installation, the WiFi internet connection from my house is working on Jaunty. I thought "okay great!!"; It takes a lot of work to get that up and running with Intrepid and now I see it works out-of-the-box on Jaunty. Pic #1 is what I had after my first login & after I entered the password for the local router.

[ATTACH]109020[/ATTACH]


This is my ifconfig with wifi in working condition:


[ATTACH]109030[/ATTACH]

Here is my Hardware Drivers with wifi in working condition, so when I press the 'Activate' & reboot, its bye-bye wifi:


[ATTACH]109021[/ATTACH]



This is what it looks like when I select "Activate" the "madwifi" Hardware Driver and reboot; here is the carnage:


**ifconfig -a**

[ATTACH]109031[/ATTACH]


**and Hardware Drivers**


[ATTACH]109024[/ATTACH]


Of course I could just simply install Jaunty and ignore the Hardware Driver activation. But this still seems like a error that many people could run into, as the CQ50 series(and now CQ60) of laptops are inexpensive & fairly popular and I assume they all use similar WiFi technology on those laptops.

I just hope that this error reaches the eyes of somebody here who can forward this to the Ubuntu braintrust :KS as a bug. Which is why I posted all of those screecaps.

---

### Post by ibuclaw on 2009-04-07
My suggestion would for you to post a bug report in Launchpad, as you are probably not alone when receiving the error.

Consult this thread for bug posting guides: [http://ubuntuforums.org/showthread.php?t=1106122](http://ubuntuforums.org/showthread.php?t=1106122)

Regards
Iain

---

### Post by Bastanteroma on 2009-04-08
Is your bug that the warning text, "Only activate this driver if you have problems with your wireless LAN connection," is too mild? Or that there should be a clearer way for the curious to undo what they've done?

I vaguely recall reading that it's difficult to distinguish between cards that need the open driver and those that need the restricted one, which explains the uncertainty of the text.

---

### Post by Greg Xix on 2009-04-08
> **tinivole said:**
> My suggestion would for you to post a bug report in Launchpad, as you are probably not alone when receiving the error.

Consult this thread for bug posting guides: [http://ubuntuforums.org/showthread.php?t=1106122](http://ubuntuforums.org/showthread.php?t=1106122)

Regards
Iain



My only concern is, can we post pictures on Launchpad as well? A picture is worth a 1000 words you know.

---

