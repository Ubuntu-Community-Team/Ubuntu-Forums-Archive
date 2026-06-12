---
title: "How can uninstall grub 1.5 from my laptop"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by Fiskal on 2007-02-22
I installed Ubunto 6.0.6 in my laptop (Asus pro31f) with windows vista. After that when i restarted the laptop Grub just showed me Ubuntu and i couldn't enter to windows. So i format the whole hard disk with my recovery cd, but now when a boot my laptop it stops in the middle of the boot and shows this message:

    Grub stage 1.5 loading....wait (something like that)
    error 2

Now i can't use my windows and i don't want using Ubunto.

My question is...Waht happend and how can fix this problem?
How can uninstall Grub from my system?

Thanks!!!!!!

---

### Post by scrooge_74 on 2007-02-22
Your windows Vista CD should give you the option for recovery.  There are some issues with Vista and using grub, there are work arounds but sadly I dont have a bookmark for them since I dont plan to install VIsta ever

---

### Post by Kateikyoushi on 2007-02-22
You can restore MBR to load windows with the fixmbr command, type it to recovery terminal.
I can't tell for sure whether the recovery CD has this option or not.

What happened is that during the installation vista was not added to your grub list, you could have done it manually takes just a few minutes.
When you used the recovery disc you removed the grub config files and it isn't able to load anymore.

---

### Post by Dylnuge on 2007-02-22
OK, if you install Vista, it should work. From what I read, you are saying that you formatted the hard drive, that means you removed Vista (it also should have removed Grub).

Formatting was unnessicary. If you have installed Vista, reboot from the recovery cd, go into the recovery terminal, and type /fixmbr.

If you choose to install Ubuntu again, you just need to open the /boot/grub/menu.lst file and add the code for windows. I will walk you through it if you want.

---

### Post by Fiskal on 2007-02-23
ok man...thanks....The situation at the moment is : I have installed the recovery cd, but it doesn't have the option of console so i can't  fix the MBR from it. After that i installed the recovery cd and i got the same problem with the same message. It means that windows didn't star. Now i have intalled Ubuntu again but i want to run Ubuntu and Windows vista. So someone can give me a solution...According to Dylnuge there is a way for add the code for windows in this file: ./boot/grub/menu.lst. So can someone give me this code and explain me how to do it.Sorry but i don't have enough experience using Unix and ubuntu.....Thanks

Thanks for the previous answers!!!!

---

### Post by Kateikyoushi on 2007-02-23
Am I wrong ifI assume you can boot into ubuntu ?
Then what you have to do is add vista to your grub menu so can boot vista as well.
You need to do this.[LINK]("http://ubuntuguide.org/wiki/Dapper#How_to_add_Windows_entry_into_GRUB_menu")

To see your partiion layout do copy this to the terminal.

```
sudo fdisk -l
```

Probably the best idea would be to post the output of this command here so we can tell how to edit your grub.

---

### Post by Fiskal on 2007-02-23
This is the output of : sudo fdisk -l

 Disk /dev/sda: 100.0 GB, 100030242816 bytes
138 heads, 12 sectors/track, 117978 cylinders
Units = cylinders of 1656 * 512 = 847872 bytes

   Device Boot      Start         End      Blocks   Id                               System
/dev/sda1               2        6185     5120000   1c                     Hidden W95 FAT32 (LBA)
/dev/sda2            6186       25470    15967980    7                      HPFS/NTFS
/dev/sda3           71281      117977    38665116    f                       W95 Ext'd (LBA)
/dev/sda4   *       25471       71280    37930680   83                          Linux
/dev/sda5           73262      117977    37023744    7                       HPFS/NTFS
/dev/sda6           71281       73261     1640256   82                   Linux swap / Solaris

---

### Post by Kateikyoushi on 2007-02-23
First copy these to terminal, it makes a backup of your current gurb then opens it for editing.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```

Add this to the end of the menu

```
title		Microsoft Windows
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

I used these to boot vista at the time I had it on my machine.

---

### Post by Fiskal on 2007-02-23
ok mate.... i did that but the answer was:


root (hd0,1)

Filesystem type unknown, partition type 0x7
save default
make active
chainloade +

error 13:invalid or unsupported executable format 
press any key to continue



If you remember i installed recovery cd but i have not entered  to windows to do thw first configuration. I mean when you start for first time windows due to i couldn't enter to this partition because GRUB!!!!!!

---

### Post by Kateikyoushi on 2007-02-23
I remember but if the recovery would restore your mbr then you would not meet grub at all so it did not. What I am trying to do is add Vista for your grub so can boot both.

Seems your hdd might not be hd(0,1) or vista is not on sda2, do you per chance know which is the vita partition ?

This could help me eliminate the first possiblity.
```
cat /boot/grub/menu.lst
```

---

### Post by Fiskal on 2007-02-24
Sorry mate but i don't know what is the windows partition......

This is the file after apply cat:

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda4 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,3)
kernel          /boot/memtest86+.bin
boot

title           Microsoft Windows Vista
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Thanks again!!!!

---

### Post by Fiskal on 2007-02-28
I want to say Thank you boys...But it didn't work. I edited the menu.lst and windows was added to Grub, also when i tried to enter it was successful and started to loaded windows, but here i got another problem because windows got stuck in the screen loading and it didn't do anything. In conclusion i took the decision of uninstall Ubunto again because i need use windows and a lot of applications for it. I liked Ubuntu and the support of the people but i couldn't solve my problem so i'll use just the live cd.

Now I'll explain how i uninstaller grub and fixed the MBR. Because i had just my recovery cd and it didn't fixed my MBR just for experiment i installed my windows xp desktop cd and formated the whole hard disk. It was successful and fixed my MBR, after that i installed my recovery cd and finally i could enter to windows vista.

Now i'll wait a time until someone can do a successful installation of dual boot with Ubunto and Vista in a laptop......

Thanks mates!!!!

---

