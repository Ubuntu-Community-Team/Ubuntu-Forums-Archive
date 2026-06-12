---
title: "Ubuntu 6.10 Splash screen error."
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by Dilox on 2007-01-22
Ok, Well First off id like to say Hi.

I'm a complete noob when it comes to Linux (all distros) it's my first time running one too.
When i install linux ubuntu 6.10 (not the live cd) it installs fine. When i start up ubuntu i get to the splash screen (The bit where it has the loading bar and the ubuntu logo on it) When it finishes loading the monitor turns its sell on stand by mode and gives me a error saying.

"Can not display this input signal"

I think it's because i am running a 6600LE and can not pick it up or something? Please tell me if im wrong.

Does any one know how to help me?

My Pc:
AMD Sempron 2800+ 2.3Ghz~
80Gb wester digital hard drive
250GB Maxtor Hard drive
Nvidia Ge-Force 6600LE
512mb 333mhz DDR Ram.

Thanks in advanced. 
Dylan  ](*,)  ](*,)  ](*,)

---

### Post by Dilox on 2007-01-22
O.k Well im guessing by the research ive done around the forums is that i need to change the x something file to load "vesa" drivers instead of what its trying to load.

Can some one please tell me a quick and easy way of changing this file?

Thanks.

Dylan ](*,)

---

### Post by Stemp on 2007-01-22
> I think it's because i am running a 6600LE and can not pick it up or something? Please tell me if im wrong.

I think you're right. There is something wrong in your Xorg configuration.
After the boot screen, press ctrl+alt+F1, then log in and try a :
```
sudo dpkg-reconfigure xserver-xorg
```

select the nvidia driver or if it's not working the vesa driver.

---

### Post by Dilox on 2007-01-22
Thanks mate. I am re-installing ubuntu now. I will update you with what happens
:D  
Dylan

---

### Post by Dilox on 2007-01-22
Ok...

I get into the command place but... It has about 100 lines like 3mm thick and you cant make out the writing at all.

Is there another method?

Dylan

---

### Post by Stemp on 2007-01-22
Can you read the last line ?

---

### Post by Dilox on 2007-01-22
It pretty much flashes real quick i see something like [login] then it just goes all wierd on me.

Ill try again.

Dylan

---

### Post by Dilox on 2007-01-22
Ok.

Linux tries to boot up. I press cntrl + alt + F1 it goes into the screen but linux is still booting causeing the screen to go wrong on me.

Is there any way to pause the start up? and just go staright into the command thing?

Dylan

---

### Post by Stemp on 2007-01-22
You may use the  (single-user mode) line in grub.
You will be sent directly to a root login (no need for sudo)

---

### Post by Dilox on 2007-01-22
As i type this i am running in ubuntu i got my network setup so i can run the net now :)

I had to start up ubuntu in recovery mode. Then i enterd the details you provided. Thank you so much :)

Now to find out how to get my gfx rolling :P

Dylan

P.s Thanks for your time and effort with a newb ;) :lolflag:

---

### Post by Stemp on 2007-01-22
Great !

Just search for nvidia on the forum and wiki, and you will find how to tweak your graphics setting ;)

---

