---
title: "Installing grub menu"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by wavemaker on 2011-06-07
Gooday all. I downloaded latest Ubuntu. Fired it up and went through normal installation procedure. After restarting I was not offered the option of getting into Ubuntu. I have 2 drives. 1 has win7 and the second drive I thought when I was installing,has mint and I gave mint and Ubuntu roughly equal amt of the disk.My question is can I use the update grub command from the live disk. If not what is my next step. Thanks.

---

### Post by garvinrick4 on 2011-06-07
> **wavemaker said:**
> Gooday all. I downloaded latest Ubuntu. Fired it up and went through normal installation procedure. After restarting I was not offered the option of getting into Ubuntu. I have 2 drives. 1 has win7 and the second drive I thought when I was installing,has mint and I gave mint and Ubuntu roughly equal amt of the disk.My question is can I use the update grub command from the live disk. If not what is my next step. Thanks.
Go into Bios and set the second drive with Linux to boot first in order and then while in ubuntu do a.
sudo update-grub
and will put all Operating systems in as Menuentrys and in config file:
#When you boot the first drive with Windows you only get Windows because you are booting from a Windows boot manager.
#When you boot from linux drive you will have grub2 as boot manager and everything as choice to boot into.

---

### Post by wavemaker on 2011-06-07
Thank you for your response garvinrick4. I did as you suggested, went to bios and changed the boot priority. Strange thing is looking it in bios those changes appear but when I reboot it comes back as having the old boot sequence. I have not shut the machine down completely, so that may be of interest. I will try that and report back. thanks again.

---

### Post by wavemaker on 2011-06-07
Yep, tried that and it doesn't just crank up at all. Just a white hyphen  -  flashing on and off in the top left hand corner of the monitor. Mate, I have to be getting to bed soon, big day at work tomorrow. Thank you very much for your input. James.

---

### Post by garvinrick4 on 2011-06-07
Put in a install Cd and use Try Ubuntu:
In upper right network manager applet get internet working:
Download this Script to DESKTOP and run with code below in a Terminal  ctrl/alt/t
Will put a text file called RESULTS on desktop. Copy and paste to this Thread:
It is a script telling all about your boot so we can repair, takes about 1 minute.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
  sudo bash ~/Desktop/boot_info_script.sh
```

---

