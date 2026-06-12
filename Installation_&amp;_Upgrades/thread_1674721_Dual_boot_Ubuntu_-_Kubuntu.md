---
title: "Dual boot: Ubuntu - Kubuntu"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by SquareRunner on 2011-01-24
Hey forum,

Got a little bit of an issue here.  I am running Ubuntu 10.10 and just yesterday installed Kubuntu 10.10 on an external drive.  Now it takes over 2 minutes to boot up (from a previous 15 seconds), I am only able to run one OS a power on can only run the other OS (starting from either) after I shut the computer down.  If I just reset the computer it says that the drive I am looking for cannot be found.  

In Grub2 both OSs show up as Ubuntu, but the actual Ubuntu seems to cycle through the HDs it says it's running from at the end of the title in Grub.  Also, I cannot edit Grub2, which is the Grub I'm running on both OSs.  For example, I tried editing the default startup OS and it just didn't take the change in either Terminal or Startup Manager.

Is there something I'm missing?  I really don't want to have to do a clean install.

Also, if I unplug the external drive my computer is directed to the grub command line.

---

### Post by sikander3786 on 2011-01-24
Lets find out more about your setup. Boot either Ubuntu or Kubuntu and run and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us about the location of Grub. Where it is installed and which boot device you need to configure as your first boot device in Bios menu.

Each time you make a change to any of Grub configuration files, you need to run *sudo update-grub* for the changes to take effect. Anyhow, I would recommend doing that without seeing your boot script output.

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

