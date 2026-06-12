---
title: "Scary no-boot scenario!"
date: 2010-01-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-01-13
I've been doing iso testing the past two days, and today I was troubleshooting a parted/Gparted bug and upon reboot to my installed Lucid I ended up with an "abnormally large" blinking cursor at the left and about 2 inches below the top of my screen.

The keyboard did show some response but uncommon at best. Alt + SysReq + B did nothing, nor did Ctrl + Alt + Delete. So after a few minutes of fiddling I tried a hard reboot and got nothing but system screen ------ forever!!!!!!!!

At that point Ctrl + Alt + Delete should reboot but wouldn't so I'd hard reboot and get the same thing! So I tried, by disconnecting components, booting from only CD, only hard drive, etc. No good.

So I finally had to really walk things back. I grabbed the last of my favorite low cost MoBo's:

[http://www.via.com.tw/en/initiatives/empowered/pc2500_mainboard/index.jsp](http://www.via.com.tw/en/initiatives/empowered/pc2500_mainboard/index.jsp)

Darn I wish I had more of those!

Anyway a new one worked, so OK, I killed a cheap MoBo ------- but as soon as tried booting into Lucid I got the same thing! Holy kerschmoliens!

Well I did get them both working again by pulling the CMOS battery and then rebooting with the VIA disc to reconfigure the setup and BIOS but what a pain!

Oh, and parted/Gparted does have bugs in Lucid :P

Care to help?

---

### Post by VMC on 2010-01-13
godallmighty, that would be scary. Glad it ultimately wasn't a blow motherboard. 

BTW, the VIA motherboard looks real nice.
 How does it work with Lucid? What are your boot times?

---

### Post by ronacc on 2010-01-13
I don't know about the experience kansasnoob has had but I will never buy anything with via graphics again , to put it bluntly their linux support is nonexistent despite what that add says .

---

### Post by kansasnoob on 2010-01-13
> **VMC said:**
> godallmighty, that would be scary. Glad it ultimately wasn't a blow motherboard. 

BTW, the VIA motherboard looks real nice.
 How does it work with Lucid? What are your boot times?

These are the same MoBo's that came in the $200.00 Wally World Everex w/gOS. Club IT had them for $59.99 w/free shipping about 2 years ago.

I originally bought just one, then two more, and just before Club IT/PC Club went belly up I bought 20 @ about $55.00 each. I can't find them anymore.

The only actual failure so far was the ethernet died on one after about one year so I just popped in a PCI card I had laying around.

But these were mostly for seniors computers, people that had paid a grand + for a box with a CPU that could be used for a boat anchor and maybe 128MB of RAM. Rememeber these bad boys:

[http://upload.wikimedia.org/wikipedia/commons/8/83/Pentium_II.jpg](http://upload.wikimedia.org/wikipedia/commons/8/83/Pentium_II.jpg)

Anyway I really liked these boards. Very simple and extremely energy efficient. IMHO better than the all-in-one Intel ATOM boards.

---

### Post by kansasnoob on 2010-01-13
> **ronacc said:**
> I don't know about the experience kansasnoob has had but I will never buy anything with via graphics again , to put it bluntly their linux support is nonexistent despite what that add says .

For these the openchrome drivers have always been in Synaptic since at least Gutsy. No 3-D but what does a blind old man need with that?

---

### Post by ronacc on 2010-01-14
the board I have has a unichrome chipset and at that time ( 2 years ago ) the only driver that worked was vesa, and that not very well .But what really turned me off was their attitude when I emailed their tech , basically their response was quit fooling around with that linux crap and install a good OS like xp or vista . I installed an Nvidia card and swore off VIA .

---

### Post by ranch hand on 2010-01-14
> **ronacc said:**
> the board I have has a unichrome chipset and at that time ( 2 years ago ) the only driver that worked was vesa, and that not very well .But what really turned me off was their attitude when I emailed their tech , basically their response was quit fooling around with that linux crap and install a good OS like xp or vista . I installed an Nvidia card and swore off VIA .
That would do it for me.

---

