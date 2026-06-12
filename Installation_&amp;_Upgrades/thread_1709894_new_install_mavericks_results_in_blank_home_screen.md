---
title: "new install mavericks results in blank home screen"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by treblemaker48 on 2011-03-19
I have just installed ubuntu mavericks to an old laptop. I burned a cd and used it to install from. I choose to have the drive wiped and ubuntu installed to it. When I start up all goes well until the end.. I get a blank screen. It is not blank as in black. It has colors you expect to see with ubuntu but there are no controls... just a blank desktop with a cursor.

What do I do now?:confused:

---

### Post by Rubi1200 on 2011-03-19
Hi and welcome to the forums :-)

Please post the specifications for the computer, especially RAM and graphics card.

Thanks.

---

### Post by treblemaker48 on 2011-03-19
Product Name	HP Pavilion ze4610us Notebook PC
US Product Number	DS518U#ABA
Microprocessor	Mobile AMD Athlon XP-M Processor 2500+ (1.87GHz) with PowerNow! Technology
Microprocessor Cache	512KB (L2 cache)
Memory	256MB DDR SDRAM (1 x 256MB) at 266MHz
Memory Max	Maximum Memory 1024MB DDR SDRAM (2 x 512MB)
Video Graphics	 ATI MOBILITY RADEON 4X AGP and 3D architecture
Video Memory	 64MB DDR (shared)*
Hard Drive	40GB enhanced-IDE hard disk drive (4200rpm)

---

### Post by treblemaker48 on 2011-03-19
That was the specs I found online. I see that i really have 720000 kb memory... I upgraded it. Now I remember.

---

### Post by Rubi1200 on 2011-03-19
Hi,
you can try this:

as the computer is starting hold down Shift to bring up the GRUB menu. When the entry for Ubuntu is highlighted press "e" to edit.

Using the arrow keys to navigate find the line that ends with quiet splash.

Add nomodeset after quiet splash so it looks like this:

> quiet splash nomodesetThen, "Ctrl" + "x" to boot.

Let me know if that helps.

---

### Post by treblemaker48 on 2011-03-19
Hi, I tried holding shift when starting and nothing happened. It just started as usual. Late last night i found that I can start in different modes... desktop, safe, recovery console, user defined session. In safe mode I see the typical opening screen complete with things to click on like... aps places system etc. But because it is safe mode I can't download the recommended software.

I regards to starting as you suggested... what am I doing wrong?

Thanks for your help.
David

---

### Post by Rubi1200 on 2011-03-19
Yes, holding down Shift can be a bit tricky and you may need to play around with it to get the GRUB menu to come up.

---

### Post by treblemaker48 on 2011-03-19
Hurray.... it worked, so far anyway. I found the right way to get into the grub window. I am presently downloading stuff.

---

### Post by treblemaker48 on 2011-03-19
Hello. Just to update progress so far... after doing as suggested my machine started to download. The screen went black. I can move the cursor around but it does not light up. I suppose it is downloading as the light on my dsl modem is flashing. I will just leave it be for awhile???

---

### Post by treblemaker48 on 2011-03-19
I don't know if I should start a new thread or not but I have an annoying issue with my good computer. I keep getting a window asking for my login keyring password. It does not recognise any of the passwords i enter. I have to click cancel several times and then I can use the system. What do I do about this?

Thanks again
David

---

### Post by treblemaker48 on 2011-03-19
Hello, Well the machine seems to be done downloading as the modem light is not longer flashing. The screen is blank except for a cursor that I can move around. Should I force a shut down? Nothing seems to be happening. The drive light is not active and I get not response from keyboard or mouse.

---

### Post by Rubi1200 on 2011-03-19
First, do not do a hard shutdown:

do this instead;
Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted. REISUO will do a shutdown rather than a restart.

For the graphics, see here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by treblemaker48 on 2011-03-19
Hello,
I have made progress but I still end up at a screen with nothing on it but a cursor with nothing to click on. My nifty useless screen has the changing cosmic images on it but...

Do I have to do as suggested every time? That is hold shift when starting up. I started in safe mode last time and was able to get online to download updated. I even viewed a web page.

What should I do now?

Thank you
David

---

### Post by treblemaker48 on 2011-03-19
I did as suggested and the machine restarted but I am still at the useless screen. I am trying to sort out what the graphics stuff means to me. It worked in safe mode... everything was there.... but starting in regular mode I get useless screen.:confused:

---

### Post by treblemaker48 on 2011-03-19
Hello
well I got it working but in safe mode. I am currently streaming my favorite jazz radio and all seems well. However, I thought you could not get online in safe mode. Should I just use the thing in safe mode always or keep trying to get it right?

Thanks again
David

---

### Post by treblemaker48 on 2011-03-19
My rule is... if it works don't fix it. I am not going to install any graphics drivers because it all works in safe mode. I have a screen which shows images of the planets and such. That works and changes to new images so... 

I guess I just start in safe mode.

Please let me know if you have more suggestions. thanks for all your help
David

---

