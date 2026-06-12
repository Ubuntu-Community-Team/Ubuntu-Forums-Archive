---
title: "Installing woes"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by Ligerzero on 2006-10-18
I tried installing ubuntu using instlux. It was already on the point of getting the files off the NZ linux server, then my laptop decides to die because i forgot that the power cable was off.

Now i restart, and all it is is just a cursor. nothing else
As the cd-rom drive in this is bung, is it possible to copy all of the files from the cd to the laptop hdd via windows? 

Any help would be really good, as i need the laptop up and running asap.

thx

---

### Post by gn2 on 2006-10-18
> **Ligerzero said:**
> I tried installing ubuntu using instlux. It was already on the point of getting the files off the NZ linux server, then my laptop decides to die because i forgot that the power cable was off.

Now i restart, and all it is is just a cursor. nothing else
As the cd-rom drive in this is bung, is it possible to copy all of the files from the cd to the laptop hdd via windows? 

Any help would be really good, as i need the laptop up and running asap.

thx

I have been told that this is possible, but have yet to try myself.

Fit HDD in another Laptop oor PC (using 2.5-3.5 IDE converter not USB enclosure) then install Ubuntu on it. (make sure you disconnect the other PC's own hard drive(s) first. 

Now re-install HDD in laptop and boot.

It should boot to a terminal prompt, type this command "sudo dpkg-reconfigure -phigh xserver-xorg" (without the quotes) and press enter.

This will allow you to reconfigure for the laptop hardware.

Like I say, I haven't tried it myself but I've been told it works......

---

### Post by Ligerzero on 2006-10-18
Ummm, i cannot do it that way as i dont have access to a convert, only USB external case for it.
Would copying the files from the cd onto the hdd make it boot into the installer?

---

### Post by gn2 on 2006-10-18
> **Ligerzero said:**
> Ummm, i cannot do it that way as i dont have access to a convert, only USB external case for it.
Would copying the files from the cd onto the hdd make it boot into the installer?

A 2.5-3.5 IDE adapter can be bought on eBay for pennies.

---

### Post by Ligerzero on 2006-10-18
nevermind. lol
just found that i could burn the image onto a dvd, and run it through there. Looks like the dvd-rom is stuffed for cd's

---

