---
title: "Yoga 730 Install"
date: 2019-09-19
forum: Installation &amp; Upgrades
---

### Post by coreyaw1 on 2019-09-19
[COLOR=#494949][FONT=&quot]I need to be able to dual boot Ubuntu and Windows on my machine. I understand (from what I've seen on the web) that the reason I can't install Ubuntu on my Yoga 730 is that it's drive controller is set to RST instead of AHCI. I tried switching in in the BIOS but than Windows wouldn't boot. I tried the solution linked to here:[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot] [/FONT][/COLOR]
[COLOR=#494949][FONT=&quot][http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-opera...]("http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/")[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot] [/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]But bcdedit doesn't recognize the command. So I'm a little stumped here. Anyone else done this?[/FONT][/COLOR]

---

### Post by oldfred on 2019-09-19
Never done it, but some links:

       Windows AHCI instructions
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
[https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html](https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html)

---

### Post by coreyaw1 on 2019-09-19
So...I missed part 3 A on the link I sent.

[COLOR=#373737][FONT=&quot]"Type this command and press ENTER: [/FONT][/COLOR]**bcdedit /set {current} safeboot minimal**[COLOR=#373737][FONT=&quot][/FONT][/COLOR]
[LIST=1]
[*]**If this command does not work for you, try [B]bcdedit /set safeboot minimal"**[/B]
[/LIST]
[FONT=inherit]****Once that was done I was able to get it to boot into safe mode and get Windows to boot in ahci. From there the install of Ubuntu was exactly as you would expect it is. Typing this there right now.
[/FONT]

---

