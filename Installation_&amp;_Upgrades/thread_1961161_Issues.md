---
title: "Issues???"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by Jdhunt3 on 2012-04-18
Ok so I will just start from the beginning.

I downloaded Ubuntu used poweriso to extract to a disc it wouldnt boot form disc and when using the "help me boot from disc" option i kept getting a "windowsbackend" error. 

I decided to use the windows image disc burner had another error wouldnt let it burn to disc.

I decided to run check disk on the hard drive had a couple errors that were fixed.

Ran windows image disc burner again got it onto the disc.

Still unable to boot from disc.

Attempted the help me boot from disc option again came up with same error.

Here is where I forget a step or something but I had an option to run inside windows. So I ran that and was able to get it into install.

I then rebooted selected ubuntu tried to boot in normal mode had an issue with my keyboard.

tried to boot in safe mode still had an issue with keyboard.

Selected the acpi boot mode? and it started and installed.

Once it rebooted i selected the normal mode got to a purple screen and it stayed there for about an hour. Couldnt get any response for reboot.

 finally reset computer and selected recovery mode. and had the same issue and now is where I am setting.  


I tried to show everyone every step I took so maybe i did something wrong.  If you need any more information please let me know I will try to give you what I can.

---

### Post by oldos2er on 2012-04-18
You don't extract the ISO file, you burn it as an image. See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Jdhunt3 on 2012-04-19
Yeah i figured that out I went back and figured out that my computer wasnt reading a DVD drive in the boot order changed that got it to recognize and attempt to boot from disc but now during boot it gets stuck on

generic-usb: probe of 0003:1038:0100.004 failed with error -22

not sure what it means but im guessing that is preventing it from going any further?

---

### Post by mastablasta on 2012-04-19
is the DVD drive connected to mashcine via USB?
 
after downloading the image did you check that the file is identical to the one on the server? :[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
after that you need to burn it propperly to a CD or DVD or you can use unetbootin or linuxliveUSB to "burn" it to USB key (htis is usefull if computer can boot form USB).
 
under no circumstances should you extract the ISO.
 
Also regarding your wubi install (inside windows) you said you had a keyboard issue. what kind of issue?

---

### Post by Jdhunt3 on 2012-04-19
mastablasta

It is an internal cd drive connected using sata.

I checked the files they are identical

I have gotten it to properly burn the files onto the disc using the windows burning tools

The issue was not with the keyboard but the usb port it was plugged into.

which is the same usb port that is giving the generic-usb: probe error i posted earlier

---

### Post by mastablasta on 2012-04-19
why do you think it would matter if USB is not working? it should still boot.
just as it boots with no keyboard or mouse or monitor attached.

---

### Post by Jdhunt3 on 2012-04-19
Because when it boots from cd it does all kinds of checks and when it gets to that usb port it gives that error and wont continue the boot. Is there a command to ignore that or does it need fixed first?  It is a port that is directly  attached to the Motherboard.

---

### Post by mastablasta on 2012-04-19
> **Jdhunt3 said:**
> Because when it boots from cd it does all kinds of checks and when it gets to that usb port it gives that error and wont continue the boot. Is there a command to ignore that or does it need fixed first?  It is a port that is directly  attached to the Motherboard.


except, when all is ok, you boot fom CD you shouldn't see those check. the plymouth splash screen should load (e.g Ubuntu with dots under it or whatever it is now)..

---

### Post by Jdhunt3 on 2012-04-19
It doesnt get that far with the boot from cd I get a black screen with what looks like basically a system check and it stops at that point I have never gotten it farther with the boot from cd.

---

