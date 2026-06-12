---
title: "Ubuntu not booting from USB"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by tantocibo on 2013-07-02
Hi,
I have an Asus A55DR-SX138H (UEFI bios, AMD x64 CPU), with secure boot disabled in the bios settings. However, I'm not able to boot Ubuntu from USB stick: Grub succesfully loads but then, if I select 'Try' or 'Install' I always get a black screen. I tried both Ubuntu 12.04 and 13.04 AMD x64 images, all installed with Universal USB Installer 1.9.3.6. Thanks in advance.

---

### Post by sudodus on 2013-07-02
We don't know yet, if it is a problem with graphics or a general problem with booting.

- What graphics chip/card is it? You can try some boot option, start with ***nomodeset***

- Did you check with ***md5sum***, that the download of the Ubuntu iso file was successful?

- ***Cloning with dd*** has a high success rate making boot USB drives. So if you try that method, and it still does not work, there is some other problem.To make it safer, see[URL="http://ubuntuforums.org/showthread.php?t=1958073"] Howto make USB boot drives
[/URL]

---

### Post by Bucky Ball on 2013-07-02
> **sudodus said:**
> You can try some boot option, start with ***nomodeset***



How?

When you get to the Try or Install screen hit F6. You should have some options pop-up. Choose 'nomodset', as suggested.

Try that first.

---

### Post by oldfred on 2013-07-02
If booting install in UEFI mode to install in UEFI mode you cannot use f6, that is BIOS.
But you add nomodeset just like you do with first boot, by editing grub.
At grub menu, use e to edit, scroll down to linux line and replace quiet splash with nomodeset.

Screen shot here but as first boot with grub after install, but editing grub is the same.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by tantocibo on 2013-07-04
Thank you all, but nomodeset did not work for me...

---

### Post by sudodus on 2013-07-04
Please let us know about the graphics chip/card! This makes it easier for us the give advice.

And please continue to test some other boot options too (maybe more than one at a time).

*Edit*: You can enter the boot option text (just to find out if you come a prompt to enter user name and password) and you can remove the standard boot options quiet and splash. This would help finding if there are some specific problem (other than the graphics).

---

### Post by tantocibo on 2013-07-04
> **sudodus said:**
> Please let us know about the graphics chip/card! This makes it easier for us the give advice.

And please continue to test some other boot options too (maybe more than one at a time).

*Edit*: You can enter the boot option text (just to find out if you come a prompt to enter user name and password) and you can remove the standard boot options quiet and splash. This would help finding if there are some specific problem (other than the graphics).

Yes: AMD Radeon HD 7470M, you can gather it from the laptop model in the first post :)

---

### Post by sudodus on 2013-07-05
Some of the Radeon chips/cards are poorly supported by the built in drivers. In some (but not all) of those cases, there is a proprietary driver, that works better.

In this case you might succeed by booting in text mode: use the boot option 'text' (without quotes). And then in text mode, you can install the proprietary driver, like you install another program package in the newest version of Ubuntu. In older versions (I think 12.04 LTS) you can use jockey-text, or in some cases you download a deb package from the manufacturer's web-site and install it according to the instructions within that package. See these links

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[URL="https://help.ubuntu.com/community/RadeonDriver"]https://help.ubuntu.com/community/RadeonDriver
[/URL]

---

### Post by tantocibo on 2013-07-05
> **sudodus said:**
> Some of the Radeon chips/cards are poorly supported by the built in drivers. In some (but not all) of those cases, there is a proprietary driver, that works better.

