---
title: "Recovered Vista. Grub gone. =("
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by noveus on 2010-05-14
I Dual-Booted (if im not mistaken is the term for installing two OS) Ubuntu 9.10 and Windows Vista. Using Ubuntu 9.10 as my primary OS and using Vista for some programming ( college stuffs )

Only a moment ago, i reformat/recovered my Vista and only i found out that, my GRUB loader has gone. I'm asking is there any way for me to install a GRUB loader using Vista?

Thanks,
Yeong Ren

---

### Post by conradin on 2010-05-14
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I see this is in the wubi section. Its likely you never had an actual linux partition. Wubi installs a folder that is then dedicated to the linux OS. Look at your disk manager to verify if you have all your disk space accounted for.
 Then look in the C drive for the wubi installation.

Im not certain wubi installs grub anyway. You could probably add a boot path to the Ms boot loader with msconfig.

---

### Post by noveus on 2010-05-14
I do not have a Blank DVD for me to burn right now. Is there any settings that can be done through Vista?

---

### Post by noveus on 2010-05-14
Tried msconfig. Doesnt help.

---

### Post by darkod on 2010-05-14
If you installed wubi, do not do the procedure for reinstalling grub2 to the MBR. You never had grub2.
During installation wubi adds entry into the windows bootloader. With recovering vista, you got the original bootloader back.

If you are sure wubi is still there, we just have to figure out to add it to the bootloader again. I never tried that, so I don't know right now.

I'll see if I can find something. Try Google too, what you want is instructions to add an OS to the bootloader using the bcdedit.exe, because for vista you need to use that file/command. Only I don't know which parameters you need to give it.

---

### Post by noveus on 2010-05-14
OKay thanks, i will give a try.

---

### Post by darkod on 2010-05-14
Look towards the end of the first post here:
[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

That is for win7 but it's the same for vista. According to the example of 4 commands how to add entry for XP residing on F: partition, the conclusion would be (replace the F: with the partition letter where you installed wubi):

1. Start administrator command prompt. Click on Start-Accessories, right-click Command Prompt and select Run as Administrator. You have to do this with admin privilegies.

2. According to the above example the commands would be:

bcdedit /create {wubi} /d "Wubi Ubuntu 10.04"
bcdedit /set {wubi} device partition=F:
bcdedit /set {wubi} path \wubildr
bcdedit /displayorder {wubi} /addlast

I hope that solves it. I think the boot file for wubi was wubildr, you can check this in the partition where you installed wubi.

---

### Post by noveus on 2010-05-14
Hey, thanks. Ill try it out tmr. Its 4am in the morning here, in Malaysia. I'll try it out and let you if it works.

---

