---
title: "manually choosing where to install the grub/bootloader"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by abh83 on 2006-12-23
Hello,

I have a 120gb HDD. I would like to make 2 partitions of equal sizes. On one partition i will install Windows XP Pro and on the Other I will install Ubuntu 6.60 Dapper.

However, is it possible to install the ubuntu grub/bootloader on the Ubuntu partition only? (I don't want to play around or change the original grub/bootloader.)

I have installed Ubuntu previously and i have some experience with dual boot. So i'm really just asking wether or not it is possible to independtly choose where to install the ubuntu grub/bootlaoder.

What other variations might there be concerning grub/bootloaders??

thx

---

### Post by mulleta on 2006-12-23
Hi,

Sorry i dont have the answer to your question but i am attempting the same thing.

I have also had experince with and installed dual boot systems with ubuntu/suse/mandriva. So i know that if you have two partions on the same drive it is possile to install windows and linux independantly on the seperate partions.

I have just purchased a laptop with Windows Media center but the deal didnt come with a reinstallation cd (thats ridiculous) so now when i install ubuntu i dont want to make any mistakes as this would lead me to bigger problems.

So in windows (which) is already running fine, i deleted the second partion and left it as unallocated space. I am currently installing the same version as you are, but i am doing it from a live cd.

Now, when it comes to the partioning section, u may select the unallocated space ( the previously deleted windows second partion) and create a new partition. within this partition you have to allow space for 2 sections, the actual main linux partion (ext 3 ?) and then a minimum 2 GB swap partition (linux-swap).

Now my problem is the next installation step. I am not sure where to go from here. The installer now asks where i would like to mount etc etc and other complicated things. I am not sure what to do here at all.

As i have said i cant attempt something as a guess, i need to get it right first time. Do you know what i need to do?

If you dont know, does someone with experise on this subject know what to do.
any help will be greatly appreciated as i would love to get this version working.....and stop using windows :)

Thanks so much

---

### Post by Lin-X on 2006-12-23
First off, if your pc didn't come with any kind of restore cd, I recommend that you get hold of a disk imaging utility, such as Norton Ghost, and make yourself a few backups of your nice, clean Windows system. (There are several other freeware disk imaging aps around. You might try searching on this forum.)

Then, I would go ahead and install Linux and let Grub be installed on the mbr so that you choose your operating system from a menu at boot. I understand your concern over changing anything on your base system, but this can be undone easily. Suppose you decide to get rid of Linux and just have Windows again: you would boot into Windows, get to a DOS prompt and type fdisk/mbr. That should set your mbr back to its original condition. There is no reason to be afraid of Grub, nothing spooky about it.

Please do get some kind of backup for your Windows system. Do it right away, before you make anymore changes.

---

### Post by Amorphous_Snake on 2006-12-23
But won't running fixmbr make some partitions unreadable? This is what is said when I tried to do so using the Windows XP CD. I didn't go on and complete the process, though, so I don't know if that's true or not.

---

### Post by Lin-X on 2006-12-23
Setting the mbr back to its original state will not make any partitions inaccessible; it would make another operating system inaccessible, but I was supposing that you might want not to use Linux anymore. If you intend to keep Linux, you should have no problem using Grub on the mbr. It will see your Windows system with no problem. At boot, it will show you a menu and you will have time to choose which system you want to boot. The arrangement of items in the menu, the default system, the time allowed to choose, etc. can all be changed if you wish.

If you are dual booting Windows and Linux, I don't know how you would access Linux if you didn't install Grub on the mbr. I know that you can install it in some other partition, but don't understand why you would want to do this. I think if you let Ubuntu install Grub on the mbr 
you will be very happy with the result.

---

### Post by cotcot on 2006-12-23
Install ubuntu with the alternate install CD. This gives you the possibilty to install the bootloader elsewhere than the MBR. Could be on a usb stick that you put in when you want dapper. (usb stick must be before the hard disk in the boot order.

---

