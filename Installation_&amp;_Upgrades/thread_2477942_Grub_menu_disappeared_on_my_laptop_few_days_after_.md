---
title: "Grub menu disappeared on my laptop few days after dual boot"
date: 2022-08-11
forum: Installation &amp; Upgrades
---

### Post by rrewale on 2022-08-11
Hello, 


First of all, I am new to ubuntuforums.org, and this is my first post. 


I have Windows 10 installed on my laptop [Asus F571GD-BQ368T]("https://www.flipkart.com/asus-vivobook-gaming-core-i5-9th-gen-8-gb-32-optane-512-ssd-windows-10-home-4-graphics-nvidia-geforce-gtx-1050-f571gd-bq368t-laptop/p/itm610800f11cd09?pid=COMFNEK5Y8P3H7KR&lid=LSTCOMFNEK5Y8P3H7KRCS3YZ4"). Recently, I decided to install Ubuntu 18.04 side-by-side with Windows 10. After installation, whenever I clicked the power button on my laptop, I would get grub menu, and it would ask me to choose the OS that I wanted to boot into. This worked for 2-3 days. One day, when I clicked the power button, it directly booted into Windows; I didn't get the grub menu. I restarted my laptop a few times, but still nothing changed.


On my laptop, clicking Esc key opens boot menu, so I tried that. I was given three options to choose from - windows, ubuntu, setup (PFA boot_menu.jpg). Whenever I selected Windows, it booted into Windows 10 correctly, but whenever I selected Ubuntu, it would again open the same screen and ask me to choose from the three options. I tried boot-repair software in a live Ubuntu session, but it didn't recommend any fixes.


Finally, I deleted the Ubuntu partition from Windows and reinstalled Ubuntu. After a few days, the same issue appeared, and again I reinstalled Ubuntu. Today, the same issue has come up again (3rd time), but I don't want to reinstall Ubuntu. Every time I reinstall, I have to spend around 2 days to install all the softwares that I need. So, please help me in identifying and fixing the issue .


boot-repair logs from a live Ubuntu session: [https://pastebin.ubuntu.com/p/pCZBQnNGGx/](https://pastebin.ubuntu.com/p/pCZBQnNGGx/)
boot_menu.jpg - the third option in the image is not visible; it is "Enter Setup", which opens bios settings



Regards,
Rahul

---

### Post by tea for one on 2022-08-12
Here is some info, where other users experienced similar problems.
Raid and Optane seem to be the stumbling blocks.

_UEFI settings_
Disable Fast Boot 
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Optane memory and storage
Remove Optane drive and reset UEFI to default
[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)

_Windows 10 settings_
Turn off Bitlocker 
Disable Fast Start Up i.e. Windows is not hibernating
Some Windows updates turn on hibernation automatically
Disable applications which manage Intel Optane memory & storage
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
[https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10](https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10)
[https://ubuntuforums.org/showthread.php?t=2458373&page=2&highlight=rst+optane](https://ubuntuforums.org/showthread.php?t=2458373&page=2&highlight=rst+optane)
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

Intel Memory and Storage Tool 
[https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux](https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux)

Lastly, for a newish laptop, it would be better to use Ubuntu 22.04 (i.e. a more recent kernel)

---

### Post by rrewale on 2022-09-03
Hello tea for one,
Thank you for your quick response and apologies for replying so late to your answer.

You are right; Optane memory is causing this problem.

Here's what ***I think*** happens:
1) Optane memory acts as a cache for frequently used software, including OS.
After installing Ubuntu, alongside Windows, whenever I powered on my laptop, I was shown a GRUB screen to choose the OS that I wanted to boot into. If I chose to boot into Windows **twice in a row**, the optane memory ended up caching the Windows OS. So, the third time onwards whenever I powered on my laptop, it directly started Windows; i.e. I didn't get the GRUB screen.

One way I dealt with this issue:
Whenever I booted into Windows for some reason, after shutting down the Windows OS, I would boot into Ubuntu once. This is to ensure that, whenever I start my laptop next time (which could be a day or two later), even if I boot into Windows, I don't end up booting into Windows twice in a row.


2) Some times I forgot to boot into Ubuntu as mentioned above and ended up booting into Windows twice in a row. Now, here onwards I didn't get the GRUB menu to choose Ubuntu. To fix this, I would reinstall GRUB2. To do this, I would boot into a live Ubuntu session and run below commands to reinstall GRUB2.

