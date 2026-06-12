---
title: "Installing XP on drive which solely has Ubuntu 12.04 installed"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by William_Booker on 2013-10-24
Drive HAD partitions but I installed Ubuntu 12.04 on total drive. Wife went mad. How do I partition the drive to install XP please?

---

### Post by sudodus on 2013-10-24
Do you realize that Windows XP will reach end of life in April 2014. After that there will be no security updates.

If you still have an old backup, I would suggest restoring from that. If not, you can 

0. ***Backup*** your Ubuntu system because there will be risky operations.

1. Boot a live system from CD/DVD/USB, for example an Ubuntu install drive.

2. Run ***gparted*** and shrink the partition with Ubuntu.

3. Create a ***primary partition*** of the unallocated space.

4. ***Install*** Windows XP into that new partition.

5. Boot from a live system from CD/DVD/USB again and ***repair/reinstall the bootloader***, that was hi-jacked by Windows, so that you will get a grub menu to boot Ubuntu.

6. Run **[FONT=courier new]sudo update-grub[/FONT]** in your installed Ubuntu system to get ***dual boot*** (with an entry for Windows).

---

### Post by William_Booker on 2013-10-24
Got as far as 3. ran the XP install disc then got the BSOD

---

### Post by oldfred on 2013-10-24
Did you create a primary NTFS partiton (sda1 thru sda4) with the boot flag?

Post screenshot from gparted if that is the case.

---

### Post by William_Booker on 2013-10-25
Sorry, absolute newcomer to Ubuntu. Boot flag? And what program does Ubuntu use to take screenshots?

---

### Post by sudodus on 2013-10-25
Use ```
sudo gparted
``` to view and edit partitions. At the pull-down menu Partition (or by 'right-clicking on a partition') you can select Manage Flags.

If you are running standard Ubuntu, it should work to press the ***PrintScreen*** key or ***alt + PrintScreen*** to dump only the active window.

---

### Post by oldfred on 2013-10-25
If in Unity you can type screenshot, after clicking on top icon or dash and open search or global search lens.
It is in my menu under Accessories using fallback on 12.04.

Better for graphically apps to use gksudo, if sudo needed. 
gksudo gparted

---

### Post by Nirose on 2013-10-25
> **William_Booker said:**
> Sorry, absolute newcomer to Ubuntu. Boot flag? And what program does Ubuntu use to take screenshots?

Boot flag configures the partition to be used as a boot partition so the computer knows whic partition to use to boot. "**PrintScreen**" button works to screenshot the whole desktop. If you just want the current window "**Alt +PrintScreen**" or if you want to select part of your screen yourself "**Shift + PrintScreen**"

back to the problem. when do you get BSOD while installing Windows?

---

### Post by William_Booker on 2013-10-25
Nirose: After it's installed the set-up files

---

### Post by William_Booker on 2013-10-25
Pressed alt+printscreen but what happens next?

Manage flags set to BOOT

---

### Post by oldfred on 2013-10-26
I so not know for sure where it saves by default. Look in /home, Pictures or Documents. 

The boot flag is really for Windows to know which partition to boot from or repair. Grub does not use boot flag. But a few BIOS, often Intel motherboards insist on a boot flag on a primary partition or BIOS will not even let you start to boot. So we still suggest a boot flag on a primary partition.

---

### Post by William_Booker on 2013-10-26
I've been looking at other posts and some have screen shots. How do they include them in the post?

---

### Post by QIII on 2013-10-26
To add a screenshot, save it somewhere.  Then, when you are composing your post, click on the paperclip button towards the right of the first row of menu buttons just above the text imput box.  You will be able to choose the file.

Please ***DO NOT*** simply paste an image in the text box.  If it works it will be too large.  If it doesn't, it will leave base64 text that one of the staff will have to deal with.

---

