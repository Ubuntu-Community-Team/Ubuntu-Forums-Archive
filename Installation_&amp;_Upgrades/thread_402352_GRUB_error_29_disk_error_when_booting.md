---
title: "GRUB error 29: disk error when booting"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by AMDAthlonX2 on 2007-04-05
Hello, i recently installed Ubuntu 6.10 using the text installer on my computer with Windows 2000. I decided to try dual-booting it and did so. The installation went fine with no errors. Then i restarted the computer when it was done. The GRUB appeared and I selected to boot to the Ubuntu kernel. then an error appears 

```
error 29: Disk write error 
press any key to continue
``` 

upon pressing another key it brings me back to the GRUB boot menu

From there i tried booting linux in recovery mode and editing /boot/grub/menu.lst because of a post I saw that said it was a solution. However i had no success doing so because there was an error when using the gedit command. 

After that I booted up my installation CD and went to "Recover a broken system" from there i tried to reinstall the GRUB in the swappable partition but got an error message "error code 20"

I'm completely lost on what to do from here, if someone could help me, that would be great, i'm a complete linux noob

thanx

---

### Post by phidia on 2007-04-05
You can't install grub to the swap partition. You either install it to the root partition of the drive the install is on or to the mbr of the 1st HD in bios order.
So if I'm understanding you and what you have for an install (windows2000 & ubuntu 6.10) then you want to select "recover a broken system" and install grub to the mbr of the 1st drive. If that doesn't work there are other things to try but maybe it's best to just try that 1st.

---

### Post by louieb on 2007-04-05
when you boot to recovery mode. You are automatically logged on as root.  
so to edit just ```
nano /boot/grub/menu.lst
```nano pretty simple and its commands are listed on the bottom of the screen.

One trick you can use is mc (midnight commander). Its great for file browsing from the cli.
```
aptitude install mc 
```

---

### Post by AMDAthlonX2 on 2007-04-05
thanks, i'll try both and repost after

---

