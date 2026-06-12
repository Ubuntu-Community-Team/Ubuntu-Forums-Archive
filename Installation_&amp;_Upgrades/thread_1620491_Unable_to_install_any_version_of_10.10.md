---
title: "Unable to install any version of 10.10"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by godsmack_dmx on 2010-11-13
[FONT="Book Antiqua"][SIZE="4"][COLOR="Green"]I'm trying to install Ubuntu 10.10 64-bit but when I'm using a CD after choosing try Ubuntu without any changes or install Ubuntu the load start and never finish.

When I'm using USB flash drive Ubuntu log in but the screen are a corrupted image from my windows so I removed the hard drive that contain windows on it and try again the screen goes black with a small colorful point on it.

and I tried the 32-bit version and same problem.

How can I fix this?[/COLOR][/SIZE][/FONT]

---

### Post by Dr. C on 2010-11-13
Was the CD and USB created from the same downloaded .iso? If so this may be due to a corrupt download so I would try to download again.

---

### Post by sikander3786 on 2010-11-14
Hi.

Please check the integrity of the downloaded image as mentioned above.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, try to burn a new disc at the lowest possible speed.

It would be handy to know your hardware specs. You might need to put in some boot options like **nomodeset** or **acpi=off**.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by godsmack_dmx on 2010-11-14
[COLOR="Teal"]I tried many download locations and it's same problem and I did check MD5SUM and the numbers matchs.

This is my PC:

MSI 890FXA-GD70
AMD Phenom II X6 1055T OC @ 3.2GHz
XFX GT240 512MB GDDR5
4GB Kingston DDR3 1600MHz
1TB WD Black 64MB cache SATA 6GB/s
1TB WD Green 64MB cache
160GB Maxtor 16MB cache ((Wich I want to install Ubuntu on it))
D-Link Wireless card[/COLOR]

---

### Post by godsmack_dmx on 2010-11-17
[FONT="Book Antiqua"][SIZE="4"][COLOR="Green"]Any help please?[/COLOR][/SIZE][/FONT]

---

### Post by Mark Phelps on 2010-11-18
Have you tried the following from post #3 above:

> It would be handy to know your hardware specs. You might need to put in some boot options like nomodeset or acpi=off.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by godsmack_dmx on 2010-11-20
[COLOR="Teal"]Yes I tried the following in post #3 Like nomodeset but I did't try acpi=off yet.

Any new ideas[/COLOR]

---

### Post by cogier on 2010-11-20
You could try the "Alternative CD" for installation. It uses less RAM which as you only have 512MB might help. The point in Post 3 is worth a try first.

---

### Post by godsmack_dmx on 2010-11-23
[FONT="Book Antiqua"][SIZE="3"][COLOR="Teal"]I have tried the acpi=off and it gave me this message 


unable to find a medium containing a live file system[/COLOR][/SIZE][/FONT]

---

### Post by sikander3786 on 2010-11-23
> **godsmack_dmx said:**
> I have tried the acpi=off and it gave me this message 


unable to find a medium containing a live file system
Maverick has some problems with some specific hardware that why special boot options for specific machines are presented at boot. There are 6 of them and you need to try all of them one-by-one.

I know you have checked the MD5SUMs of the images, but did you try to check the disc for defects? There is an option just below Try, Install options on the same page. It might be a bad burn.... You may need to re-burn the disc at the lowest possible speeds (I use 4x).

---

### Post by godsmack_dmx on 2010-11-23
[FONT="Book Antiqua"][COLOR="Teal"][SIZE="3"]I actually checked the disc for defects and it OK, Maybe I should try the other versions of ubuntu 10.10

But could you gave the links of the different 64-bit versions of it please?   :D[/SIZE][/COLOR][/FONT]

---

### Post by sikander3786 on 2010-11-24
> **godsmack_dmx said:**
> [FONT="Book Antiqua"][COLOR="Teal"][SIZE="3"]I actually checked the disc for defects and it OK, Maybe I should try the other versions of ubuntu 10.10

But could you gave the links of the different 64-bit versions of it please?   :D[/SIZE][/COLOR][/FONT]
The only versions I would recommend are 10.10 and 10.04. Don't install any older versions as support for them is likely to end within 5 months.

You can find both 10.10 and 10.04 on the official Ubuntu website.

---

### Post by godsmack_dmx on 2010-11-24
[FONT="Book Antiqua"][COLOR="Teal"][SIZE="3"]Thanks a lot[/SIZE][/COLOR][/FONT]

---

