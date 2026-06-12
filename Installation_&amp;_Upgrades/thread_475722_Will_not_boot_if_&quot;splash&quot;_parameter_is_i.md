---
title: "Will not boot if &quot;splash&quot; parameter is included..."
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2007-06-16
Hello everyone :-)

I've been thinking about it for very long, but know I've done it!!  The boot hard disk of my main rig crashed, and I decided that I will not install Windows again!  Instead I went full Ubuntu 7.04.  I knew from the beginning that I was going to face a lot of unknown territory, but I have a lot of patience, and most of all the absolute will to be totally free from windows.

I've been with Microsoft products since 1987 and I understand that this will not be easy :-)

Since I started installing I have faced a lot of different issues, but I am willing to overcome them, one by one.  I am going to start a new thread for each one, unless I find the answer in another thread of course.

So here goes the first one:

When I installed I could not boot.  I could see the first few messages, but then I got the message from my monitor "No signal", my monitor went into standby and nothing was happening.
After I played around with the boot parameters, I found out that if I exclude the "splash" after quiet on the first option of the grub, I could boot.

Does anyone know why?  Most importantly, does anyone know how I can configure my grab in such a way that it does not include the "splash" parameter each time.  Because everytime I want to boot, I have to edit the line, delete splash and then press enter and "b" in order to boot.

Does anyone have any other ideas or suggestions?

Thank you all in advance, I appreciate your taking the time to read and answer to my post :)

---

### Post by Ifaistos on 2007-06-16
bump

---

### Post by Ifaistos on 2007-06-17
bump

---

### Post by Ifaistos on 2007-06-24
bump

---

### Post by Ifaistos on 2007-06-29
bump

---

### Post by Ifaistos on 2007-07-08
bump

---

### Post by Gremlinzzz on 2007-07-08
I have found a program that sets up control of grub menu on/ system / Administration / startup-manager=lets me setup which system starts by default and alot of other things.heres screen shots and the site i downloaded it from.Deb package.
[http://linux.softpedia.com/progScree...hot-27320.html](http://linux.softpedia.com/progScree...hot-27320.html)
[http://linux.softpedia.com/get/Syste...er-27320.shtml](http://linux.softpedia.com/get/Syste...er-27320.shtml)

---

### Post by Gremlinzzz on 2007-07-08
[http://linux.softpedia.com/progScreenshots/SUM-Start-up-Manager-Screenshot-27320.html](http://linux.softpedia.com/progScreenshots/SUM-Start-up-Manager-Screenshot-27320.html)
[http://linux.softpedia.com/get/System/System-Administration/SUM-Start-up-Manager-27320.shtml](http://linux.softpedia.com/get/System/System-Administration/SUM-Start-up-Manager-27320.shtml)
not sure what happen on first paste but this one works

---

### Post by thomaswp on 2007-10-23
> **Gremlinzzz said:**
> [http://linux.softpedia.com/progScreenshots/SUM-Start-up-Manager-Screenshot-27320.html](http://linux.softpedia.com/progScreenshots/SUM-Start-up-Manager-Screenshot-27320.html)
[http://linux.softpedia.com/get/System/System-Administration/SUM-Start-up-Manager-27320.shtml](http://linux.softpedia.com/get/System/System-Administration/SUM-Start-up-Manager-27320.shtml)
not sure what happen on first paste but this one worksI have the exact same problem.  After upgrade to gutsy all worked fine but my broadcom wireless was not working.

After MUCH digging and frustration [I used this thread]("http://ubuntuforums.org/showthread.php?t=405990") to get the wirelss working.

Since then, the PC (DELL Inspiron 1300) hangs on boot (3.5 squares in).

If I take the "splash" parameter out of the boot line in grub everything works perfectly!

I am guessing it is related to the wireless card but am at a loss.

---

### Post by Diabolis on 2007-10-23
You can edit your grub file and erase the splash option. Since I don't like the splash I deleted it and also uninstalled **usplash**. This will get you to the file you need to modify:
```
sudo nano /boot/grub/menu.lst
```

---

### Post by thomaswp on 2007-10-24
Thanks, yes I have done that but I think the ubuntu splash screen is classy and don't like to see the guts when it is working.

But it seems that it is the splash screen interacting with the wifi that is breaking things at the moment.

---

### Post by Ifaistos on 2007-10-24
hm... I've never thought of that !!

My mind would never go to that direction.  However I do have a wifi internet card on my computer.
It would be really strange if the wifi is causing the problems.

Anyone??!!

---

### Post by WaterBreath on 2007-10-25
I have been having what appears to be the exact same problem, except I **don't** have a wireless card in my computer.  In fact, the only thing I seem to have in common with Ifaistos is that we both have 64-bit machines.  I even had this problem with the Live CD and installation.

I have edited the GRUB file to remove the splash option, but I would like to fix the problem, if there is a known solution.

Machine specs are in my signature.  Anyone have any idea what it might be?

---

### Post by Ifaistos on 2007-10-27
Well I have a couple of thoughts that I would like to share with anyone that is reading.

It seems to me that for some reason the "splash" option does NOT freeze the computer.
What I see is that my computer boots correctly but when it is time to display the splash picture it tries to change resolution or refresh rate or both.

Then I get the error : No signal from my monitor.  And then there is nothing I can do but to reboot.

So I believe that it has to do with the splash picture itself.  I wonder if there is a way to change the splash picture to a picture that we are sure that our monitors can display.  Maybe even better if we could specify the resolution and refresh of the splash screen, then we would be absolutely sure.

I thought I would share this with anyone that might want to help us.
Thanks in advance...

---

### Post by thomaswp on 2007-10-28
This seems related to the post below that was suggested by frodon as a cure for my woes.  It did not fix my problem but may help with  you...

[http://ubuntuforums.org/showthread.php?p=3617992](http://ubuntuforums.org/showthread.php?p=3617992)

---

### Post by thomaswp on 2008-02-21
I am bumping this because I still have the problem  No idea if it is the wifi.

Every time ubuntu updates I have to edit the grub menu.lst file and remove the "splash"  parameter.

It is particularly annoying since I have moved the machine over to Ubuntu fully and it seems that this problem always catches out my wife whilst I am at work.

Does anyone have any idea how to fix or even diagnose this?

---

