---
title: "unable to boot ubuntu, getting &quot;grub&gt;&quot; prompt on boot screen"
date: 2013-01-22
forum: Installation &amp; Upgrades
---

### Post by apancholi on 2013-01-22
I am trying to Triple-Boot w/ Mountain Lion10.8.2, Ubuntu and Windows7. 
System Configuration is - 

[LIST]
[*][COLOR=#000000][FONT=Arial]Intel(R) Core(TM) i3 processor.[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Motherboard: Intel chipset with AHCI enabled.[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]4GB of memory.[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]500 GB of internal hard disk space attached to Intel SATA controller running in AHCI mode.[/FONT][/COLOR]
[/LIST]
We have made three partitioned, two 100-100 GB partitioned for MAC and Linux and 300 GB partitioned for Windows. 

We have successfully installed MAC OS X and Window 7.  

On windows we have downloaded the latest wubi.exe and follow the steps mentioned in [guide ]("https://wiki.ubuntu.com/WubiGuide"). After latest Ubuntu has been downloaded and it has been extracted successfully, it asked to re-start the system.

Once we restarted the system, on boot screen, we are getting only "grub>" prompt. We pressed TAB and see options. Tried different options like - "Boot", "configfile", "linux", "continue" but it asked for file-name. What file-name we need to specified?  

We have installed Linux on D:/ partition where we can see Ubuntu folder. What we need to type after "grub>" prompt on boot screen? Do we need to specified any file name located in D drive?

---

### Post by oldfred on 2013-01-23
Welcome to the forums. Is this a Mac as we cannot support any violation of Apples TOS.

But wubi does not work on gpt partitioned drives. Not sure if it with Windows on a Mac the hybrid MBR will support wubi or not in the Windows MBR portion.

---

