---
title: "Cannot install ubuntu on HP Spectre X360"
date: 2018-11-28
forum: Installation &amp; Upgrades
---

### Post by openversus on 2018-11-28
I'm trying to install ubuntu on my new HP Spectre X360 but I cannot because I get this message (see attach) when I start installation from usb.
Can you help me?
Thank you

Stefano

---

### Post by jabrilm on 2018-12-06
Have you had any luck since you posted this? I am also having trouble installing on an HP Spectre x360, but getting different problems than you are. 

For your issue, you could try editing the grub settings and adding [FONT=courier new]acpi=off[/FONT].

So, I previously tried to install 18.04 and now just tried 18.10 and got the same error that you did. I was able to make that disappear by setting acpi=off in the grub settings. But now I am getting a different message, "Couldn't get size: Unknown error code"

I was able to solve all previous errors installing 18.04 by adding [FONT=courier new]noapic noacpi nosplash[/FONT] in place of [FONT=courier new]quiet splash[/FONT] in the grub boot settings. The touchpad and touchscreen are not working, but I was able to navigate the installation GUI using keys, and will try to get them working with the right drivers. Everything seems to be installing okay.

---

### Post by pranavganore on 2018-12-15
Hello, I recently got the new HP Spectre x360 Laptop (The new Diamond cut design 2019 model).
I was getting the same issue u mentioned above , was getting stuck at splash screen with dots.
So i tried your solution of setting [COLOR=#000000][FONT=&amp]noapic noacpi nosplash[/FONT][/COLOR][COLOR=#000000] in place of [/COLOR][COLOR=#000000][FONT=&amp]quiet splash[/FONT][/COLOR][COLOR=#000000] in the grub boot settings.
Things got ahead but at a point (as you can see in the attached screenshot), 
[/COLOR][ATTACH=CONFIG]281933[/ATTACH]
It keeps on checking for GPU : "A start job is running for detect the available GPUs and deal with any system changes" and  2of2"A start job is running for ubuntu Live CD installer"
after it runs for some time (few minutes), I get a [Failed] Failed to start Ubuntu Live CD installer messgae
but then the step 2of2 - the GPU check starts again. As you can see in next screenshot
[ATTACH=CONFIG]281934[/ATTACH]
I am not getting past this issue. What shoud I do ? anything you can think of ? @jabrilm or anyone ?

(My laptops Config :
Product Name : HP Spectre x360 Convertible 15-df0xxx
Product Number : 4CJ41AV

System BIOS: F.09
Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
16GB RAM
Intel(R) UHD Graphics 630
NVIDIA GeForce GTX 1050 Ti with Max-Q Design

(This laptop has a TPM chip as well))

---

### Post by wildmanne39 on 2018-12-15
Hello and welcome to the forum pranavganore, please start your own thread for support so you and the person that started this one can get the individual help you need.

Instead of posting images for terminal output please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks

---

### Post by jbamford92 on 2019-01-02
> **openversus said:**
> I'm trying to install ubuntu on my new HP Spectre X360 but I cannot because I get this message (see attach) when I start installation from usb.
Can you help me?
Thank you

Stefano


HP requires a special setup when it comes to the Grub Bootloader. How are you creating your USB Pen Drive? UEFI Booting or Legacy Booting?

---

### Post by jbamford92 on 2019-01-02
> **pranavganore said:**
> Hello, I recently got the new HP Spectre x360 Laptop (The new Diamond cut design 2019 model).
I was getting the same issue u mentioned above , was getting stuck at splash screen with dots.
So i tried your solution of setting [COLOR=#000000][FONT=&amp]noapic noacpi nosplash[/FONT][/COLOR][COLOR=#000000] in place of [/COLOR][COLOR=#000000][FONT=&amp]quiet splash[/FONT][/COLOR][COLOR=#000000] in the grub boot settings.
Things got ahead but at a point (as you can see in the attached screenshot), 
[/COLOR][ATTACH=CONFIG]281933[/ATTACH]
It keeps on checking for GPU : "A start job is running for detect the available GPUs and deal with any system changes" and  2of2"A start job is running for ubuntu Live CD installer"
after it runs for some time (few minutes), I get a [Failed] Failed to start Ubuntu Live CD installer messgae
but then the step 2of2 - the GPU check starts again. As you can see in next screenshot
[ATTACH=CONFIG]281934[/ATTACH]
I am not getting past this issue. What shoud I do ? anything you can think of ? @jabrilm or anyone ?

(My laptops Config :
Product Name : HP Spectre x360 Convertible 15-df0xxx
Product Number : 4CJ41AV

System BIOS: F.09
Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
16GB RAM
Intel(R) UHD Graphics 630
NVIDIA GeForce GTX 1050 Ti with Max-Q Design

(This laptop has a TPM chip as well))

Disable Swappable GPUs in the BIOS. Try installing with just IGPU instead of Dedicated Graphics until you get Ubuntu Installed.

---

