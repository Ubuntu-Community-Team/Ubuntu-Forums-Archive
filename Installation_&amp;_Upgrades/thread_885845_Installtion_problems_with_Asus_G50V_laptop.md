---
title: "Installtion problems with Asus G50V laptop"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Biciclettapc on 2008-08-10
Ok, 4th try on installing Ubu 8.04 on this laptop.  I'm wanting a dual boot with vista.  Pretty much have to use Win-blows since thats what I HAVE to use to pay the bill, lol.

Here is the laptop.  Yes, its a gamer but I need the VC for engineering graphics (solid modeling)  [http://www.bestbuy.com/site/olspage.jsp?skuId=8906133&type=product&id=1213046768588](http://www.bestbuy.com/site/olspage.jsp?skuId=8906133&type=product&id=1213046768588)

Now, I first tried the 64 bit version (2x) and it errors somewhere around the grub installtion.  So, I d/l'd the alternative version and it hit the same problem.  I then tried the i386 version and have the same issue.

Why?

I am sort of a newbie with Ubu, but have it running on 2 other machines in my house without any issues.  

I suspect that the Nvidia9700gt VC and or possibly the 4gig of ram might be part of the problem.  

Help!

Thanks
Paul

---

### Post by mfaust731 on 2008-08-10
Paul, we are going to need the error code you see if you would like any accurate help.

---

### Post by Biciclettapc on 2008-08-10
re-installing again soon.  Have to reinstall vista first since I am unable to use the partition Ubu created when I try re-installation of that, guess its b/c it craps out before it finishes.

---

### Post by Biciclettapc on 2008-08-10
Very quick flash of red saying install [fail]

Then a command prompt.....  

I then end up with a page full of 
[612.807***] Buffer i/o error on device sr0, logical block 2944**

(* = number)

Then lines of 

[612.809****] SQUASHFS error: and a whole list of failed blocks, frags, caches

it then locks up......

then if I hit the power button to shut down it begins a non-stop scroll of errors

---

### Post by mfaust731 on 2008-08-10
looks like hard drive issues, but im not sure
any other ideas?

Bump!

---

### Post by Biciclettapc on 2008-08-10
installed inside of windows....

But working on getting the internet working

---

### Post by zshift on 2008-08-10
I have the exact same laptop with the exact same issue...
i think it either has to with the new centrino 2 chipset (pm45)
or the nvidia 9700m gt. also, when it crashes to root login, pressing power button or typing ay form of shutdown command (i tried `sudo shutdown -r now`) causes infinite of the mentioned error. The funny thing is that asus has express gate preinstalled, which is based off of linux, so the must be SOME way of getting ubuntu to work. HELP LINUX EXPERTS!!!!!!!!

---

### Post by Biciclettapc on 2008-08-11
I was able to install inside of windows on a 30g partition without any installation issues, it produces a dual boot option after re-start.

It did not detect much with drivers.  I have no internet connection through hard wire and need that to update and get other things running.

---

### Post by WhiteFofito on 2008-08-11
News about the G50V, well i have that laptop so i start looking about drivers and i found something bad :(.

Good:
Madwifi is working wit the atheros 9k series so probably in some weeks or days wireless will work...

BAD:
Graphics, nvidia no news about 9700GT...
Sound: i didnt found something about the azalea drivers..

maybe in some months everything should work :) be patient and lets work whit VGA mode and the never fail RJ45.

---

### Post by Biciclettapc on 2008-08-11
If I can get the hardwire internet to work I can hold on the rest.  Havent had any time to work on it since I finally got it loaded, maybe this evening I can and post my trouble areas

Thanks and lets hope for the best with the G50.  Its a sweet computer so far, looking forward to seeing how solid modeling graphics work with the 9700 card.  (Inventor / Solidworks)

Paul

---

### Post by mfaust731 on 2008-08-11
Paul, did I tell you my e is running Ubuntu!

---

### Post by Biciclettapc on 2008-08-11
on the touch screen?

---

### Post by zshift on 2008-08-14
I was looking at my laptop and the sound is a realtek chipset (vendor id 10ec, hardware id 0663) i wasn't able to find anything about it, im looking into asus website now. azalea is a term used by intel that is justa code name for HDA (high definition audio) that supports intel's standards. also, LAN doesnt work in ubuntu for me even though ubuntu is telling me it has a connection. I was looking in vista device manager and the lan doesnt even show up. please check your laptop as there may be a flaw with LAN in all of the models. i hope this isnt the case though.

---

### Post by Egarretsen on 2008-12-24
Please try installing Hardy Heron, in the install menu use acpi=off or MAXCPUS=1, this worked for me. After installing on my asus X56TR notebook. After this i could run hardy but vista failed. This was solved by editing the menu.list. hda(0,0) had to be changed into hda(0,1), otherwise vista would come up big (giant) red error saying something about recover.dat. This is due to the recover partition which is not seen bij ubuntu, so grub tries to load Vista from (0,0) and not (0,1). Hopes this helps some people for i had problems for almost a week. Intrepid Ibex is not working for me, problems with the 7.4 XORG version.

---

### Post by seuaniu on 2008-12-28
I was having the same problem with my G50 (bought from newegg which is a different model than the best buy version) and it was the drive settings that were making the install go haywire.  Switching the drive from "enhanced" to "compatible" mode in the BIOS fixed it for me.  Be warned though, this will nuke your vista install.  For some reason, vista won't boot if you change the drive mode.

---

### Post by alkasir-33 on 2009-11-08
[CENTER][SIZE=4]Dear Sir, Good evening[/SIZE]
[SIZE=4]I own a laptop ASUS Model Purchased without a floppy discs for programs the device[/SIZE]
[SIZE=4]Formate has worked for the device then excised all programs and applications of computerized Noise all the definitions from the website of the company, but here the question[/SIZE]
[SIZE=4]I Express installation program, but the program does not work please help in the way the installation and repair of errors possible in such a situation and I hope to help as needed and thank you[/SIZE]
[SIZE=4]of the program with the knowledge I have Windows 7[/SIZE][/CENTER]
 
[CENTER][SIZE=4]Please help those who have the DVD accompanying applications for computers from the company I would like a copy if possible please please[/SIZE][/CENTER]

---

