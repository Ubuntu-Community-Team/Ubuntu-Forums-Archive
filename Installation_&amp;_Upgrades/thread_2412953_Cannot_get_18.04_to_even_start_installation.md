---
title: "Cannot get 18.04 to even start installation"
date: 2019-02-19
forum: Installation &amp; Upgrades
---

### Post by mlapoint on 2019-02-19
I am trying to do a fresh install of Ubuntu 18.04 on my Desktop machine.  I have Ubuntu 16.04 installed on that machine now.  I downloaded Ubuntu 18.04.2 and put it on a USB stick and a DVD.  Both of those worked just fine.  I know this because one time I accidentally forgot to take my USB stick out of my Windows 10 laptop and reboot.  It loaded up Ubuntu 18.04.

So, on my Desktop, I changed the boot order to the USB stick first.  Then I save and it "starts", but it goes to a black screen and nothing else happens.  Even if I wait overnight.  Then I tried it with the DVD and the same thing happens.

I tried switching the HDD out for another one that does not have Ubuntu on it and same thing happens.  I am at my wits end with this upgrade.  My 16.04 has stopped updating because of an error so I just thought I'd start all over and hopefully it will work again.  16.04 has worked flawlessly for several years.  I basically use it for Emby media server.

My desktop machine:
ASUS M Series M51AC
Core i7 4770 3.4 GHz
16 GB Ram
1 TB HDD

Thank You,
Mike LaPointe

---

### Post by vidtek on 2019-02-19
> **mlapoint said:**
> I am trying to do a fresh install of Ubuntu 18.04 on my Desktop machine.  I have Ubuntu 16.04 installed on that machine now.  I downloaded Ubuntu 18.04.2 and put it on a USB stick and a DVD.  Both of those worked just fine.  I know this because one time I accidentally forgot to take my USB stick out of my Windows 10 laptop and reboot.  It loaded up Ubuntu 18.04.

So, on my Desktop, I changed the boot order to the USB stick first.  Then I save and it "starts", but it goes to a black screen and nothing else happens.  Even if I wait overnight.  Then I tried it with the DVD and the same thing happens.

I tried switching the HDD out for another one that does not have Ubuntu on it and same thing happens.  I am at my wits end with this upgrade.  My 16.04 has stopped updating because of an error so I just thought I'd start all over and hopefully it will work again.  16.04 has worked flawlessly for several years.  I basically use it for Emby media server.

My desktop machine:
ASUS M Series M51AC
Core i7 4770 3.4 GHz
16 GB Ram
1 TB HDD





Thank You,
Mike LaPointe


Mike-  when the machine starts to boot and goes to the grub screen, go to advanced options and insert "nomodeset" in place of "quiet splash" (minus quotes) in the editable options.  Then you can see at which point it stops and go from there.
If you don't see an initial grub screen, try hitting the F12 or F8 keys after power on.

Cheers Tony.

---

