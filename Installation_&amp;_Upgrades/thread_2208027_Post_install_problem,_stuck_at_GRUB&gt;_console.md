---
title: "Post install problem, stuck at GRUB&gt; console"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by sega2 on 2014-02-26
Hello here is my system, Currently running on windows 8.1 

[http://puu.sh/7b8wA.png](http://puu.sh/7b8wA.png)
[http://puu.sh/7b8xp.png](http://puu.sh/7b8xp.png)

Created new partition -> installed ubuntu on there (When installing the Ubuntu, I cannot see any options that has "... install along Windows 8". I can only see option to erase the disk which is I dont want), and done. After computer restarts, my pc does not detect Ubuntu, and it proceed to windows 8.1. So I use EasyBCD, and I added the Ubuntu there 

[http://puu.sh/7b8E8.png](http://puu.sh/7b8E8.png)

Reboot my pc, and voila I can see Ubuntu there below my Windows 8.1 selection. But after I choose the "Ubuntu", it takes me to a big black screen with GRUB> console there. I dont know what am I supposed to do with this except type "reboot" and enter 

Anyone can help me if I missed something??

[IMG]http://i.imgur.com/9E03shN.jpg[/IMG]

---

### Post by sega2 on 2014-02-26
I've also tried to change my EasyBCD into partition 5, where I installed my Ubuntu
[http://puu.sh/7b8Mr.png](http://puu.sh/7b8Mr.png)

Though I still see that black screen grub console!

---

### Post by tomrlopes on 2014-02-27
Try booting to Ubuntu from the Motherboard boot menu.  On your motherboard the boot choice screen is F11.  

Or go into the Uefi setup (Del or F2) and choose Ubuntu as the default OS.  

If your machine boots too fast to enter Uefi bios then try this from windows 8:  


[LIST=1]
[*]Press the **Windows ([IMG]http://panam.acer.com/acerpanam/images/icon_Windows8_key.png[/IMG]) key** + **C**, or swipe in from the right edge of the screen to open your Charms.
[*]Click **Settings**.
[*]Click **Change PC Settings**.
[*]In PC Settings, select **General**.
[*]Under Advanced startup, click **Restart now**. The system will restart and show the Windows 8 boot menu.
[*]In the boot menu, select **Troubleshoot**.
[*]In the Troubleshoot menu, select **Advanced options**.
[*]In the Advanced options menu, select **UEFI Firmware Settings**.
[*]Click **Restart** to restart the system and enter UEFI (BIOS).
[/LIST]

From here: [http://acer--uk.custhelp.com/app/answers/detail/a_id/27102/~/accessing-the-uefi-%28bios%29-setup-on-a-windows-8-system](http://acer--uk.custhelp.com/app/answers/detail/a_id/27102/~/accessing-the-uefi-%28bios%29-setup-on-a-windows-8-system)

---