In this case you might succeed by booting in text mode: use the boot option 'text' (without quotes). And then in text mode, you can install the proprietary driver, like you install another program package in the newest version of Ubuntu. In older versions (I think 12.04 LTS) you can use jockey-text, or in some cases you download a deb package from the manufacturer's web-site and install it according to the instructions within that package. See these links

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[URL="https://help.ubuntu.com/community/RadeonDriver"]https://help.ubuntu.com/community/RadeonDriver
[/URL]
I tried with both 'text' and 'nomodeset' options (together), with the same result. If I enable secure boot from bios , I get 'Binary is whitelisted' (I don't know if this can be useful for you). I also found the proprietary driver for my gpu, but how can I boot the live distro or install it with *that* driver?

---

### Post by sudodus on 2013-07-05
I still know too little about your problem to really help.

Please describe what you have done and what you get! What same result?

Did you try another method to make a boot USB drive (other than [COLOR=#000000]Universal USB Installer)?

Please try the USB drive in another computer!

I guess it is a new computer, so you have better chances to get working drivers with a new version of Ubuntu (13.04) or you might even test the not yet released version 13.10. It is still in alpha stage, and there will be a rough ride (with crashes) before it will be released in October, but you can try the daily build, and hope there will be working drivers for your computer. See this link

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

[/COLOR]

---

### Post by tantocibo on 2013-07-05
> **sudodus said:**
> I still know too little about your problem to really help.

Please describe what you have done and what you get! What same result?

Did you try another method to make a boot USB drive (other than [COLOR=#000000]Universal USB Installer)?

Please try the USB drive in another computer!

I guess it is a new computer, so you have better chances to get working drivers with a new version of Ubuntu (13.04) or you might even test the not yet released version 13.10. It is still in alpha stage, and there will be a rough ride (with crashes) before it will be released in October, but you can try the daily build, and hope there will be working drivers for your computer. See this link

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

[/COLOR]
**What I have done**: I booted from USB stick; on GRUB screen I hit the 'e' key and I edited the specific line adding 'text' and 'nomodeset' as boot options, and then I booted the live system by pressing 'F10' (CTRL+X does not work). I only tried the USB Universal Installer+Ubuntu 13.04 AMD6/12.04 AMD64 combination, because the other 'immediate' solution (LinuxLive USB Creator) does not support Ubuntu 13.04 (maybe I can try with the Ubuntu 12.04 image now...);

**What I get**: Black screen (see the first post... that is the 'same result');

The USB drive is tested on other computers.

---

### Post by DeathByDenim on 2013-07-05
Actually, I had the same problem with my new Acer laptop that I bought last month. The trick for me was to just use the "Increase brightness" key on your keyboard. Probably something like <Fn> + <F6> or <Fn> + <Arrow up> or something like that.

---

### Post by Bucky Ball on 2013-07-05
> **DeathByDenim said:**
> The trick for me was to just use the "Increase brightness" key on your keyboard.

How did you discover that? :-k ... but glad you did. Worth a try.

---

### Post by DeathByDenim on 2013-07-05
Heh, I stumbled upon it, while researching the linux compatibility for various laptops I was interested in.

---

### Post by sudodus on 2013-07-05
> **tantocibo said:**
> **What I have done**: I booted from USB stick; on GRUB screen I hit the 'e' key and I edited the specific line adding 'text' and 'nomodeset' as boot options, and then I booted the live system by pressing 'F10' (CTRL+X does not work). I only tried the USB Universal Installer+Ubuntu 13.04 AMD6/12.04 AMD64 combination, because the other 'immediate' solution (LinuxLive USB Creator) does not support Ubuntu 13.04 (maybe I can try with the Ubuntu 12.04 image now...);

**What I get**: Black screen (see the first post... that is the 'same result');

The USB drive is tested on other computers.

1. Try the tip by [COLOR=#000000]*DeathByDenim*.

2. If still no go
 
I understand that the USB drive works in (can boot) other computers

- Try to add the boot option text, and to remove the standard boot options quiet splash

- Select the recovery mode and try the different options in the menu[/COLOR]

---

### Post by tantocibo on 2013-07-06
> **sudodus said:**
> 1. Try the tip by [COLOR=#000000]*DeathByDenim*.

2. If still no go
 
I understand that the USB drive works in (can boot) other computers

- Try to add the boot option text, and to remove the standard boot options quiet splash

- Select the recovery mode and try the different options in the menu[/COLOR]
1. Did not work;
2. Did not work;
There isn't any recovery boot option on grub...Is it accesible in another way?

---

### Post by sudodus on 2013-07-06
Some of these new computers are made in such a way, that it should be hard or impossible to boot other operating systems than the one installed. The best thing for you would be if someone has succeeded with that brand and model, and shares her/his method to do it. Maybe you can find something on the internet browsing for linux dual boot and {the brand and model of your computer}.

---

### Post by Bucky Ball on 2013-07-06
Yes. I'd start investigating UEFI boots perhaps to see if that's the issue. That would prevent it booting.

Also, how many partitions are on the drive already?

---

### Post by slooksterpsv on 2013-07-06
For OS mode in your BIOS is it set to UEFI or do you have one that is like a UEFI/Custom/Legacy option - mine had a triple option which I selected that would do all 3. Otherwise, where the nomodeset didn't work, how did you make the USB via unetbootin? If so what version 583 failed miserably for me all the time. Finally 584 worked, but only in Windows.

Can you get to another TTY after you start having it boot via CTLR+ALT+F1 see if it gives you an error, or you can remove the quiet item in the grub area and see what's failing.

---

### Post by tantocibo on 2013-07-06
> **sudodus said:**
> Some of these new computers are made in such a way, that it should be hard or impossible to boot other operating systems than the one installed. The best thing for you would be if someone has succeeded with that brand and model, and shares her/his method to do it. Maybe you can find something on the internet browsing for linux dual boot and {the brand and model of your computer}.

Thank you **sudodus**! I found the solution on the official Italian Ubuntu forum (here is the translated page): [http://goo.gl/JBEoB](http://goo.gl/JBEoB). Hope this will help all ASUS A55DR users ;)

---

### Post by Bucky Ball on 2013-07-07
Good news. Please mark as solved to help others by following the link in my signature. Thanks.

---

### Post by sudodus on 2013-07-07
> **tantocibo said:**
> Thank you **sudodus**! I found the solution on the official Italian Ubuntu forum (here is the translated page): [http://goo.gl/JBEoB](http://goo.gl/JBEoB). Hope this will help all ASUS A55DR users ;)
I'm glad I could help you finding the solution :-)

---

