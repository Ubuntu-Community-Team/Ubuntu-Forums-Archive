---
title: "Reinstalling Grub After Windows"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by ElMoshe on 2010-12-13
Every other guide I've seen is confusing the heck outta me. 
 
I had ubuntu, and no other OS, then I installed win7, and now I want GRUB to be my MBR and any help?

---

### Post by tajiknomi on 2010-12-13
> **ElMoshe said:**
> Every other guide I've seen is confusing the heck outta me. 
 
I had ubuntu, and no other OS, then I installed win7, and now I want GRUB to be my MBR and any help?

[SIZE=2]you want to say that you didn't see ubuntu anymore,right?

this is because windows has Overwrite your mbr, you have to install Grub-again.... using live cd...

Once you in live Cd:-

Mount your Ubuntu-drive:-

 [/SIZE]```
[SIZE=3]*sudo mount /dev/sd**XY*** /mnt[/SIZE]
```[SIZE=2]
***Change XY*** with your Partition of Ubuntu...[/SIZE]
[SIZE=2]
Once it is mounted, Reinstall Grub by the Following Command:-

[/SIZE]```
[SIZE=3]sudo grub-install --root-directory=/mnt /dev/sd**X**[/SIZE]
```[SIZE=2]In the Upper code, Change "X" with your hdd e.g ***sda(if you have only one hdd)***....Once it is done,you will get back your Grub along with Ubuntu, all you have to do is to just Go to Ubuntu , and "***sudo update-grub***" to get your win-7 too[/SIZE]...

---

