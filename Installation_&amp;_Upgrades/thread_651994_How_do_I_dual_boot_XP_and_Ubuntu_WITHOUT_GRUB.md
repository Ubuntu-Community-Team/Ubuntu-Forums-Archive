---
title: "How do I dual boot XP and Ubuntu WITHOUT GRUB"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by TonyKmau on 2007-12-28
I've dual booted Windows XP and Ubuntu for a long time on my current machine. But after a bad upgrade I was left with unbootable machine due to Grub Error 22, and both my ubuntu and XP partitions were somehow ruined. I solved the Error 22 but I am left with an unbootable ubuntu partition and a reinstalled XP one. I'm not asking for help on this, just giving you the back story to my query.

How can I dual boot XP and ubuntu without using grub? I want the two operating systems to be as seperate as possible, so if I have a problem with one it won't effect the other, like it did on my machine. I will be getting a new computer in the new year so I will be a clean install.

Could wubi be an alternative to dual booting? Will it have any disadvantages against installing ubuntu traditionally?

Any help would be much appreciated. :)

---

### Post by LaRoza on 2007-12-28
You can:

* Keep the Super Grub Disk on hand to easily and quickly restore and fix the MBR of Grub or the Windows boot loader

* Use VirtualBox or another VM

* Use LILO or another boot loader.

---

### Post by aysiu on 2007-12-28
If you have at least 512 MB of RAM (I'd recommend 1 GB, though), VirtualBox would be the way to go:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Otherwise, Wubi is a good choice.

But Wubi is not an alternative to dual booting--it's just a different way to set up a dual boot. VirtualBox is an alternative to dual booting.

---

### Post by lvleph on 2007-12-28
You could always use Wubi, but then Windows would be your main OS and Linux would be on an image. There are other problems associated with it too, such as difficulties upgrading.

---

### Post by pietjanjaap on 2007-12-28
You can switch harddisk, witch removable bracket.

But better is to search wat is the problem with grub.
The only problem wat i have is that grub mixes(changes) the harddrive nr, so the computer would not boot.
This you can fix. I had this 3 times.

If grub fails then use supergrub, very simple.

---

### Post by CypherHackz on 2007-12-28
i am not sure you can do dual boot with two different boot loader on same hd. maybe wubi is the best way you can choose.

-cypher.

---

### Post by meierfra on 2007-12-28
You can also do a regular dual boot, but instead of installing Grub to the MBR install Grub to the Ubuntu partition and add  Ubuntu to the Windows boot loader .


If you have two different hard drive, you can keep the OS' completely separate. Just install Windows and XP on different drives  and install Grub to the MBR of the Ubuntu drive.   Set  bios to boot from the Ubuntu drive. But if Ubuntu fails, you can just boot from the Windows drive.

---

### Post by meierfra on 2007-12-28
> XP partitions were somehow ruined. I 

??? Nothing Ubuntu  does should    effect your Windows partition. To get back into windows you just have the fix the MBR, you should not have to reinstall Windows.

---

### Post by TonyKmau on 2007-12-30
what would happen if i was to uninstall grub from the synaptic package manager?

---

### Post by TonyKmau on 2008-01-01
does anyone know?

---

### Post by allforcarrie on 2008-01-01
you should try WUBI!!!!!!!!! you dont install grub at all but you get a full function ubuntu.

---

### Post by CypherHackz on 2008-01-02
but using wubi you need to download ubuntu files from the server, am i right? is that is the case, user who has slow connection might need to wait hours before they can use ubuntu. if they already has ubuntu live cd, they can install it in a snap like what i did. :D

-cypher.

---

### Post by Em-Buntu on 2008-01-02
I use Partition Magic "Boot Magic" to boot Win XP 64/Ubuntu/Suse.

It works great since I never have to worry about over writing Win boot, Grub, or any other boot module.

---

