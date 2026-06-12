---
title: "unable to install karmic on dell 1464"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by lifetonjoyu on 2010-03-04
i m unable to install karmic on my dell inspiron1464 laptop...it has core i3 processor n 2 gb ram with windows7 already installed.....i had installed karmic on my pc n it didnt gave any prblm....but whn i m trying to installl it on my laptop it is just shoeing the try ubuntu n install ubuntu options....n wen i select the option to install it is shoeing blank screen n after sometime even the cd stops working n i hav to reboot again,,,,,, i want to install karmic on my laptop with dual boot option wit windows 7...... please tell me the way to install it....!!!!! 

will i hav to download the netbook version... cant i install from the desktop version of karmic......!!!!

---

### Post by stlsaint on 2010-03-04
If you laptop is a netbook i would suggest try using Ubuntu Netbook Remix or [UNR]("http://www.ubuntu.com/GetUbuntu/download-netbook").

---

### Post by manishmahabir on 2010-03-05
@lifetonjoy
hello friend!
if yoou have an onboard graphics ie intel hd,even lucid wont work...because this graphics card has been officially supported by intel only from the kernel version 2.6.33, while lucid ships with 2.6.32.

---

### Post by drrakesh on 2010-03-06
> **lifetonjoyu said:**
> i m unable to install karmic on my dell inspiron1464 laptop...it has core i3 processor n 2 gb ram with windows7 already installed.....i had installed karmic on my pc n it didnt gave any prblm....but whn i m trying to installl it on my laptop it is just shoeing the try ubuntu n install ubuntu options....n wen i select the option to install it is shoeing blank screen n after sometime even the cd stops working n i hav to reboot again,,,,,, i want to install karmic on my laptop with dual boot option wit windows 7...... please tell me the way to install it....!!!!! 

will i hav to download the netbook version... cant i install from the desktop version of karmic......!!!!
Hi Lifetonjoyu - I am running into the same issues while trying to install on a Dell inspiron 1464 machine, have tried installing the 64 bit version and the 32 bit  version of Karmic but run into i/o errors and a blank screen each time. Is it possible that a usb install will work instead? I am going to try that next!
 
Rakesh

---

### Post by noravanq on 2010-03-28
I got the same laptop. i3 processor, intel HD graphics. I didn't have blank CD's but had a ubuntu 8.10. 32 bit disk, so tried that and it installed just fine. I booted in to the liv cd and used the 7 step gui to install it. After installation everything worked except the screen looked just a tiny bit stretched. I installed the proprietry wifi driver, then upgraded to 9.04 and then to 9.10. Everything seemd to work fine. For example Hulu on hi-res in full screen was fine. 

The only problem was it froze for no apparent reason and was completely not rsponsive. I will wait for 10.04, unless I find the reason for the freezes and a solution.

---

### Post by noravanq on 2010-03-29
Today I tried to boot from a 9.10 Live on USB flash drive, but it wouldn't boot. I tried both 32bit and 64 bit versions. After I press on "Run Ubuntu without making any changes to your computer", a cursor blinks in the top left corner, then the LED backlight goes off and on, and nothing appears on the screen, it just stays black and nothing happens.

I tried 8.04 Live on USB and bot 32 and 64 bit versions worked. 

When 10.04 comes out, will it be possible to directly upgrade from 8.04 to 10.04, considering both are LTS, or will I have to go through 4 upgrades to get to 10.04?  When I had installed 8.10 earlier, it only gave me an option to upgrade to 9.04 and only then to 9.10.

Thanks.

---

### Post by Sef on 2010-03-29
> When 10.04 comes out, will it be possible to directly upgrade from 8.04  to 10.04, considering both are LTS, or will I have to go through 4  upgrades to get to 10.04?  When I had installed 8.10 earlier, it only  gave me an option to upgrade to 9.04 and only then to 9.10.

There will be an option to upgrade directly from Hardy, 8.04 to Lucid, 10.04.

---

### Post by noravanq on 2010-03-30
Thanks Sef.

---

### Post by FlynDice on 2010-04-04
I was getting random freezups with karmic on my Dell 1634 until I selected "none" under visual effects in Appearance Preferences.  Since I did that I've had no lockups at all.

---

### Post by lifetonjoyu on 2010-05-01
guise i talked to dell support centre.....dey told me tat core i3 processor does not support ubuntu n hence it wiil  not install in our machine .... lets jst hope tat 10.04 is supported on i3........

---

### Post by noravanq on 2010-05-03
I have successfully installed the 64 bit 10.04 on my Dell 1464, with Core-i3. So far everything has been working fine, with the exception of "Stand By" and microphone in skype.

---

