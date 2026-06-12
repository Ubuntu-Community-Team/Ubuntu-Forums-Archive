---
title: "Clean Wubi Removal"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by Tactical Fart on 2010-02-06
First, I tried wubi. It's AMAZING! However I wanted to try the netbook remix (because I'm on a netbook atm). So I uninstalled, and reinstalled with the netbook-remix iso... which totally failed and put me into grub while booting. 

"Oh well, that's fine, It worked okay using the normal iso. So I'll try to install over it." 

That also put me into grub. I can boot into windows no problem, but not ubuntu. I think I royally failed at something. What did I screw up this time?

P.S. Running wubi under Windows 7 Home Professional as the primary OS.

---

### Post by darkod on 2010-02-06
You have to be more specific. When you said you tried UNR was it also wubi install or full UNR install on its own partition?
If it was also wubi install, you seem to be affected by a bug in the wubildr file. Boot windows, and get the new wubildr file from here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Copy that file to C:, or if you selected to install wubi on D:, E: etc, copy it there. It will replace the current file. You should be OK after that.

If you did NOT install wubi but instead you installed full ubuntu, ignore the above, you don't need the wubildr file.

---

### Post by Tactical Fart on 2010-02-06
It was strictly wubi. I don't have a usb cdrom yet.

Also, I forgot to mention a certain symptom. When I ran the wubi install, in puts the files where they need to go, and then offers a reboot. I reboot. I boot to ubuntu, it finishes up. Then I have to reboot again (understandable). THEN grub glitches. Also I just tried the file you specified. I put it at the root of the partition, (filed) and in winboot (failed). Sorry for forgetting this.

---

### Post by darkod on 2010-02-06
Hmmm, that is the "most popular" wubi bug around. You only need to replace the wubildr with that new file, in the root of the partition where you installed wubi (C:, D:, E:, etc). If that didn't help, I'm lost, sorry. I never use wubi myself.
Just to make sure, did it ask you if you want to overwrite the wubildr file? You would have the old file there and if it didn't ask you that means it might be on another partition. You need to put it on exactly the same partition, you understand that.

---

### Post by OrangeCrate on 2010-02-06
> You uninstall it as any other applications. In Windows go to the control panel and select "Add or Remove Programs", then select Wubi/Ubuntu and uninstall it. You can also use the uninstaller that you find in the installation folder.

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by Tactical Fart on 2010-02-06
I'm an idiot. I put the file at the root of the partition that contains the installation, not the partition that I have wubi on. I put the file there, the heavens opened up, and an choir of angels sang out as I got past grub. You where right in your first post.

---

