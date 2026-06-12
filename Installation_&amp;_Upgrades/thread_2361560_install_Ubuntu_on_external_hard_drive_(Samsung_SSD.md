---
title: "install Ubuntu on external hard drive (Samsung SSD)"
date: 2017-05-18
forum: Installation &amp; Upgrades
---

### Post by jackkiller1 on 2017-05-18
Hi. Recently, I was planning to install Ubuntu completely on my external hard drive (Samsung SSD), but I failed. 

First, I run the installation on my USB and I choose the option "try Ubuntu without installation". Then, I plug the SSD into my laptop. During the installation process, I choose to install Ubuntu on the SSD, including the grub loader. After the installation is finished, I shut down my laptop. Then, I open my laptop and enter the BIOS setup. After I choose to boot from external hard drive, the screen becomes absolutely black. Yes, absolutely black. Nothing shows up. I have tried most of the methods on Google and you know the results. Does anyone meet such a problem and successfully fix it? 

PS: my laptop is Win7, 32bits, HP dv6 series.

---

### Post by oldfred on 2017-05-18
May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jackkiller1 on 2017-05-18
I am a little confused. How can I generate a report without logging into Ubuntu? I can run Ubuntu via my USB installer. But as I said, I can't run it on my external hard drive. Can you give me more details so that I can generate a detailed report? Thank you

---

### Post by oldfred on 2017-05-18
Boot the Ubuntu live installer and as per instructions on link above:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-info && boot-info
```

Run the report (see example screens if needed in link) and post just the link it gives.

---

### Post by jackkiller1 on 2017-05-20
Hi. When I run the commands, the report does not give a correct link. The link given to me does not have a number following ".org". Hence, I have attached the .zip file. Please take a look. Thank you.

---

### Post by oldfred on 2017-05-20
Do not know if this is an issue, but another thread I suggested changing hdX to hd0 as from BIOS/grub boot drive is always hd0.
But grub is supposed to be using UUID to find correct partition.

If you can get grub menu by holding shift key when booting. Change all references of hd2 to hd0 for boot stanza and AHCI2 to 5.
set root='hd2,msdos5'

If still not booting try manually editing the grub.cfg in install using live installer.

---

