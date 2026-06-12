---
title: "What to install first - sorry!, another dual boot question."
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by m1ck on 2010-10-06
Hi all, am just wondering whaich os i should install first windows 7 or ubuntu?.

I am going to completely wipe my main hard drive of *all* partitions and start from fresh because every time i've tried to install ubuntu alongside windows 7 (which has always been the main operating system) ubuntu has never shown up in the boot loader.

Any help would be greatly appreciated.
thanks.

---

### Post by Rubi1200 on 2010-10-06
This should help:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

---

### Post by xnostradamusx on 2010-10-06
you should install windows first then ubuntu so ubuntu will properly configure the grub correctly

---

### Post by m1ck on 2010-10-06
Ok thanks all for your input, i will give the above ideas a try.
Thanks again

---

### Post by Rubi1200 on 2010-10-06
You are more than welcome :)

If you have any other questions, feel free to ask.

---

### Post by richf on 2010-10-06
I started with Win 7 installed first. 

I used Win7 to shrink the drive to create a partition for Ubuntu. Then booted the Live CD and installed Ubuntu on the largest contiguous free space.

When I rebooted, I selected Win 7 from the Grub menu and booted into Win 7. 

Once there, I ran EasyBCD (download.com) and rewrote the Win7 MBR; I decided to use the Win 7 boot loader instead of Grub. 

Then added an entry for Ubuntu to the Win 7 boot menu. 

With EasyBCD, you can select which system to use as the default.

Works good for me.

---

### Post by m1ck on 2010-10-07
> **richf said:**
> I started with Win 7 installed first. 

I used Win7 to shrink the drive to create a partition for Ubuntu. Then booted the Live CD and installed Ubuntu on the largest contiguous free space.

When I rebooted, I selected Win 7 from the Grub menu and booted into Win 7. 

Once there, I ran EasyBCD (download.com) and rewrote the Win7 MBR; I decided to use the Win 7 boot loader instead of Grub. 

Then added an entry for Ubuntu to the Win 7 boot menu. 

With EasyBCD, you can select which system to use as the default.

Works good for me.


What did you add with easybcd, im trying to add unbuntu into the windows 7 boot loader now but don't really have a clue what i'm doing, i know its supposed to be simple but then i'm pretty simple too :D

---

### Post by richf on 2010-10-07
If you have EasyBCD 2.0.2 installed in Windows, (after installing Ubuntu) the first thing I do is click the Bootloader Setup button. 

Under MBR config options, I select Install Vista/Win 7 bootloader to MBR. Then click the Write MBR button. This will overwrite the Grub bootloader with Win 7. (I prefer using Win7 bootloader and EasyBCD over Grub).

Then click the Add New Entry Button.

Select the Linux/BSD tab, make Type = Grub2 and Name the entry. I use Ubuntu 10.04

Click Add Entry.

That will add an entry for Ubuntu to the Windows boot loader.

Click the Edit Boot Menu button. You will see 2 entries, Win7 and Ubuntu. Select the default OS to load on start. You can also set the number of seconds to wait to boot the default OS. I use 3. Click Save Settings.

That's all there is to it. When you start the comp, a short menu will appear with the default OS highlighted. You can change the OS with the UP/Down arrow keys.

---

### Post by m1ck on 2010-10-07
Thanks RichF your a star!, that works....not pressing the *write mbr* button was where i was going wrong all this time.

---

### Post by richf on 2010-10-07
Your welcome. Glad it worked.

---

