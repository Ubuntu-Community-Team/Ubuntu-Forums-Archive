---
title: "Boot-repair not working!"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by Alaiyo on 2013-01-10
I ran a bunch of recommended updates on my Toshiba Satellite C655 earlier today. Thereafter I could not boot my computer at all. It's a dual installation, and I can't boot either Ubuntu 12.04 or Linux Mint 11 Katya. I decided to try a fresh install, tried booting each system from the live CDs, and that failed. I just burned and tried to boot from the Boot-Repair GUI from YannBuntu at [http://ubuntuforums.org/showthread.p...7#post10871917](http://ubuntuforums.org/showthread.p...7#post10871917), what I got what the following error message at startup:
 
[FONT=Courier New]EDD: Error 0400 reading sector 172696[/FONT]
[FONT=Courier New]No DEFAULT or UI configuration directive found![/FONT]
[FONT=Courier New]boot:[/FONT]

 
The grub is apparently so messed up that I can't boot from anywhere, including the grub> prompt after following the step-by-step instructions in the Ubuntu documentation section. My paths are (hd0, 11). I also tried booting from recovery mode (doesn't work properly), failsafe mode (not installed), nothing has worked. Again, I cannot get in anywhere in order to reach sudo, only grub>. And I can't boot from any live CD, including the Boot-Repair GUI.  I've been searching the forums all day.  Really screwed here...
 
[SIZE=3]*What to do??*[/SIZE] 
:-({|=

---

### Post by oldfred on 2013-01-11
That seems more like a bad write or download as if system cannot read a sector.

Check that you have a good download with md5sum and if using a DVD burn at the slowest speed you can.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

