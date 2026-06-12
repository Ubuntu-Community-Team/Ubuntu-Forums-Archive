---
title: "USB Live install hangs at boot"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by RampantAndroid on 2012-05-18
Hi all,

I'm currently trying to experiment to see if I want to install Ubuntu on an SSD arriving today (I know I'll be installing CentOS too) and so I tried loading it onto a USB drive. I've used both unetbootin, and the live USB link found on the main page, and downloaded the latest 12.4 AMD64 ISO. On boot, I see the selection page to run Ubuntu, I see a ton of text go past to fast to read (but I don't think I saw any errors) and then I get to a purple load screen with a progress bar.

Now, while loading, my keyboard is powered and I can change my caps lock, num lock and such. Then I hear my sound card click on (ASUS Xonar Essence STX, it has a relay for its headphone amp that when the card powers up, makes an audible click) and then my mouse powers up. However, at this point, while I can move my cursor, I can no longer toggle my numlock/scroll/caps lock states which makes me think the system has hung.

Are there any places to find logs? How can I debug this?

I'm loading the system off a Corsair Flash Voyager GT drive. My system specs are:
Core i7 3770k (both OCed and stock settings prevent me from booting)
MSI Z77A-GD65 mainboard
16GB Corsair DDR3-1600 RAM
ASUS Xonar Essence STX PCIe soundcard
Intel LAN
Onboard sound card disabled

Could there be some BIOS setting causing this?

Thanks in advance!!

---

### Post by RampantAndroid on 2012-05-18
No one?

---

### Post by Quackers on 2012-05-18
Welcome to UF :-)
What graphics card?

Also did you check the md5sum of the downloaded iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by RampantAndroid on 2012-05-18
> **Quackers said:**
> Welcome to UF :-)
What graphics card?

Also did you check the md5sum of the downloaded iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

GTX580, with the intel HD4000 disabled. 

I believe I did check the MD5 on the ISO from the website. Just not the one from unetbootin. 

Thanks!

---

### Post by Quackers on 2012-05-19
When booting the live cd/usb are you getting to a desktop? 
Are the caps lock/numlk lights flashing at all?

Have you tried the nomodeset boot option?
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

