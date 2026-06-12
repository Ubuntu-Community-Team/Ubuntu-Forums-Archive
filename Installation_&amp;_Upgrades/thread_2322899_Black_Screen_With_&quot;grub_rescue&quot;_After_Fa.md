---
title: "Black Screen With &quot;grub rescue&quot; After Failing to Install"
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by Nosophorus on 2016-05-01
Hi!

I tried to update my Ubuntu 12.04 LTS Precise Pangolin to the newer Ubuntu MATE 16.04 LTS Xenial Xerus. In my computer Windows 8.1 was installed too.

First, I created a new partition to install Xenial in it, but after the install, all I got was a black screen after rebooting my computer with the word "**grub**" whatever on it.

Then, I deleted the partition in which Precise was installed and tried to install Xenial in it. Once again, the installation failed and I got more black screen with many words on it.

Finally, I deleted the entire HD and tried to install Ubuntu 12.04 in it. The install was going all right until I got this message:

> [B]grub-efi-amd64-signed failed to install into /target/. Without GRUB boot loader,
the installed system will not boot[/B]

For all the failed install attempts, I used bootable USB sticks (one with Precise and another with Xenial).

I tried to use **boot-repair**, but got nothing useful. I still can`t install an operating system in my machine.

I think I did something wrong, because I really don`t understand all those stuffs about "**UEFI**", "**Secure Boot**" and so on. I did change something related to "**Secure Boot**", but I don`t know if I did it right.

Now, all I want is to install Ubuntu 12.04 once again in my machine. I don`t mind using all the HD for that (Windows is useless to me anyway).

Is there any simple way to do that?

Right now, when I boot from my HD, I got a black screen with the words "**grub rescue**" and when I type "**ls**", I got these three "words": **(hd0)**; **(hdX,msdos1)** (I don`t remember if the **X** was **0 [zero]**  or **1 [one]**), **(hd1)**. The only way I can use Ubuntu in my computer is through a bootable USB stick (I`m using Precise right now).

Best regards.

---

### Post by yancek on 2016-05-01
You should have used the "Create Bootinfo Summary" option with boot repair and posted a link to it here.  Do that now.  You also need to decide if you are going to use UEFI or MBR and if you still have windows 8, in all likelihood it uses UEFI which means your Ubuntu must also be UEFI.  Some info on that at the Ubuntu documentation site below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Nosophorus on 2016-05-01
Hi!

Thank you for yout reply. :-)

I ran "**boot-repair**" and it created  a report. Here you are what the report says:

[http://paste.ubuntu.com/16184588/](http://paste.ubuntu.com/16184588/)

I don`t have **Windows 8.1** installed anymmore. I deleted it on puporse because I wanted to use the entire HD just for **Ubuntu 12.04 LTS Precise Pangolin** (I would like to install the newer **Ubuntu MATE 16.04 LTS Xenial Xerus**, but I can`t configure my DSL Internet connection, however that`s another and secundary problem right now).

My HD partitions are this way right now:

[IMG]http://s32.postimg.org/d5d86gu1x/Screenshot_from_2016_05_02_02_03_32.png[/IMG]

I`ll wait for your feedback and I`m reading right now that Ubuntu Help website you suggested.

Thank you and best regards.

---

### Post by yancek on 2016-05-02
At the very top of the boot repair it indicates you have no boot code in the MBR so it won't boot.
If you then go to the bottom of the boot repair output, you will see that your computer is shown to be in EFI mode but you have no EFI partition.  It suggests you create a BIOS_Grub partition using GParted which is on the Ubuntu installation media.  That way you will be able to put boot code in the MBR and use GPT partitioning.  After creating the BIOS_Grub partition you can install Grub to the MBR of the 1TB drive with the command:  sudo grub-install /dev/sda

The default repair of the boot repair script indicates that this is what it would do, install Grub to the MBR of sda but you need the 1MB BIOS_Grub partition to boot.

---

