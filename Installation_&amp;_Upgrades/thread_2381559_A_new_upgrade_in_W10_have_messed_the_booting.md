---
title: "A new upgrade in W10 have messed the booting"
date: 2018-01-02
forum: Installation &amp; Upgrades
---

### Post by logonbe on 2018-01-02
Happy New Year to you all
 
 
 I'm quite new in using Ubuntu and my knowledge does not go quite beyond office and common programs.
 
 
 In my laptop it was installed Windows 8 and I updated it to W10. Later, I decided to try Ubuntu (16.04 LTS). When the computer always started, it did it with the option menu for choosing Ubuntu or Windows. Everything was fine until some day it was needed an update in Windows. After that, the menu didn't display anymore and it says that Windows has an irrecoverable error and that it needs to be repaired. The file is \hiberfil.sys, and the error code is 0xc0000225.
 
 
 Later I enterd the BIOS. There is no problem booting W10 directly if it's the first booting option in the BIOS. If I try to boot as always with Ubuntu, the option menu of OS will not show and the error will pop up again.
 
 
 Does anybody have a clue of what to do? I tried with some tutorials of recovering Windows with a USB with a ISO, but there is no problem with W10 (except that it messed the Ubuntu launching menu).


Here a pic of the problem:

 [ATTACH=CONFIG]277999[/ATTACH]

---

### Post by dav123456789 on 2018-01-02
looks like windows erased your bootloader and didn't included linux when it set up his one.
You should certainly take a read at Grub and try to see if he can solve your problem by re creating a correct bootload.
Sorry, english isn't my native language, i lack the word to be more precise, i'll add that i'm not a linux expert, maybe someone will help you more than me there.
Good luck,
Dav

---

### Post by oldfred on 2018-01-02
Windows is known to turn on fast start up or the always on hibernation with updates. So even if you turned off fast start up, it may be back on again.
Grub only boots working Windows, which means no hiberfile.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

[/URL] 

     May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by logonbe on 2018-01-04
Thank you for the response.
Dav, I'll read about Grub for a first comprehension of it.

Thanks for the links oldfred, I'll start right now to fix the booting. Maybe this afternoon I'll post again with the Boot-Info and, luckyly, the problem solved.

---

### Post by logonbe on 2018-01-05
Finally, my W10 started to go worse, so I erased everything and installed Ubuntu. Thank you all for the advice.

---

