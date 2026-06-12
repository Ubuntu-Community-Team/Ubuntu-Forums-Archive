---
title: "Problem installing wubi"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by phampson on 2010-06-09
Ive tried to install ubuntu via wubi. When it boots and i select ubuntu it starts the final installation tasks. But halts with no rootfs defined and says i need to define one. However it wont continue to boot obviously so am unable to do so. My PC does have raid but its switched off in the bios. I know dual booting is one way to go but would prefer initially to have it in the file.

Any ideas. I can boot into the demo version and there is an install option there but doesnt offer my boot disk.

---

### Post by phampson on 2010-06-09
Bump

---

### Post by SlidingHorn on 2010-06-09
What version windows/ubuntu?  

> **ago said:**
> uninstall, run wubi again
after selecting ubuntu at reboot press esc and select the verbose mode.

When it fails look for logs in C:\ubuntu\

If they are not there, repeat the steps, and before rebooting after failure you should press ctrl+alt+f2 and run

sh /custom-installation/hooks/failure-command.sh

tons of this on google...haven't found a solved one yet though...here's another place to look

---

### Post by bcbc on 2010-06-09
See this [post]("http://swiss.ubuntuforums.org/showpost.php?p=8334643&postcount=4")

You'll need to boot a live CD to do it.

Caution: please use your own judgement on this - I can't verify that it works, or whether in fact this will help your situation.

---

### Post by phampson on 2010-06-10
Im on Windox XP Pro sp3 and trying the latest version of wubi / ubuntu 10.0.4. I have never used the disks in raid and the raid is definately disabled in the bios.

---