(I found most of the commands here [https://forum.level1techs.com/t/reinstall-grub/134056](https://forum.level1techs.com/t/reinstall-grub/134056); I have made minor modifications in the commands based on my system)

    a) Find out the partitions containing Ubuntu OS and EFI
*        sudo fdisk -l*

        Partial output on my system:
        
        *Disk /dev/nvme0n1: 477 GiB, 512110190592 bytes, 1000215216 sectors**        ... few lines were here ...*

*         Device             Start        End   Sectors  Size Type*
*         /dev/nvme0n1p1      2048     534527    532480  260M EFI System*
*         /dev/nvme0n1p2    534528     567295     32768   16M Microsoft reserved*
*         /dev/nvme0n1p3    567296  315132558 314565263  150G Microsoft basic data*
*         /dev/nvme0n1p4 315147112  598244534 283097423  135G Microsoft basic data*
*         /dev/nvme0n1p5 598244536  663243524  64998989   31G Microsoft basic data*
*         /dev/nvme0n1p6 684257280  998873087 314615808  150G Linux filesystem*
*         /dev/nvme0n1p7 998873088 1000204287   1331200  650M Windows recovery environment*


    b) Mount the partition containing Ubuntu OS
*        sudo mount /dev/nvme0n1p6 /mnt*

    c) Mount the partition containing EFI
*        sudo mount /dev/nvme0n1p1 /mnt/boot/efi*

    d) Mounting few other things
[I]        for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done

    e) [/I]Change root
*        sudo chroot /mnt*

    f) Install GRUB2 (note: in below command, we are using the device name and not specific partition)
*        grub-install /dev/**nvme0n1*
*        update-grub2*

    Shut down the live Ubuntu session and start the laptop again. I would get the GRUB screen to choose the OS that I wanted to boot into.

3) Reinstalling grub doesn't take much time (~10 minutes), but I had to always carry my bootable pen-drive having Ubuntu with me. One time, I forgot my pen-drive. So, I looked for other ways to solve the issue. I started Windows OS, opened Intel® Optane&#8482; Memory and Storage Management, and disabled the Optane memory. After this, I had to reinstall GRUB2 once (which I did by borrowing a pen-drive from a colleague).


This last approach solved the issue permanently. Now, even if I boot into Windows OS multiple times in a row, I don't have to reinstall GRUB2. I get the GRUB screen every time I start my laptop.




Some comments about your answer:
1) I have to use Ubuntu 18.04 only for some work related reason.
2) I had disabled Fast Boot before installing Ubuntu.
3) I had stopped automatic updates in Windows before installing Ubuntu.
4) I didn't want to remove Optane memory. Also, I didn't even want to disable it because I thought that it would make my laptop slow. Later on, I read somewhere that Optane is most effective when you have a HDD in your system; it doesn't improve performance much if you have a SSD. So, since I have a SSD in my laptop and not HDD, I decided to disable the optane memory in Windows. Fortunately, my laptop performance has not degraded (or degraded by such a small amount that I don't even recognise it).


Thank you. Hope my detailed answer/comments above help other people!

---

### Post by tea for one on 2022-09-03
> **rrewale said:**
> Here's what ***I think*** happens:
1) Optane memory acts as a cache for frequently used software, including OS.
After installing Ubuntu, alongside Windows, whenever I powered on my laptop, I was shown a GRUB screen to choose the OS that I wanted to boot into. If I chose to boot into Windows **twice in a row**, the optane memory ended up caching the Windows OS. So, the third time onwards whenever I powered on my laptop, it directly started Windows; i.e. I didn't get the GRUB screen.
Booting into Windows twice in a row destroys Grub - that's a new one for me.
Yet another obstacle to dual booting, but just another rung on the ladder to climb.
> One way I dealt with this issue:
Whenever I booted into Windows for some reason, after shutting down the Windows OS, I would boot into Ubuntu once. This is to ensure that, whenever I start my laptop next time (which could be a day or two later), even if I boot into Windows, I don't end up booting into Windows twice in a row.
Very inventive
>  I didn't want to remove Optane memory. Also, I didn't even want to disable it because I thought that it would make my laptop slow. Later on, I read somewhere that Optane is most effective when you have a HDD in your system; it doesn't improve performance much if you have a SSD. So, since I have a SSD in my laptop and not HDD, I decided to disable the optane memory in Windows. Fortunately, my laptop performance has not degraded (or degraded by such a small amount that I don't even recognise it)
That is good news. I did not know that Optane is most useful for HDD rather than SSD.

If appropriate, it is beneficial to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

