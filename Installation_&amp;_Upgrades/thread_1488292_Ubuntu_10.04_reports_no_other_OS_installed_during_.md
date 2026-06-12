---
title: "Ubuntu 10.04 reports no other OS installed during installation"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by rocknzen on 2010-05-19
I spent the last couple of hours reading different posts here and other sites but haven't been able to find a good enough answer.

I have Win7 Ultimate x64 installed on my main drive. I disconnected all other drives to keep the installation as straightforward as possible. I have installed Ubuntu 8.xx and 9.xx a number of times so I am comfortable installing single and dual boot setups.

What concerns me is that the Ubuntu 10.04 installation reports that there is no operating system installed at all.

I still see the slider to choose whatever size I want for the Ubuntu installation. When I boot to the live cd I can in fact access my files in the Windows partition.

What will happen if I continue with the installation? Is there a chance that my Windows installation will get fragged?

Will it just be a matter of getting Grub to recognize Win7?

Thanks for your answers in advance:)

---

### Post by rocknzen on 2010-05-20
Anyone? No suggestions?

---

### Post by rocknzen on 2010-05-22
Can I please get some advice on this? I just need to know if there's a chance that Windows will get fried.

---

### Post by recluce on 2010-05-22
I am probably not able to give *solid* advice on this, just some 2nd hand information and a vague idea. Some people had issues similar to yours during the alpha-test stages.

Some anecdotal solutions:

1.) Check for the SATA mode in your BIOS. I read reports that "Legacy" or "IDE Emulation" caused all kinds of weird issues with certain motherboards and the Ubuntu Installer, so try AHCI mode.

2.) Similar reports for certain motherboards running "Fake Raid", be sure this is disabled (should be, as you don't seem to be running a RAID anyway). 

2.) Try to install from the Alternate Install CD.

3.) Check if GParted on the Live CD is able to see your partitions. If it does, prepare the partitions manually (at least / and swap, preferably a separate /home) and just install Ubuntu into the root partition so prepared.

Wiping out Win 7: there is always a risk, so **do have a backup.** 

If you install automatically from the installer that does not see your OS, disaster seems likely. If you install according to 3.) above, nothing should happen, but GRUB2 might not have an entry for Windows. Just be sure NOT to install GRUB2 to all partitions, as the installer suggests.

---

### Post by efflandt on 2010-05-22
I am not familiar with the Sata or Raid issues.  But I would suggest backing up anything you do not want to lose, and then resize your Win7 partition using its own admin utilities.

Then either tell Ubuntu install to only use unallocated space, or manually configure partition(s).

---

