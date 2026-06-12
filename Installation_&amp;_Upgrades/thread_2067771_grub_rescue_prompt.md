---
title: "grub rescue prompt"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by eslam elbyaly on 2012-10-07
i had xp sp two and kubuntu 
i deleted kubuntu partition from xp

when i restarted , i got the prompt    grub rescue

-what i have now in my hand is xp sp3 cd and ubuntu live cd
-i tried to boot from xp cd , and i failed , it did not boot ,i just saw the grub rescue prompt again 

-then i tried to boot from ubuntu live cd , it booted with just two options ,either try it or install it .

- when i tried it , i did not see any partions when i explored the home folder.

- i tried also to install it , but when getting the partitionning window , it just see the whole disk as one mass , dev/sda , as i remember , there were no other partitions .
-Iam afraid of data loss.

Notice: i have no network connection , but i have mobinil usb modem .

Please be direct because i am using mobile for writing this thread .c

---

### Post by amerinde on 2012-10-07
> **eslam elbyaly said:**
> i had xp sp two and kubuntu 
i deleted kubuntu partition from xp

when i restarted , i got the prompt    grub rescue

-what i have now in my hand is xp sp3 cd and ubuntu live cd
-i tried to boot from xp cd , and i failed , it did not boot ,i just saw the grub rescue prompt again 

-then i tried to boot from ubuntu live cd , it booted with just two options ,either try it or install it .

- when i tried it , i did not see any partions when i explored the home folder.

- i tried also to install it , but when getting the partitionning window , it just see the whole disk as one mass , dev/sda , as i remember , there were no other partitions .
-Iam afraid of data loss.

Notice: i have no network connection , but i have mobinil usb modem .

Please be direct because i am using mobile for writing this thread .c


Do you have another XP disk? I assume since you deleted kubuntu, you didnt want it anymore. So, you need to restore the windows MBR.  If you can get a windows disk to boot, goto the recovery console, at the command promt type "fixmbr"

---

### Post by raja.genupula on 2012-10-07
> **eslam elbyaly said:**
> i had xp sp two and kubuntu 
i deleted kubuntu partition from xp

when i restarted , i got the prompt    grub rescue

-what i have now in my hand is xp sp3 cd and ubuntu live cd
-i tried to boot from xp cd , and i failed , it did not boot ,i just saw the grub rescue prompt again 

-then i tried to boot from ubuntu live cd , it booted with just two options ,either try it or install it .

- when i tried it , i did not see any partions when i explored the home folder.

- i tried also to install it , but when getting the partitionning window , it just see the whole disk as one mass , dev/sda , as i remember , there were no other partitions .
-Iam afraid of data loss.

Notice: i have no network connection , but i have mobinil usb modem .

Please be direct because i am using mobile for writing this thread .c

you have a simple process to do . you can find grub restore from signature and that will help you .

---

### Post by darkod on 2012-10-07
It seems XP messed up the partition table when deleting the partition.
And the XP cd should boot, you might have a bad cd if it doesn't boot. It's best to repair the windows bootloader with the XP cd but you can do it also with linux tools if that fails.

Don't try to install ubuntu again if you don't want it, just use live mode to try fixing this.

But if you don't have internet on the computer it might make it more difficult. If this is a corruption in the partition table sometimes that can be fixed by running fixparts from live mode:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

But before running that you can see what fdisk and parted say about the disk:
sudo fdisk -l (small L)
sudo parted -l (small L)

---

### Post by eslam elbyaly on 2012-10-07
> **raja.genupula said:**
> you have a simple process to do . you can find grub restore from signature and that will help you .

what signature do you mean to restore grub from?

---

### Post by eslam elbyaly on 2012-10-07
> **darkod said:**
> It seems XP messed up the partition table when deleting the partition.
And the XP cd should boot, you might have a bad cd if it doesn't boot. It's best to repair the windows bootloader with the XP cd but you can do it also with linux tools if that fails.

Don't try to install ubuntu again if you don't want it, just use live mode to try fixing this.

But if you don't have internet on the computer it might make it more difficult. If this is a corruption in the partition table sometimes that can be fixed by running fixparts from live mode:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

But before running that you can see what fdisk and parted say about the disk:
sudo fdisk -l (small L)
sudo parted -l (small L)

thanks to all of you for you reply ,but please do not let me in the middle of  the road , iam in a bad need to my pc .

Fdisk: unable to seek on dev/sda: invalid argument 
fparted: invalid argument during seek for read on /dev/sda
retry/ignore/cancel? 

I wrote it like so         fdisk -l    ,right?

---

### Post by eslam elbyaly on 2012-10-07
> **eslam elbyaly said:**
> thanks to all of you for you reply ,but please do not let me in the middle of  the road , iam in a bad need to my pc .

Fdisk: unable to seek on dev/sda: invalid argument 
fparted: invalid argument during seek for read on /dev/sda
retry/ignore/cancel? 

I wrote it like so         fdisk -l    ,right?

i wrote ignore 
and i see a table with 5 partitions , three of them are fat32 , which are the windows partitions sure , and the other two , one of them with the number 2 is extended type , file system column is empty , and flags is lba ,

the last one is logical , ext4, flags is empty .

Warning:unable to open /dev/sr0 read-write (read-only file system) . /dev/sr0 has been opened read-only.
Error: can not have a partition outside the disk

---

### Post by darkod on 2012-10-07
You are running XP in FAT32, not NTFS? Do you know? Usually you would run it on ntfs.

And for kubuntu you would usually have two partitions inside the extended partition, the root and the swap partition, not only one.

Which software did you use in XP to delete the kubuntu partition?

---

### Post by eslam elbyaly on 2012-10-07
> **darkod said:**
> You are running XP in FAT32, not NTFS? Do you know? Usually you would run it on ntfs.

