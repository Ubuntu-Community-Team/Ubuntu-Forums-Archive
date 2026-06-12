---
title: "Ubuntu 10.04.1 on Compaq EVO N610c Fails"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by pr0xyius on 2010-11-18
Hello world!

I'm having a problem with installing ubuntu 10.10 and even 10.04.1 on my Compaq EVO n610c when i put my DVD (4,7gb) it does read it but it doesn't install and goes back to my windows XP, when i do it on the USB it does the same thing.. i cant get it to work and i changed in the bios the thing that you can choice wich thing first boots but i dont see USB either im desprerred now need some help!

(sorry for my bad english, I'm Dutch )

Ty for advice

---

### Post by sikander3786 on 2010-11-18
Hi and Welcome to the Forums :-)

How were the DVDs prepared? I hope you did the proper burn image to disc thing?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And regarding USB, how was the USB drive prepared?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Sometimes USB drives pop-in under the Hard Disk menu in Bios and you need to set priority there.

Or alternatively, there might be a shortcut key to boot menu. You might see an informative label when your computer is showing the Bios logo screen. Sometimes it is F12.

---

### Post by pr0xyius on 2010-11-19
> **sikander3786 said:**
> Hi and Welcome to the Forums :-)

How were the DVDs prepared? I hope you did the proper burn image to disc thing?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

And regarding USB, how was the USB drive prepared?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Sometimes USB drives pop-in under the Hard Disk menu in Bios and you need to set priority there.

Or alternatively, there might be a shortcut key to boot menu. You might see an informative label when your computer is showing the Bios logo screen. Sometimes it is F12.

I had do all the things you said but i doesn't work is it not compatble with my laptop need i get an older version?

---

### Post by sikander3786 on 2010-11-19
> **pr0xyius said:**
> I had do all the things you said but i doesn't work is it not compatble with my laptop need i get an older version?
Compatibility should not be an issue here.

And even if it is not compatible, your laptop should at least boot from the DVD/USB and then throw some error.

I still doubt about the preparation of discs and USB.

And also make sure you have selected proper boot device from Bios menu.

Did you check the disc for defects?

---

### Post by pr0xyius on 2010-11-19
> **sikander3786 said:**
> Compatibility should not be an issue here.

And even if it is not compatible, your laptop should at least boot from the DVD/USB and then throw some error.

I still doubt about the preparation of discs and USB.

And also make sure you have selected proper boot device from Bios menu.

Did you check the disc for defects?

uhm no not disc defects and i gonna look it through than...
but the thing is he sees it.. than is see a MAC adress and you see some white stripe is turning around and than an error says PXE no read or something and wich os is better Ubuntu 10.10 or 10.04?

---

### Post by sikander3786 on 2010-11-19
> than is see a MAC adress and you see some white stripe is turning around and than an error says PXE no read or something and 

Then it is definitely a Bios boot problem. The boot device is not configured properly there or the installation media is not bootable.

Burn a new disc or usb and let us know how you burnt that.

Regarding 10.04 and 10.10, 10.04 is a Long Term Support release. It would be supported for 3 years on the dekstop and 5 years on server.

10.10 will be supported for next 18 months.

If your machine is intended for some type of production purposes, go for the LTS.

And if it is just for fun, you'll find the latest version of software in 10.10.

However there have been more issues with 10.10 than with 10.04. Search the forums for that.

And personally, I am using both 10.04 and 10.10 and am more satisfied with 10.04.

If you can manage to test both the releases from Live CDs, you can test your hardware with both of them and then choose the one that better suits you.

---

### Post by pr0xyius on 2010-11-19
> **sikander3786 said:**
> Then it is definitely a Bios boot problem. The boot device is not configured properly there or the installation media is not bootable.

Burn a new disc or usb and let us know how you burnt that.

Regarding 10.04 and 10.10, 10.04 is a Long Term Support release. It would be supported for 3 years on the dekstop and 5 years on server.

10.10 will be supported for next 18 months.

If your machine is intended for some type of production purposes, go for the LTS.

And if it is just for fun, you'll find the latest version of software in 10.10.

However there have been more issues with 10.10 than with 10.04. Search the forums for that.

And personally, I am using both 10.04 and 10.10 and am more satisfied with 10.04.

If you can manage to test both the releases from Live CDs, you can test your hardware with both of them and then choose the one that better suits you.

I love you <3 no homo... :D it worked yay :) i installed it on a CD instead of a DVD it's loading right now im further so i think it works hahah! 

thank you verry much :D!
windows can be flushed trough the toilet hihi :KS

---

### Post by sikander3786 on 2010-11-19
You are Welcome. Glad to know you got it working :-)

Feel free to post any new queries.

For the moment, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of page.

And another advise, there is a known bug in 10.10's installer. If you are going to install 10.10, make sure your username (asked during Ubuntu installer) contains no Uppercase Letter or invalid characters or you might get stuck at the installation screen.

Happy Ubuntu-ing!

---

### Post by pr0xyius on 2010-11-19
> **sikander3786 said:**
> You are Welcome. Glad to know you got it working :-)

Feel free to post any new queries.

For the moment, you can mark this thread Solved using **[COLOR=Red]Thread Tools[/COLOR]** near the top of page.

And another advise, there is a known bug in 10.10's installer. If you are going to install 10.10, make sure your username (asked during Ubuntu installer) contains no Uppercase Letter or invalid characters or you might get stuck at the installation screen.

Happy Ubuntu-ing!

Thank you and I will do it :)

---

