---
title: "Lubuntu doesn't install"
date: 2017-04-11
forum: Installation &amp; Upgrades
---

### Post by gbnmvfx on 2017-04-11
Hi Everyone,

I tried to install Lubuntu 16.10 on my Lifebook A. Everything works fine, until it says that it failed to install GRUB. Then, a window with three options is displayed: 1. Choose another device [...] 2. Continue without installation of [...] 3. Aboard the installation. The thing is: If I choose one of them and press ok, then nothing happens. I have to shut down the laptop by pressing power. I really need help fixing this. I know very little about booting or GRUB. 

Best Regards
Jieby

---

### Post by gbnmvfx on 2017-04-12
I searched for a solution and found this [page]("https://wiki.ubuntuusers.de/GRUB_2/Reparatur/#Reparatur-mittels-Desktop-CD") on wiki.ubuntuusers.de. I tried to fix it by following the steps without knowing what happens, but I am really annoyed now. It's like this: I have a problem, I try to fix it, but I get a problem. I am trying to fix that problem, I get a problem. So I kinda try to solve the problem C of the solution C to the problem B of the solution B to the problem A. I need help :frown:

I tried it with the instructions on this [site]("http://www.pcwelt.de/ratgeber/Grub-2-So-optimieren-Sie-den-Linux-Bootmanager-Grub-Reparaturen-9715246.html"), without success. I used the DVD to check itself and it is testing the memory of the laptop. Until now everything is fine. I am going to try to install it a third time. :-|

---

### Post by Autodave on 2017-04-12
Is this an installation of only Lubuntu or are you trying to put it along side (and keep) your Windows? If you are trying to dual boot, what version of Windows are you running?

---

### Post by gbnmvfx on 2017-04-12
Since Lubuntu deleted it's predecessor, there is no working operating system on the laptop.

---

### Post by yancek on 2017-04-12
Which version of which operating system did you previously have on this computer?
Was this operating system an EFI install or the older MBR?
You can get more detailed information to post here by using boot repair which you can get if you boot the Lubuntu DVD and go to the site below to download it per the instructions on that page.  When you run it, select the option to Create BootInfo Summary rather than trying any repairs.  When it finishes, it should give you a link which you can post here and someone should be able to offer assistance.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gbnmvfx on 2017-04-13
The laptop doesn't use EFI. It runs with BIOS. I don't know if it counts as MBR. I am going to create the BootInfo Summary later this day.

---

### Post by gbnmvfx on 2017-04-13
I attached the BootInfo as zipped txt file. I zipped it because its size is to high in order to be uploaded as a txt file. The suggested repair is:
" [...] The default repair of the Boot-Repair utility would purge (in order to fix packages fix executable) and reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s [...] "

---

### Post by gbnmvfx on 2017-04-14
Is the suggested repair going to solve my problem?

---

### Post by gbnmvfx on 2017-04-14
I ran the suggested repair and it seemed to work because the laptop booted into a terminal interface as "grub". I tried to "reinstall" Lubuntu, but the same error occurred. Now the laptop boots into another terminal interface as "grub rescue". The programm created a [summary]("http://paste2.org/cnmhPk4z") after it finished.

---