And for kubuntu you would usually have two partitions inside the extended partition, the root and the swap partition, not only one.

Which software did you use in XP to delete the kubuntu partition?

i used xp itself for deleting , disk management

---

### Post by eslam elbyaly on 2012-10-07
pic for the table by mobile cam

---

### Post by darkod on 2012-10-07
Well, as you can see one of the errors says "Invalid partition table on /dev/sda". Like I said, the XP procedure messed up something.

In live mode you can download and run fixparts from the link I provided. It should help you out and sort the error. Once you have the program downloaded usually you only need to open the disk with it, like:
sudo fixparts /dev/sda

It can repair most errors automatically.

If it does ask you some questions, be careful what you answer.

Once the partition errors are sorted, we can help you write a generic bootloader using the kubuntu cd since your XP cd is not working.

---

### Post by eslam elbyaly on 2012-10-07
> **darkod said:**
> You are running XP in FAT32, not NTFS? Do you know? Usually you would run it on ntfs.

And for kubuntu you would usually have two partitions inside the extended partition, the root and the swap partition, not only one.

Which software did you use in XP to delete the kubuntu partition?

by the way , i do not want any partition but c,d,e (windows partitions) , i need free space

---

### Post by eslam elbyaly on 2012-10-07
> **darkod said:**
> Well, as you can see one of the errors says "Invalid partition table on /dev/sda". Like I said, the XP procedure messed up something.

In live mode you can download and run fixparts from the link I provided. It should help you out and sort the error. Once you have the program downloaded usually you only need to open the disk with it, like:
sudo fixparts /dev/sda

It can repair most errors automatically.

If it does ask you some questions, be careful what you answer.

Once the partition errors are sorted, we can help you write a generic bootloader using the kubuntu cd since your XP cd is not working.

you forgot i do not have network . any other solution?

---

### Post by darkod on 2012-10-07
No, not without internet so you can get tools. On top of that your XP cd doesn't even boot, and this situation was created by XP disk management.

A windows forum might be a better place to look for more options since you don't even want to keep the dual boot and this is not about repairing grub.

I wanted to at least use the option that the kubuntu cd boots so you can install generic MBR, but the partition table error needs to be sorted before that. The disk partitions are not even read right now.

---

### Post by eslam elbyaly on 2012-10-07
> **eslam elbyaly said:**
> thanks to all of you for you reply ,but please do not let me in the middle of  the road , iam in a bad need to my pc .

Fdisk: unable to seek on dev/sda: invalid argument 
fparted: invalid argument during seek for read on /dev/sda
retry/ignore/cancel? 

I wrote it like so         fdisk -l    ,right?

> **darkod said:**
> Well, as you can see one of the errors says "Invalid partition table on /dev/sda". Like I said, the XP procedure messed up something.

In live mode you can download and run fixparts from the link I provided. It should help you out and sort the error. Once you have the program downloaded usually you only need to open the disk with it, like:
sudo fixparts /dev/sda

It can repair most errors automatically.

If it does ask you some questions, be careful what you answer.

Once the partition errors are sorted, we can help you write a generic bootloader using the kubuntu cd since your XP cd is not working.

please tell me where to download fixparts , there are no partitions i can see when i try ubuntu , just downloads folder, music ,etc... , and how to install it when i download it in any mentioned folder ?
Thanks a lot man

---

### Post by darkod on 2012-10-08
The download link is right there on their home page:
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/)

You need the .deb file for ubuntu, the 32bit or 64bit, which ever you want. If you double click it, it should install.

Then just open terminal and try something like:
sudo fixparts /dev/sda

Note: The software installed in live mode usually is not remembered when you reboot. So if you boot with the cd in live mode again you will have to install it again. It might be better to keep a copy of the downloaded .deb on a usb stick so that you don't need to download more than once.

---

### Post by eslam elbyaly on 2012-10-08
> **darkod said:**
> The download link is right there on their home page:
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/)

You need the .deb file for ubuntu, the 32bit or 64bit, which ever you want. If you double click it, it should install.

Then just open terminal and try something like:
sudo fixparts /dev/sda

Note: The software installed in live mode usually is not remembered when you reboot. So if you boot with the cd in live mode again you will have to install it again. It might be better to keep a copy of the downloaded .deb on a usb stick so that you don't need to download more than once.

i got into the link you provided 
[http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.4/fixparts-binaries/)

and downloaded the i386.deb , is not this what you meant ?

---

### Post by eslam elbyaly on 2012-10-08
any help , where are you darkod?

---

### Post by eslam elbyaly on 2012-10-09
help people , is it the one ?

---

### Post by darkod on 2012-10-09
Yes, you can use i386.deb. Just double click it and it should install.

After that use it in terminal with:
sudo fixparts /dev/sda

If it finds any problem and asks you something about repairing it, you will have to answer depending on the question.

---

### Post by eslam elbyaly on 2012-10-10
> **darkod said:**
> Yes, you can use i386.deb. Just double click it and it should install.

After that use it in terminal with:
sudo fixparts /dev/sda

If it finds any problem and asks you something about repairing it, you will have to answer depending on the question.

i've installed the program , and run the program with sudo command as you said , then , i found this :

---

### Post by eslam elbyaly on 2012-10-10
> **eslam elbyaly said:**
> i've installed the program , and run the program with sudo command as you said , then , i found this :

what should i do ?

---

### Post by eslam elbyaly on 2012-10-10
> **eslam elbyaly said:**
> what should i do ?
please i need a prompt reply , i've got this internet connection for just about one hour ?

and i am in a bad need to this laptop , 

thanks in advance

---

### Post by eslam elbyaly on 2012-10-14
thanks all , i used boot-repair gui , and it is solved

---

