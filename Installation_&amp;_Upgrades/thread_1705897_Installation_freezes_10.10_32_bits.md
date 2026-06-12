---
title: "Installation freezes 10.10 32 bits"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by Craphter on 2011-03-13
I have 2 HDD, one is 500 GB, the other is 70 GB, 1.5 GB RAM and a 256 MB nVidia graphics card.
In one HDD I have Win XP 32 bits, the other one is empty, and I want to install Ubuntu, so I downloaded the .iso 32 bits from the official page, burned it with the recommended software, no problems (I used the slowest speed).

I reboot the computer, BIOS > Boot from CD, and Ubuntu screen appears (sorta purple with black).
About 10 mins pass by, it's still "loading" or something, and, suddenly, it just freezes, out of the nowhere.

Here's a short vid of what happens:
[http://www.youtube.com/watch?v=zLRhOrR1OJ8](http://www.youtube.com/watch?v=zLRhOrR1OJ8)


I would really appreciate your help here, I'm quite desperate.
Craphter

---

### Post by Dutch70 on 2011-03-13
> **Craphter said:**
> I have 2 HDD, one is 500 GB, the other is 70 GB, 1.5 GB RAM and a 256 MB nVidia graphics card.
In one HDD I have Win XP 32 bits, the other one is empty, and I want to install Ubuntu, so I downloaded the .iso 32 bits from the official page, burned it with the recommended software, no problems (I used the slowest speed).

I reboot the computer, BIOS > Boot from CD, and Ubuntu screen appears (sorta purple with black).
About 10 mins pass by, it's still "loading" or something, and, suddenly, it just freezes, out of the nowhere.

Here's a short vid of what happens:
[http://www.youtube.com/watch?v=zLRhOrR1OJ8](http://www.youtube.com/watch?v=zLRhOrR1OJ8)


I would really appreciate your help here, I'm quite desperate.
Craphter

Hi Craphter, and welcome to UF.

 It sounds like you burned the .iso correctly. Did you check the md5sum of the download? 

[[COLOR="Blue"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
*I've heard there can be problems caused by certain applications used to burn the .iso. *

Also, you do know that if you have a usb stick aka flash/thumb drive, you can use that to install Ubuntu. It's much faster than a cd.
The directions on this site will lead you through it, on step-2, tick "usb stick" & "show me how" 
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Alternatively, you can use Unetbootin to create your live usb stick. Available here...
[[COLOR="Blue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

Best regards

---

### Post by kansasnoob on 2011-03-13
Right after the system/BIOS screen passes on boot you'll see a purple screen with two small favicons at the bottom. When that appears you have 3 seconds to press any key which should cause the language selection screen to appear followed by the boot options screen. 

At that screen select "Check CD for defects". That generally takes a few minutes to complete and, if successful, it'll say no defects found.

---

### Post by Craphter on 2011-03-13
> **Dutch70 said:**
> Hi Craphter, and welcome to UF.

 It sounds like you burned the .iso correctly. Did you check the md5sum of the download? 

[[COLOR=Blue]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
*I've heard there can be problems caused by certain applications used to burn the .iso. *

Also, you do know that if you have a usb stick aka flash/thumb drive, you can use that to install Ubuntu. It's much faster than a cd.
The directions on this site will lead you through it, on step-2, tick "usb stick" & "show me how" 
[[COLOR=Blue]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Alternatively, you can use Unetbootin to create your live usb stick. Available here...
[[COLOR=Blue]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

Best regards



> Right after the system/BIOS screen passes on boot you'll see a purple  screen with two small favicons at the bottom. When that appears you have  3 seconds to press any key which should cause the language selection  screen to appear followed by the boot options screen. 

At that screen select "Check CD for defects". That generally takes a few  minutes to complete and, if successful, it'll say no defects found.




Ok, thanks for the fast answer you guys.
I started by doing the md5sum, and it said no errors, the keys match.
Then, I rebooted, and did the "check disc for errors", and, after a few minutes, it said "found errors in 1 file".
Should I redownload the .iso?
Should I rewrite the CD?

And, by the way, I did know about the USB stick, but I only have one USB memory, and it's 1 GB, hence, I didn't even try it.

---

### Post by Dutch70 on 2011-03-13
> **Craphter said:**
> Ok, thanks for the fast answer you guys.
I started by doing the md5sum, and it said no errors, the keys match.
Then, I rebooted, and did the "check disc for errors", and, after a few minutes, it said "found errors in 1 file".
Should I redownload the .iso?
Should I rewrite the CD?

And, by the way, I did know about the USB stick, but I only have one USB memory, and it's 1 GB, hence, I didn't even try it.

Yes, I would try rewriting the cd, if you want to go that route. 
If your md5sum checked out, the download **should** be ok. 

ps. If your usb stick is 1GB, that's quite a bit more than your cd.

---

### Post by Craphter on 2011-03-13
> **Dutch70 said:**
> Yes, I would try rewriting the cd, if you want to go that route. 
If your md5sum checked out, the download **should** be ok. 

ps. If your usb stick is 1GB, that's quite a bit more than your cd.


LOL
Dude, I'm laughing quite hard right now...
700 MB < 1 GB
I ruled out the USB from the beggining since the official page says minimum 2GB, so I didn't even think of it.
Gonna try with the USB, since I already re-wrote the CD several times.
Thanks man!

---

### Post by Dutch70 on 2011-03-13
> **Craphter said:**
> LOL
Dude, I'm laughing quite hard right now...
700 MB < 1 GB
I ruled out the USB from the beggining since the official page says minimum 2GB, so I didn't even think of it.
Gonna try with the USB, since I already re-wrote the CD several times.
Thanks man!

:biggrin: Yeah, I was too. I started to say... "Wow, how big is your cd?" but I was concerned that it might not come across the right way. 

However I didn't know the site said minimum 2GB, or why it would. Anyway, if you have trouble with the universal usb installer, 
try unetbootin. It's very simple & has worked well for me.

good luck

---

### Post by Craphter on 2011-03-14
> **Dutch70 said:**
> :biggrin: Yeah, I was too. I started to say... "Wow, how big is your cd?" but I was concerned that it might not come across the right way. 

However I didn't know the site said minimum 2GB, or why it would. Anyway, if you have trouble with the universal usb installer, 
try unetbootin. It's very simple & has worked well for me.

good luck


Ok, I'm answering from Ubuntu now :D:D
THANK YOU dude, I'm REALLY happy with my new OS.
The installation was flawless! I just used my USB stick, and I do not know why the page says a minimum of 2 GB, when It went perfectly fine with 1 GB!
Anyways, thanks again!
Craphter

---

### Post by Dutch70 on 2011-03-14
> **Craphter said:**
> Ok, I'm answering from Ubuntu now :D:D
THANK YOU dude, I'm REALLY happy with my new OS.
The installation was flawless! I just used my USB stick, and I do not know why the page says a minimum of 2 GB, when It went perfectly fine with 1 GB!
Anyways, thanks again!
Craphter

Great, glad you got it working & it's always nice to hear a glory story. 

So, I take it this thread is "Solved"?

---

### Post by Craphter on 2011-03-14
> **Dutch70 said:**
> Great, glad you got it working & it's always nice to hear a glory story. 

So, I take it this thread is "Solved"?


Sure, how to change it lol

---

### Post by Dutch70 on 2011-03-15
> **Craphter said:**
> Sure, how to change it lol

lol, check my sig.

click on "[COLOR="Red"]Thread Tools[/COLOR]" at the top of the page & you will see it in the drop down menu. 

Happy Ubuntuing :popcorn:

---

### Post by Craphter on 2011-03-15
> **Dutch70 said:**
> lol, check my sig.

click on "[COLOR=Red]Thread Tools[/COLOR]" at the top of the page & you will see it in the drop down menu. 

Happy Ubuntuing :popcorn:


Thanks! I tried around in "edit post" lol
Thank you, again, for the help! :D

---

