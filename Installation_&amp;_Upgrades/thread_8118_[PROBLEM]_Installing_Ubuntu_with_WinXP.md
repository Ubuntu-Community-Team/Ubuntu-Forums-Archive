---
title: "[PROBLEM] Installing Ubuntu with WinXP"
date: 2004-12-14
forum: Installation &amp; Upgrades
---

### Post by Pink Floyd on 2004-12-14
Hi,
I'm an Italian boy, and I wanto to try Ubuntu.
My hard disk is partitioned and contains Windows XP.
Some days ago I installed Mandrake in another partition, and LILO worked perfectly so I could use both operating systems.

Now I want to try Ubuntu, but it doesn't recognize the partitions of my HD: it only see's a hda1 of 40GB (total size of my HD), but the HD is partitioned and I want to use both WinXP and Ubuntu, I don't want to format all the HD.

I already have a ReiserFS partition and a swap partition, that I used with Mandrake and then with Debian (which recognized my partitions too).

What can I do?

Isn't there any way to make Ubuntu recognize my partitions and use only the partitions I choose?

Thank you,
Pink Floyd

---

### Post by Alessio on 2004-12-14
Sicuro che la tabella delle partizioni non sia rovinata?
Are you sure about status of partiton table, is it corrupt?

---

### Post by Pink Floyd on 2004-12-14
Sì, ne sono certo, altrimenti non sarei riuscito a installare Mandrake nè Debian pochi giorni fa.

I'm sure. If it was corrupted, I could not have installed Mandrake and Debian a few days ago.

---

### Post by gheorghe_pop on 2004-12-14
What version of Ubuntu are you using?
I had some problems with Hoary then i swiched to Warty wich works greath(Ubuntu+WinXP).
Are you sure your partition's aren't corupt?
Are both of your partiton primary?
You should try fdisk to see your partition table.
Oh yes!How did you partitioned your hardisk?

---

### Post by Pink Floyd on 2004-12-14
[QUOTE=gheorghe_pop]What version of Ubuntu are you using?
I had some problems with Hoary then i swiched to Warty wich works greath(Ubuntu+WinXP).
Are you sure your partition's aren't corupt?
Are both of your partiton primary?
You should try fdisk to see your partition table.
Oh yes!How did you partitioned your hardisk?[/QUOTE]


I'm using Warty.

My partitions aren't corrupt, I've made two NTFS (Win) partitions with Acronis Partition Expert, and the ReiserFS and Linux Swap with Debain installation cd.

If I open partitionexpert he sees the two Win partitions as primary, and the ReiserFS and Linux Swap partitions as logical (probably because it is a "strange" fs for win).
But ReiserFS partition is the root partition, I setted it when installing mandrake first, and then debian.

However, Ubuntu must see all the partitions, but in fact he only sees a generic HDA.

Any suggests?

---

### Post by Pink Floyd on 2004-12-15
problem solved 

(I'm writing from Ubuntu)


now I need to know how to config the default bootloader (I want to delete the unuseful boot options)

---

### Post by TamirEr on 2004-12-15
edit the /boot/grub/menu.lst file.
make sure you know what you're doing there.
you can edit with gedit, nano, emacs, whatever... just make sure you're saving plain text.

example:
sudo gedit /boot/grub/menu.lst

btw, i guess you used grub which is the default in ubuntu...

---

### Post by Pink Floyd on 2004-12-15
yes you're true.
So I have just tomodify that text file, without running any config program that checks that file? good

---

### Post by TamirEr on 2004-12-15
well, the solution i offered will work on almost any linux system.
There's a graphical tool to do the same thing in ubuntu hoary. I don't remember if this option exists in warty... go through the menus and look for "boot" if you want to check it. in hoary it's under system-system settings-boot.
have fun and be careful. it's always a good idea to have a backup of this file. 
It seems like the graphical tool is very easy to use, but understanding GRUB's config file is essential for "the typical linux user" IMHO...

---

### Post by Pink Floyd on 2004-12-16
[QUOTE=TamirEr]well, the solution i offered will work on almost any linux system.
There's a graphical tool to do the same thing in ubuntu hoary. I don't remember if this option exists in warty... go through the menus and look for "boot" if you want to check it. in hoary it's under system-system settings-boot.
have fun and be careful. it's always a good idea to have a backup of this file. 
It seems like the graphical tool is very easy to use, but understanding GRUB's config file is essential for "the typical linux user" IMHO...[/QUOTE]
 yes but I found quite easy to edit the grub config file, and I made a simple "textual" interface with titles etc...:D

I'll probably try the graphical bootloader later.

---

### Post by gheorghe_pop on 2004-12-16
so what  was the problem?
is'n it necesary to run grub-install after modify menu.lst so changes take efect?

---

### Post by Pink Floyd on 2004-12-16
[QUOTE=gheorghe_pop]so what  was the problem?
is'n it necesary to run grub-install after modify menu.lst so changes take efect?[/QUOTE]

no, changes have taken effect only modifying the text file

---

### Post by T31 on 2005-01-12
Hi Pink Floyd, I have the same problem u had,  when I use windows xp I can see my fat32 partition and, I have as well knoppix in other partition, with it I can see everyone,

so why the h_ll I cant see them when Im using ubuntu? even grub can see all my partitions,

tell me please how you did it?

Thanks in advance

---

### Post by T31 on 2005-01-13
just solved, :) really easy for anyone with the same problems starting this guide is super [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by lvv2002 on 2007-05-15
> **gheorghe_pop said:**
> so what  was the problem?
is'n it necesary to run grub-install after modify menu.lst so changes take efect?


[insects memory Skin care Equity Loans physics](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

