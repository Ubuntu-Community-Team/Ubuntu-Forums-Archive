---
title: "Dual boot vista-ubuntu, can't boot ubuntu"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by se_landy on 2008-09-25
So here is the problem: 6 months ago I had only XP on my laptop. Than I installed ubuntu. Dual boot worked great. 5 days ago, I installed vista, and now i can't boot ubuntu... When i press the power button, vista boot automatically. there is no grub that would ask me which OS do I want to boot...:(
I could reinstall ubuntu, but I have some files in my old Ubuntu there that I would want to save...
Any ideas how to work this out and to save my data without reinstalling vista or ubuntu???

---

### Post by Partyboi2 on 2008-09-25
When you installed vista it would have written to the mbr. You should be able to restore grub using a ubuntu live cd. See [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by kspncr on 2008-09-25
When you installed Vista, it definitely wrote over GRUB. It seems you have already been pointed in the right direction, but personally, I find it easier to use the [SuperGrubDisk]("http://www.supergrubdisk.org/")

---

