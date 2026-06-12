---
title: "Ubuntu and Win 7"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by teddy379 on 2010-05-23
So, I have Windows 7 as my main OS on the C drive, Ubuntu 10.4 as the second OS on my D drive. I installed Ubuntu from outside Win7, not through the Wubi, so I had to format the D drive, change the file system into ext4 so I ended up not seeing the D drive anymore on Win7.

My first question is, how can I get the Windows booter load first?

My second question is, if I want to remove Ubuntu, how do I get back my D drive?

---

### Post by Tkdboy on 2010-05-23
Hi

You have to change grub settings to boot win7 first.

To format ur partition follow this steps..
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by darkod on 2010-05-23
You mean you want win7 to be the default OS in the grub menu?
Depends how you want to do it. If you prefer with graphical interface, you can install the package startupmanager.

sudo apt-get install startupmanager

Or you can do it with commands issued in terminal. If you want to, just ask.

If you decide to stop using ubuntu, first you will repair your MBR to windows one, then simply delete the ubuntu partitions and format that space as ntfs. Then windows will be able to sue that partition. It can't read linux partitions, not by default.

---

### Post by teddy379 on 2010-05-23
Well the boot loader thing. I don't really have any experience messing with that. The situation right now is, I get the Ubuntu options (Ubuntu, memory test, several other options, Windows 7). If I choose Win 7 I get the Win7 one after the Ubuntu one.

Also about removing Ubuntu. What are the steps exactly? I attached a screenie of what I get when I'm on Windows 7 if I try to format drive D (Ubuntu drive in ext4). Actually the option is greyed out.

---

### Post by darkod on 2010-05-23
Read my previous reply more carefully. I didn't say you can format it directly. I said you can delete it (and you have the option Delete Volume available) and then you can create ntfs partiion in its place.

However, if you do that right now, grub2 will show an error and you won't be able to boot anything. This is because grub2 depends on its config files which are on the ubuntu partition.

The reason why you might be getting a second boot screen with the win7 bootloader is if you had (have) wubi installed inside win7 or similar. Basically, if win7 was the only option in the windows bootloader, it will boot directly after selecting win7 in the grub2 menu.

But if you had other options in the windows bootloader, it will show them as second stage. This is because grub2 doesn't actually boot win7 directly, it just hands over to the windows bootloader.

---

### Post by teddy379 on 2010-06-03
Well one last question.

If I remove Ubuntu and format the remaining space, would it appear as D drive in Windows, or would it be the letter after my CD Rom's drive?

---

### Post by darkod on 2010-06-03
> **teddy379 said:**
> Well one last question.

If I remove Ubuntu and format the remaining space, would it appear as D drive in Windows, or would it be the letter after my CD Rom's drive?

Usually it would take the next available letter, so if D: is available right now, it should be D:.

But you can change those letters around anyway. You see in the screenshot you posted, Change Driver Letter and Path...? But you can only change it to a letter it doesn't exist at that moment. You can't have two C: for example.

---

### Post by teddy379 on 2010-06-03
Glad to know.

Thanks for helping ^^

---

