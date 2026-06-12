---
title: "ux31a dual boot problems"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by bprior89 on 2012-10-26
So I just bought a new zenbook prime ux31a a few weeks ago and thought I would try putting ubuntu on it along side Windows 7. I first created a partition in Windows before installing with my live USB. Installed Ubuntu, updated it, and tried running Boot-Repair. When I restarted Windows 7 still gave me a invalid efi path error. 

I basically followed this install procedure: [URL="http://www.citizenstain.com/2012/09/tutorial-dual-boot-windows-and-ubuntu.html"]http://www.citizenstain.com/2012/09/tutorial-dual-boot-windows-and-ubuntu.html
[/URL] 
Here is a link to the Boot-Repair report: [http://paste.ubuntu.com/1308054/](http://paste.ubuntu.com/1308054/)

I have tried searching around and it appears Boot-Repair seems to fix everyone else's issue, so I am at a loss. Anyone able to help?

---

### Post by YannBuntu on 2012-10-26
Hello

> **bprior89 said:**
> Here is a link to the Boot-Repair report: [http://paste.ubuntu.com/1308054/](http://paste.ubuntu.com/1308054/)

Now the GRUB menu should show a "Windows UEFI loader" entry. Did you try it?

---

### Post by bprior89 on 2012-10-26
> **YannBuntu said:**
> Hello



Now the GRUB menu should show a "Windows UEFI loader" entry. Did you try it?


When I try that option it now brings me to the starting windows screen, then a black screen that says something along the lines of "setting up your computer for first use". Loads windows in a super low resolution, and then immediately shows a Asus screen that says that it is configuring the computer. After about a second of that my computer restarts.

It used to just show the starting windows screen and then go back to grub.

---

### Post by YannBuntu on 2012-10-26
ok. Then your Windows UEFI boot is broken. This may be due to partition resizing.

> **bprior89 said:**
> I first created a partition in Windows before installing with my live USB.

After creating this partition, and just before installing Ubuntu, did you check that Windows was still booting ok?

---

### Post by bprior89 on 2012-10-26
> **YannBuntu said:**
> ok. Then your Windows UEFI boot is broken. This may be due to partition resizing.



After creating this partition, and just before installing Ubuntu, did you check that Windows was still booting ok?


I believe so, but I don't remember 100% if I rebooted into Windows after resizing. Is there a way to fix it?

---

### Post by YannBuntu on 2012-10-29
You can try to fix it via a Windows disk, this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) , until you have direct access to Windows.
Then use Boot-Repair to recover the GRUB menu.

---

