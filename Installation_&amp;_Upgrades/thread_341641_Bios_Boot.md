---
title: "Bios Boot"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by BillZog on 2007-01-18
First attempt to dual boot XP and Ubuntu on 2 SATA Drives, one each, gave me a Grub menu that would boot Windows and not Ubuntu. The second attempt gave me a Grub menu that would boot Ubuntu but not Windows, in fact Ubuntu overwrote the MBR of the Windows drive and somehow the Windows partition was zapped in the process.

This time, my first step  was to disconnect the HDD meant for Ubuntu then reinstall WindowsXP and all necessary programs and all is working well so far.

My next step will be to disconnect the Windows drive and get the Ubuntu disk working like I want it.

The final step, I hope, will be to reconnect both drives and boot both through the Bios. Yeah, I'll have to hit the Delete key and change the boot order of the drives every time I want to change Operating Systems, but it seems safer, at least for the time being. Later, probably much later, I can work on dual booting via Grub or NTLDR. 

Question: Is this &#8220;BIOS Boot&#8221; working okay for others? Is there any chance, even under this setup, that one or the other Operating System is going to try to reach over and toy with the MBR of the other disk? 

I really liked the couple of days I had to work with and explore the Ubuntu environment, but right now cannot do without several of the Windows based programs and related data files and don't want to risk another disaster to try it.

BZ

---

