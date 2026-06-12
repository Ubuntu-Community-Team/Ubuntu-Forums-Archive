---
title: "what is the best boot loader with Ubuntu 10.04 and windows 7?"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by james2b on 2010-10-03
What is the preferred boot loader with Ubuntu 10.04 and windows 7, when multiple booting also with Vista and XP all on one hard drive and each on separate partitions ? All are installed except Ubuntu and now boot with the windows boot manager. I have heard that if you install grub 2 on the MBR, then boot windows 7, that it will replace the grub boot code with windows boot code automatically. So is it best to use that NeoSmart EasyBCD tool to add Ubuntu in to the windows boot manager, and can I install grub on the boot sector of Ubuntu's root partition ?

---

### Post by krishnandu.sarkar on 2010-10-03
Well..answer of all the question is yes. Use GRUB. Install it in ubuntu's /boot parition or MBR it will work normally.

---

### Post by sikander3786 on 2010-10-03
You can use either Grub2 or EasyBCD. Whatever you prefer. But Grub picks up all the available installs, whether Linux or Windows, without any problems.

If you are going to install Ubuntu now, I'll recommend that you let Grub install at its default location i.e, MBR of sda and it'll automatically pick up all your installs and let you dual, triple or quad boot.

> 
I have heard that if you install grub 2 on the MBR, then boot windows 7, that it will replace the grub boot code with windows boot code automatically

I actually couldn't understand that statement.

---

### Post by krishnandu.sarkar on 2010-10-03
> **sikander3786 said:**
> I actually couldn't understand that statement.

He said say if I install GRUB2 on MBR and then boot Windows 7 from the menu then the Windows Bootloader will replace GRUB2.

BTW the answer is NO..!! Never..!!

---

### Post by wilee-nilee on 2010-10-03
> **james2b said:**
> 
I have heard that if you install grub 2 on the MBR, then boot windows 7, that it will replace the grub boot code with windows boot code automatically 

> **sikander3786 said:**
> I actually couldn't understand that statement.

I think the OP has heard tales of the dell data safe program.

> **krishnandu.sarkar said:**
> He said say if I install GRUB2 on MBR and then boot Windows 7 from the menu then the Windows Bootloader will replace GRUB2.

BTW the answer is NO..!! Never..!!
Have a read it does happen.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by webtechquery on 2010-10-03
Grub2.. I'm using it with Ubuntu 10.04...

[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)

---

### Post by krishnandu.sarkar on 2010-10-03
> **wilee-nilee said:**
> Have a read it does happen.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

But how is this possible..?? I'm using it on my desktop since Ubuntu 10.04 released.

---

### Post by sikander3786 on 2010-10-03
> **wilee-nilee said:**
> I think the OP has heard tales of the dell data safe program.


Have a read it does happen.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
I got it now :-)

---

### Post by teresaejunior on 2010-10-03
Dirty strategy to make your *NIX system unbootable

Should I sue them, lads? :shock:

---

### Post by james2b on 2010-10-03
If I want to boot with the Vista/7 boot manager, will the Ubuntu install allow me to put the grub onto the bootsector of Ubuntu's root parttion, or insist to place grub on master boot record. See this here; [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by sikander3786 on 2010-10-03
At the last stage of the installer, just before the installation starts, I think step 7, click the Advanced button and select the target of the boot-loader or un-check "Install Bootloader".

---

### Post by james2b on 2010-10-03
So it may be most safe to select not to install grub at that last page of the install process, if I plan to use the windows boot manager, and add the Linux with that Easy BCD boot configuration tool. "There is a bug in Ubuntu 10.04 that does not allow you to manually install GRUB to another partition." So that may include the boot sector of the Ubuntu 10.04 partition. Here is that guide for easyBCD; [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by sikander3786 on 2010-10-03
Yes, it will be absolutely safe until you feel confident with configuring the install with EasyBCD.

---

