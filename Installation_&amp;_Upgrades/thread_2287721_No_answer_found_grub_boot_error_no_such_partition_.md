---
title: "No answer found: grub boot error: no such partition and no BIOS options,"
date: 2015-07-21
forum: Installation &amp; Upgrades
---

### Post by Kieran_ on 2015-07-21
Hi all,    I have been search the internet for a few hours to no avail. I was an idiot and for whatever reason deleted the Ubuntu partitions I had on my computer.    I have a Lenovo ideapad z575 running Windows 7 with a dual boot Ubuntu 14.04 LTS I do believe. I did not ever use Ubuntu do to the complexity of it. As a result I was trying to get rid of this partition and return to only Windows 7. Luckily this is not my main computer so I am not panicking. However after a while of searching for an answer I have yet to find one. Every time I turn on the computer I get an error saying:   error: no such partition. Entering rescue mode... grub rescue>   Every single video or link I find online tells me to boot with my Windows 7 recovery disk, but doesn't tell me how.    I have a Windows 7 recovery disk (CD-R) and a Windows 10 recovery disk (CD-R). I put them in the disk drive (tried both) and turn on the computer and am greeted by the lovely error message every time. I tried holding and pushing F12 or Delete during the boot, I've tried pushing nothing, no response, no options, nothing.  If you know at all what I could do to just let my computer boot into Windows 7, that would be great. My whole goal is just to blow away the machine and start anew anyway, so if that's an option just let me know.    Thank you!

---

### Post by howefield on 2015-07-21
Do you have a "Novo" button somewhere around or near the power button, try pressing it to boot the Novo Button Menu from which you can choose to go into BIOS or select which device to boot from, amongst other options.

---

### Post by oldfred on 2015-07-21
You should restore Windows boot loader to MBR, if BIOS system. Most Windows 7 systems were BIOS.
If UEFI follow Howefield's suggestion and go into UEFI can choose to boot Windows in Boot tab.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Windows screenshots:
[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

            f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

