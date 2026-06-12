---
title: "ubuntu 11.04 does not boot on HP ProBook 4525s"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by vitalix on 2011-05-17
Hi everybody. I have a laptop HP ProBook 4525s. First when I got it I installed Ubunu 11.04 and it worked fine until I pressed a wifi disable/enable button. After this system just stoped. Then I tried to use my backup but it didn't help, system did't boot. So, I decided to boot from live CD Ubuntu 11.04 to install the new system but it also didn't boot, just stoped at Ubuntu purple picture screen. The same situation with USB drive.
Then I thied to install Ubuntu 10.10 and it worked well, so, I tried to upgrade it to 11.04. After all installation and cleaning were complete I rebooted my computer and got the some result as with live cd: system just stops booting at ubuntu purlpe screen and nothing happening.
Please help me solve it!

---

### Post by jerrrys on 2011-05-18
is this whats happening?
[http://ubuntuforums.org/showthread.php?t=1756110](http://ubuntuforums.org/showthread.php?t=1756110)

---

### Post by luberfly on 2011-06-20
IHi, I have a problem similar.
I'm unable to install the Ubuntu 11.04 on my HP Probook 4520s

It appear a black screen or the pink ubuntu screen and the pc seems stopped.

Ho I can install the Ubuntu 11.04 in my notebook?

Best Regards

Luca

---

### Post by foresthill on 2011-06-20
Try plugging in an external monitor during installation. 

If you can install that way, but still can't see the screen on your laptop, it might be the backlight not working. Shine a bright light on the screen and see if you can make out a very dim picture on the screen when the laptop is on and running (or trying to run) 11.04.

If it is the backlight, try the solution in post 5 of this thread:

[http://ubuntuforums.org/showthread.php?t=1781055&](http://ubuntuforums.org/showthread.php?t=1781055&)

---

### Post by dex1511 on 2011-06-20
i had a similar problem... i noticed that ubuntu would run at times, but otherwise it would just hang at the purple load screen with 5 dots...

however, even when connected to a power source it wouldnt run... im running a hp mini 110-3605tu. 

i noticed however, that ubuntu would load if the battery was at 100% (batt light at white, charging -orange)

dont know if this would solve your problem, but try using it after its charged completely...

---

### Post by Jocika1990 on 2011-06-26
> **vitalix said:**
> Hi everybody. I have a laptop HP ProBook 4525s. First when I got it I installed Ubunu 11.04 and it worked fine until I pressed a wifi disable/enable button. After this system just stoped. Then I tried to use my backup but it didn't help, system did't boot. So, I decided to boot from live CD Ubuntu 11.04 to install the new system but it also didn't boot, just stoped at Ubuntu purple picture screen. The same situation with USB drive.
Then I thied to install Ubuntu 10.10 and it worked well, so, I tried to upgrade it to 11.04. After all installation and cleaning were complete I rebooted my computer and got the some result as with live cd: system just stops booting at ubuntu purlpe screen and nothing happening.
Please help me solve it!

Have you solved the problem? I have the same on my hp 4525s :(

---

### Post by vitalix on 2011-06-26
Thanks all you guys. The problem was solved. I just disabled wi-fi in BIOS

---

### Post by updogliu on 2011-08-02
I have the same problem with my HP Probook 4525s. Unfortunately I have to use wifi. Hope somebody can help.

---

### Post by ybytyruzu on 2011-08-02
Hi, I have the same laptop and that problem was here too. If you have your Windows installed boot on it and turn on your WI-FI and then you will be able to boot on Ubuntu.

---

### Post by steve11911 on 2011-08-04
Please open a terminal and check the output of 
 lspci

If you have a Ralink wireless, the page linked below may lead to a resolution...

[http://askubuntu.com/questions/46004/hp-probook-4520s-drivers-problem](http://askubuntu.com/questions/46004/hp-probook-4520s-drivers-problem)

---

