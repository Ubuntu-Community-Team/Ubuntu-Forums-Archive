---
title: "Install 13.10 on HP ENVY Phoenix 810 from USB"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by robert_carroll2 on 2014-02-18
I am trying to install **Ubuntu 13.10 **on my new **HP Envy**.  My goal is to have **Ubuntu run as the main OS** and then run windows in virtualbox. 
 I chose 13.10 because I figured the latest edition will have the latest drivers and my box is new.  Please see the specs below:
 [INDENT]*[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03897788&cc=us&dlc=en&lc=en#N90](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03897788&cc=us&dlc=en&lc=en#N90)*[/INDENT]

The OS it came with is **windows 8.1**, so after reading about the **UEFI** and **secure boot **I am leaning toward secure boot being my issue, but I am not sure.  I have followed the instructions by [B]Louis Alverdo 
[/B][I][URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported"]
[/URL][/I][INDENT]*[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)*[/INDENT]

Here is what happens.  I insert my **live USB** with 13.10 on it, boot my computer and I get a screen that asks me do I want to test ubuntu, install it, check for errors etc.  The normal start of an install.

Next I click test without installing and I get a blank screen.  I try alt + f2, alt + enter, esc and I am not able to get anywhere.  The screens just stays blank.

Does anyone have any thoughts on what this might be?  If it is secure boot, any advice on how to get around / use it with 13.10 would be great. I thought maybe the nvidia driver too, but if I cant get to a command prompt I cant install the drivers.  The one thing I can do is get to grub.  Any advise would be much appreciated.  Thanks.

---

### Post by fdrake on 2014-02-18
probably need to aply the nomodeset option when booting your kernel . See here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by robert_carroll2 on 2014-02-18
I dont get that far though.  Here is where I got to.

[http://www.screencast.com/t/bQYqgfCMhk](http://www.screencast.com/t/bQYqgfCMhk)

After that, black screen.  no mode set isnt available in grub ... 

I have not ruled out that it could be the video cards.  I will try this in another machine, maybe I can apply the nomodeset option in my other box on this USB and see if that works.  I'll get back to you with the results.

Thanks.

---

### Post by fdrake on 2014-02-18
that's good . highlight "try ubntu" and press "e" and add this line to the console
replace "quiet splash&#8221; with &#8220;nomodeset" then press enter

---

### Post by jamesp2 on 2014-02-18
I had a similar problem. Try connecting a VGA Cable from laptop to TV/monitor.
Ubuntu started for me on the TV but not on my laptop screen

---

### Post by robert_carroll2 on 2014-02-19
> [COLOR=#000000]that's good . highlight "try ubntu" and press "e" and add this line to the console[/COLOR]
[COLOR=#000000]replace "quiet splash&#8221; with &#8220;nomodeset" then press enter[/COLOR]

Here is what I did.

[http://www.screencast.com/t/bQYqgfCMhk](http://www.screencast.com/t/bQYqgfCMhk)

I tried ctrl - x , it just printed an x, so I used f10 which worked and I was able to see some text scrolling by like it was booting (which is more than I have seen thus far), but then after a short period of time, it stopped.  Back to the black screen.  Thank you for any advice you can think of.  I do really appreciate your suggestions.

---

### Post by robert_carroll2 on 2014-05-29
I decided to wait for 14.04.  Maybe they would include drivers for my new computer in the new update ...  Unfortunately that wasnt the case, so I needed to find the issue and solve it.  Turns out it was my video card (GeForce GTX 760). I went to [http://www.geforce.com/drivers/results/73221](http://www.geforce.com/drivers/results/73221) and downloaded the driver and installed it.  From there it works fine, although I need to figure out how to tell the OS to look for this driver on startup.  Each time I need to boot into safe mode and it works fine.  

I am using an hdmi and dvi cables without an issue though.

---

