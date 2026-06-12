---
title: "Cl 56 install problems"
date: 2005-03-05
forum: Installation &amp; Upgrades
---

### Post by Threespot on 2005-03-05
Hi-

I'm pretty new to linux. I had my Cl 56 (actually chembook 2056) set up to dual boot Suse 9.1 and windows XP before, but I was having problems with Suse and my getting my wireless to work and I found that Ubuntu supports my laptop so I deleted the Suse and I plan on replacing it with Ubuntu.

It says in the install section that for my computer you need to set the fbcon to 770 otherwise the boot crashes, and that there are instructions in the install loader on how to do this. I've been working on it for a little while and I can't find how to do this in the install loader help files. I've tried doing linux fbcon=770 but I still get the same result, a blank screen. Any help would be great. Thanks

---

### Post by hcf on 2005-03-12
linux vga=771 at the boot prompt worked on my CL 56.

---

### Post by Olaf on 2005-03-13
[QUOTE=Threespot]Hi-
 I found that Ubuntu supports my laptop [/QUOTE]

Hi there, I have a CL56 laptop (zepto.dk) and would like to install ubuntu on it. Do you know of any ressources on the internet about this? Hopefully detailing how to configure the quickstar buttons, graphics card, etc....


I have googled a bit but haven't really found anything.

Thanks in advance ;o)

---

### Post by hcf on 2005-03-14
This one helped me out:
[http://heim.ifi.uio.no/~krisvh/linux/cl56.html](http://heim.ifi.uio.no/~krisvh/linux/cl56.html)

---

### Post by Olaf on 2005-03-15
Thanks, Hcf, that page looks good.  :-D

---

### Post by hcf on 2005-03-21
Olaf, the page is now updated with an added section on ACPI/sensors

---

