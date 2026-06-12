---
title: "Booting from live memory stick can't go past &quot;Try Ubuntu&quot;"
date: 2017-03-09
forum: Installation &amp; Upgrades
---

### Post by zurga on 2017-03-09
My Kit: Dell Inspiron
Preloaded by Dell with Ubuntu 14
Now attempting to upgrade to Ubuntu 16

I have made up a live USB stick with Ubuntu 16. The integrity of the ISO file was verified with SHA256 sumcheck, and I have used the stick on my other laptops with no problem.

When I try to boot my Dell from the above memory stick, the booting options recognises the USB by name, and goes as far as the screen which gives options for either trying Ubuntu or installing it. I select "Try", and after a few seconds the screen goes off and essentially everything dies, except that the HDD will go on spinning. (I know that because I have to hold the OFF button for several seconds to force it off).
It could be that Dell have set up a fiendish trap to prevent the consumer from changing the op system, or there is some incompatibility between the stick and the PC.

To upgrade to Ubuntu 16 is obviously the right thing to do, but additionally I am not convinced that the Dell installed system works correctly, with the Firefox being extremely slow to respond to clicks.
I would be grateful for any advice that enables me to move on, as otherwise this PC which is still under warranty has to be junked. I have of course called Dell about this, but they seem completely unable to comprehend the problem e.g., they point me to online help for upgrading from Windows 8 to Windows 10!

---

### Post by ajgreeny on 2017-03-09
Hardware?
Dell Inspiron tells us very little about the hardware in use, in particular the graphic card, so from your Ubuntu 14.o4 show us the output of ```
lspci | grep VGA
```
I suspect you may have an nvidia graphic card and therefore need to use the nomodeset boot option.
See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by zurga on 2017-03-09
[COLOR=#000000][FONT=Calibri]Thanks, ajgreeny, for your reply. VGA info as follows. I shall also follow up the help link you have given.

$ lspci | grep VGA[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]00:02.0 VGA compatible controller: Intel Corporation Device 22b1 (rev 21)[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-03-10
Hhhmmmmm!
So it is an Intel integrated graphics which usually work faultlessly in the Ubuntu systems.

What is the rest of your hardware?
PLease show us the output of ```
sudo lshw -short
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by zurga on 2017-03-10
The output from lshw is attached.[ATTACH]274073[/ATTACH]

Additional information: I tried a live USB of Kubuntu 14, and it all seemed fine, but Kubuntu 16 fails similar to ubuntu 16. 

The Live USB has two set of options to select from:[INDENT]LEGACY OPTIONS:[/INDENT]
[INDENT=2]Hard Drive
USB Storage Device[/INDENT]
[INDENT]UEFI Options:[/INDENT]
[INDENT=2]Ubuntu
USB1 - UEFI OS (Recognisable USB Label)[/INDENT]

Having tried Ubuntu and Kubuntu version 14 & 16, I conclude that dichotomy lise between 14 and 16, rather than Ubuntu and Kubuntu.
I would be grateful for any kind of response that helps to close this question, even if the problem cannot be fixed.

Thanks

---

