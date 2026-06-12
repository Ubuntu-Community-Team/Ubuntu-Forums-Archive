---
title: "Fresh build, installed Ubuntu 7.1 from live CD and when i restart i get blank screen"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by adorableedgar on 2008-02-25
When i got Ubuntu in the mail i popped the CD into my DVD drive and then when i clicked on "install/run Ubuntu" it came with the APIC error on my scree, so what i did was disable APIC from my BIOS screen, then the live CD Ubuntu worked...i was able to use Ubuntu from the CD then i decided to install ( the computer in question is a new build, no other previous OS was installed) so after the partitioner get my drive ready and the installer installs Ubuntu (i used the entire disk not two partitions, its only 80gb disk) i get an icon on the desktop that says shows the files on my HDD, so by this point im like "awesome all i have to do now is take the CD out and restart"......so i restart and all i get is a blank screen with a flashing "-"  .....a dash is what i should call it? i dont know its just a line that flashes and a blank screen, i tried reinstalling Ubuntu 7.1 and i still get the same problem...anyone know whats wrong? please help me!

---

### Post by adorableedgar on 2008-02-25
i also have no pci, pci-e cards....all that i have is basic, 1 hdd 1 DVD drive, onboard video and sound.....ps/2 keyboard and mouse

---

### Post by adorableedgar on 2008-02-25
please anyone? im desparate!

---

### Post by confused57 on 2008-02-25
Here are some boot options that can be added to the kernel line in your grub boot menu:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Knoppix cheatcodes:
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

You might start with trying noapic...you can do this by highlighting your Ubuntu entry in the grub boot menu, press "e", then highlight the kernel line, press "e" again, then add noapic to the very end of the line, press "enter", then "b" to boot.

---

### Post by adorableedgar on 2008-02-26
> **confused57 said:**
> Here are some boot options that can be added to the kernel line in your grub boot menu:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Knoppix cheatcodes:
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)

You might start with trying noapic...you can do this by highlighting your Ubuntu entry in the grub boot menu, press "e", then highlight the kernel line, press "e" again, then add noapic to the very end of the line, press "enter", then "b" to boot.

okay but when i turn on the computer is see the BIOS thing that tells me my mobo model and the option "press delete to enter bios" after that i see JUST a blank page with a blinking slash "-" nothing else.....so i don't even know what the grub boot menu is....

---

### Post by confused57 on 2008-02-26
> **adorableedgar said:**
> okay but when i turn on the computer is see the BIOS thing that tells me my mobo model and the option "press delete to enter bios" after that i see JUST a blank page with a blinking slash "-" nothing else.....so i don't even know what the grub boot menu is....

It might help to post some more info about your computer & possibly post the output of(Applications---Accessories---Terminal)::
```
lspci
```
this should show your hardware

This should show how your hard drive is partitioned:
```
sudo fdisk -l
```
-l is a small "L"

In a successful Ubuntu install, after your bios finishes posting, there will be a prompt to press "Esc" to enter the grub boot menu(I think it gives you 3 seconds to do so).

You could also try entering your bios setup and make sure your hard drive is recognized properly or enabling apic in bios(then add the noapic if you get a grub boot menu).

---

### Post by ChronoSphere on 2008-02-26
The dash at the top left corner sounds like it's a booting issue. Are you sure GRUB was installed to the MBR?

---

### Post by adorableedgar on 2008-02-26
> **confused57 said:**
> It might help to post some more info about your computer & possibly post the output of(Applications---Accessories---Terminal)::
```
lspci
```
this should show your hardware

This should show how your hard drive is partitioned:
```
sudo fdisk -l
```
-l is a small "L"

In a successful Ubuntu install, after your bios finishes posting, there will be a prompt to press "Esc" to enter the grub boot menu(I think it gives you 3 seconds to do so).

You could also try entering your bios setup and make sure your hard drive is recognized properly or enabling apic in bios(then add the noapic if you get a grub boot menu).

okay i don't know how to do anything that you just told me to do lol...my hard drive is NOT partitioned....also how do i know i have had a successful install? All i get after i click the install icon on the desktop of the Live CD is the partitioner and the installer but once the installer is done i get no message or alert....all i get is an icon on the desktop that is labeled "/target" ...so what i did after this i rebooted and took out the CD and the i got the black screen with just a flashing cursor NOTHING more.....also when i first tried running Ubuntu from the Live CD the first time i got the "8254 timer not connecteed to IO- APIC Kernel panic- not syncing:IO-apic timer doesn't work! Boot with apic=debug" etc.. error...so what i did to get the live cd going was disable APIC from the bios, then i was able to run the live CD and use Ubuntu FROM the live CD but after i installed it to the hdd i get the problem with the blank screen.....also this is a newly built computer....so no previous OS's have been installed...its a new disk....i haven't formatted the disk, nothing (doesn't ubuntu do this if necessary?) also i already checked my BIOS and it detects my hdd fine.

---

### Post by adorableedgar on 2008-02-26
> **ChronoSphere said:**
> The dash at the top left corner sounds like it's a booting issue. Are you sure GRUB was installed to the MBR?
first off, thank you...
Second- What is the Grub? all i did was pop the Live CD, had the problem with the "apic timer doesn't work!, boot with apic=debug and send..." so to fix it i disabled APIC from my BIOS and was able to get the live CD to load Ubuntu (FROM THE CD) later i decided to install it (i clicked the install icon) it asked me all the question about time zone and username, then i got to the "partition disk section" ....i choose to not partition and just use the entire disk....so later the installer comes up and the progress bar fills up and then it just disappears.....no message saying "CONGRATS!!!! now restart your system"....so i was "okay" and just decided to restart manually and take out the disk...and once the motherboard page model with the "press delete to enter setting" option finished ALL i got was a blank screen with a flashing cursor.......i didn't even get the message that you normally get before you install any OS "insert bootable media and press any key, or restart and set proper boot sequence" 

ps. at the blank page with the cursor i've tried everything....i waited for like 20 minutes for something to happen by itself, then i pressed esc, then ctrl + every letter from A-Z and nothing happened...

---

### Post by adorableedgar on 2008-02-26
> **confused57 said:**
>  

In a successful Ubuntu install, after your bios finishes posting, there will be a prompt to press "Esc" to enter the grub boot menu(I think it gives you 3 seconds to do so).

You could also try entering your bios setup and make sure your hard drive is recognized properly or enabling apic in bios(then add the noapic if you get a grub boot menu).

i never get that prompt to press "Esc"

---

### Post by confused57 on 2008-02-26
> **adorableedgar said:**
> okay i don't know how to do anything that you just told me to do lol...my hard drive is NOT partitioned....also how do i know i have had a successful install? All i get after i click the install icon on the desktop of the Live CD is the partitioner and the installer but once the installer is done i get no message or alert....all i get is an icon on the desktop that is labeled "/target" ...so what i did after this i rebooted and took out the CD and the i got the black screen with just a flashing cursor NOTHING more.....also when i first tried running Ubuntu from the Live CD the first time i got the "8254 timer not connecteed to IO- APIC Kernel panic- not syncing:IO-apic timer doesn't work! Boot with apic=debug" etc.. error...so what i did to get the live cd going was disable APIC from the bios, then i was able to run the live CD and use Ubuntu FROM the live CD but after i installed it to the hdd i get the problem with the blank screen.....also this is a newly built computer....so no previous OS's have been installed...its a new disk....i haven't formatted the disk, nothing (doesn't ubuntu do this if necessary?) also i already checked my BIOS and it detects my hdd fine.
You have to run the commands I gave you from a live cd terminal(Applications---Accessories---Terminal), the output of "sudo fdisk -l" should show if you have a successful install or not.

---

### Post by adorableedgar on 2008-02-26
> **confused57 said:**
> You have to run the commands I gave you from a live cd terminal(Applications---Accessories---Terminal), the output of "sudo fdisk -l" should show if you have a successful install or not.
ok i did what you told me and the results are as follow


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000931d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1824    14651248+  83  Linux
/dev/sda2            9694        9729      289170   82  Linux swap / Solaris
/dev/sda3            1825        9693    63207742+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
ubuntu@ubuntu:~$ 

i've tried everything I can think of...i've made no partitions,,, and then a Playstation Netwrok buddy told me that linux sometimes requries 3 partitions...so i made 3 partitions manually and still no success.......I ALSO tried selecting the option "install OEM, Text-based installer, Run with safe graphics mode," and none of these options have worked for me..the OEM just takes me directly to the blank screen with flashing cursor....and so does the text based installer

---

### Post by confused57 on 2008-02-26
This guide explains how grub works:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

If you have access to another computer, I would recommend that you burn a Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It's a very small download(5-10 Mb?), be sure to read the instructions in the guide on how to burn the image to disk...

When you get the blank screen, you could try pressing "Ctrl+Alt+F1", just to see if you're presented with a console.

You could try reinstalling grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Make a note if you get any errors or if grub installs successfully.

You can mount your Ubuntu partition, using the live cd, & based on the output of "sudo fdisk -l"...open a terminal:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
```
This will mount or allow you to access the files on your installed Ubuntu, using the live cd...you can check the boot entries in your menu.lst(the configuration file for grub):
```
gedit /media/ubuntu/boot/grub/menu.lst
```
menu.lst is short for menu.list, not menu.first

You may also want to check your xorg.conf file to see what video driver is being used:
```
gedit /media/ubuntu/etc/X11/xorg.conf
```
make sure to use a capital X, (one)(one)

It does sound like a hardware issue, which I don't have much experience with; but hopefully someone else can help you with this.  I've seen others suggest to set the Sata controller to "emulate"(don't remember the exact usage) IDE.   If nothing works from the suggestions I've mentioned, you may want to start a new thread(with a descriptive title) in the Laptop & Hardware section of the forum...provide a link to this thread, explain your problem & what you've tried.
Hopefully someone more hardware savvy will be able to assist you.

---

### Post by confused57 on 2008-02-26
Another idea...mount your Ubuntu partition from the live cd, using the instructions in my previous reply, then go ahead and edit your menu.lst:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
cd /media/ubuntu
gksudo gedit /boot/grub/menu.lst
```
Make these changes to your menu.lst:
change the line with timeout to:
```
timeout  10
```
put a # in front of hiddenmenu:
```
#hiddenmenu
```

Change the kernel line in your first Ubuntu boot entry, remove quiet & splash, then add the following options to the end of your kernel line:
```
acpi=off noapic nolapic
```
I'm on Dapper right now, but here's how mine would look:
```
kernel		/boot/vmlinuz-2.6.15-51-386 root=/dev/hda1 ro acpi=off noapic nolapic
```
quit & save

May not help, but you could edit your xorg.conf to use the "vesa" driver, mount your Ubuntu:
```
gksudo gedit /etc/X11/xorg.conf
```
go down to the video device section & change the driver to "vesa"(with quotes)

---

### Post by ChronoSphere on 2008-02-27
It still sounds like a GRUB issue. I've seen that dash problem before.

Based on the output of fdisk, your HD is in fact partitioned (you only need one ext3 partition and optionally one swap partition). And if you can run Ubuntu from the CD, then it makes sense that it can be installed on your HD. So it probably is installed correctly but just doesn't boot up. Paste this command into a terminal window to see your MBR: 

**sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | hexdump -Cv**

If you see all zeros, then GRUB isn't there. If you see random characters and some readable words, then GRUB is most likely installed, but maybe not correctly. Reinstalling it won't hurt.

---

### Post by adorableedgar on 2008-02-27
> **ChronoSphere said:**
> It still sounds like a GRUB issue. I've seen that dash problem before.

Based on the output of fdisk, your HD is in fact partitioned (you only need one ext3 partition and optionally one swap partition). And if you can run Ubuntu from the CD, then it makes sense that it can be installed on your HD. So it probably is installed correctly but just doesn't boot up. Paste this command into a terminal window to see your MBR: 

**sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | hexdump -Cv**

If you see all zeros, then GRUB isn't there. If you see random characters and some readable words, then GRUB is most likely installed, but maybe not correctly. Reinstalling it won't hurt.

okay i put the command in the terminal window and this is what i got

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | hexdump -Cv
00000000  fa b8 00 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |................|
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 01 8b  |.........|...t..|
00000040  4c 02 cd 13 ea 00 7c 00  00 eb fe 00 00 00 00 00  |L.....|.........|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  d6 31 09 00 00 00 00 01  |.........1......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 e1 1e bf 01 00 fe  |......?.........|
000001d0  ff ff 82 fe ff ff 9d 11  48 09 24 d3 08 00 00 fe  |........H.$.....|
000001e0  ff ff 83 fe ff ff 20 1f  bf 01 7d f2 88 07 00 00  |...... ...}.....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
ubuntu@ubuntu:~$

---

### Post by adorableedgar on 2008-02-27
> **adorableedgar said:**
> okay i put the command in the terminal window and this is what i got

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | hexdump -Cv
00000000  fa b8 00 10 8e d0 bc 00  b0 b8 00 00 8e d8 8e c0  |................|
00000010  fb be 00 7c bf 00 06 b9  00 02 f3 a4 ea 21 06 00  |...|.........!..|
00000020  00 be be 07 38 04 75 0b  83 c6 10 81 fe fe 07 75  |....8.u........u|
00000030  f3 eb 16 b4 02 b0 01 bb  00 7c b2 80 8a 74 01 8b  |.........|...t..|
00000040  4c 02 cd 13 ea 00 7c 00  00 eb fe 00 00 00 00 00  |L.....|.........|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  d6 31 09 00 00 00 00 01  |.........1......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 e1 1e bf 01 00 fe  |......?.........|
000001d0  ff ff 82 fe ff ff 9d 11  48 09 24 d3 08 00 00 fe  |........H.$.....|
000001e0  ff ff 83 fe ff ff 20 1f  bf 01 7d f2 88 07 00 00  |...... ...}.....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
ubuntu@ubuntu:~$

could you interpret this for me chrono? because i see many characters but i also so MANY zeros.....

---

### Post by adorableedgar on 2008-02-27
ALSO, i've tried restoring grub by following the directions in one of the links above but when i type the command "find /boot/grub/stage1" on the "grub>" it gives me the response "Error 15: File not found" rather than a location

---

### Post by adorableedgar on 2008-02-27
also, after i first installed Ubuntu i never got the prompt to restart my computer.....the installer just filled up and closed.....so i waited for more activity for like 30 minutes and nothing happened so i just restarted without being prompted to do so

---

### Post by ChronoSphere on 2008-02-27
I knew it -- GRUB is not installed in the MBR. There are too many zeros and the word "GRUB" is not present. Plus the install failed -- you should have mentioned that at the beginning. :)

We are close to solving problem. What does **ls -l /boot/grub** report?

---

### Post by ChronoSphere on 2008-02-27
Here's what GRUB in the MBR should look like. If all else fails, restore it via the dd command. I've attached the GRUB code from my HD. Unzip it first, then install with this command: **sudo dd if=grub of=/dev/sda bs=[COLOR="Red"]446[/COLOR] count=1**

It's not the recommended way to restore grub, but you can try it when none of the other methods work, Then compare it to the one below, and only the last 4 lines should be different because, of course, your partition table is different than mine. :)


```
sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | hexdump -Cv

00000000  eb 48 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.H....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  68 24 69 24 00 00 80 01  |........h$i$....|
000001c0  01 00 83 fe ff ff 3f 00  00 00 5e b2 ae 01 00 00  |......?...^.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
```

---

### Post by adorableedgar on 2008-02-27
lol okay Chrono but before you replied i did the following 

1. GOT SUPPER MAD AND JUMPED UP AND DOWN
2. Decided to install a different way
                    -this time i ENABLED apic on my motherboard 
                    -i added the "noapic" option to the Live CD screen by pressing 
                         "F6" and typing "noapic" after "quiet splash" 
                    -I got to the Live CD desktop and clicked on the "install" icon 
                    -I made no MANUAL partitons but i believe that the guided      
                          partition automatically creates two
                     -I GOT THE RESTART COMPUTER MESSAGE:guitar:
                     -Then i rebooted and got the options to press "esc" to edit
                           the Grub menu....i didn't do it the first time i restarted
                     - I got as far as the screen that shows the Ubuntu Logo and
                           loading bar.....but
                     - it stopped loading and it sent me back to the familiar blank 
                          screen with the flashing cursor...but this time i could type 
                         things....i typed all i kinds of things and i got no reply back
                         so im guess that that function is worthless
                     - i rebooted, this time pressing the "esc" button when
                          prompted
                     - i looked at the first boot option out of 3 total....
                                - it shows the followin "kernel/boot/umlinuz -2.6.22-14
                                   -generic root = UUID= dce 8624b-37aa-456fb-37aa
                                    -456f-bf9f-545104f66a94 ro quiet splash noapic"
                                - it also shows "init rd/ boot/ initrdimg5-2.6.22-14- 
                                   generic
                       - so i tried booting using the 1st of the 3 options
                       -i basically got the same problem as i did the first time i 
                       rebooted after the successful install
                      - 3rd time----> this time i tried booting with the "recovery
                        mode boot" but all i got was alot of text and at the bottom 
                        a message saying "time not working! try rebooting with 
                       "noapic"" 
          +++++ to sum things up---> the grub menu comes up with the option to press "esc" and then the Ubuntu Logo comes up with the loading bar....but the bar stops after filling up about 2cm and then sends me to the familiar blank page with the flashing cursor

---

### Post by adorableedgar on 2008-02-27
also...i can't run the Live CD anymore for some reason....so now im using my trusty Vaio windows XP P4.....lol i was super impressed with my home built computers speeddd.....BUT NOT WITH THE DIFFICULTY TO INSTALL UBUNTU lol ....so im trying to gather as many possible solutions to try before i unplug my keyboard/mouse/monitor from my WINxp before i go to the other computer

---

### Post by confused57 on 2008-02-27
> **adorableedgar said:**
> also...i can't run the Live CD anymore for some reason....so now im using my trusty Vaio windows XP P4.....lol i was super impressed with my home built computers speeddd.....BUT NOT WITH THE DIFFICULTY TO INSTALL UBUNTU lol ....so im trying to gather as many possible solutions to try before i unplug my keyboard/mouse/monitor from my WINxp before i go to the other computer
Looks like you're making progress...after pressing "Esc" to get to the grub boot menu, select your first Ubuntu entry(highlighted), press "e", highlight the kernel line, press "e" again, at the end of the kernel line, remove quiet & splash, then add acpi=off noapic nolapic to the kernel line(see the example I gave you earlier of how it looked in my Dapper kernel line), press "enter", then "b" to boot.

May not work, but worth trying...you might still end up with a graphics problem, but it may boot further than you're currently getting.

---

### Post by adorableedgar on 2008-02-28
> **confused57 said:**
> Looks like you're making progress...after pressing "Esc" to get to the grub boot menu, select your first Ubuntu entry(highlighted), press "e", highlight the kernel line, press "e" again, at the end of the kernel line, remove quiet & splash, then add acpi=off noapic nolapic to the kernel line(see the example I gave you earlier of how it looked in my Dapper kernel line), press "enter", then "b" to boot.

May not work, but worth trying...you might still end up with a graphics problem, but it may boot further than you're currently getting.

yea i tried it...doesn't work.

---

### Post by adorableedgar on 2008-02-29
anyoneeeeeeeeeee? please help[-o<

---

### Post by confused57 on 2008-02-29
> **adorableedgar said:**
> anyoneeeeeeeeeee? please help[-o<
Seems like this is a problem with certain hardware:
[http://www.google.com/search?hl=en&q=8254+timer+not+connecteed+to+IO-+APIC+Kernel+panic-+not+syncing%3AIO-apic+timer&btnG=Google+Search](http://www.google.com/search?hl=en&q=8254+timer+not+connecteed+to+IO-+APIC+Kernel+panic-+not+syncing%3AIO-apic+timer&btnG=Google+Search)
I didn't really see a solution other than what I've already suggested...you may want  to try adding the option noirqpoll to your kernel line.  When booting doesn't work, do you see any boot errors?

The only other thing I could suggest is to try another distro, such as PCLinuxOS:
[http://distrowatch.com/table.php?distribution=pclinuxos](http://distrowatch.com/table.php?distribution=pclinuxos)

or possibly Hardy Heron, the newest version(still in development).
[http://distrowatch.com/?newsid=04766](http://distrowatch.com/?newsid=04766)

Good luck with it...sorry I can't help you more.  You may want to start a new thread in the Laptop & Hardware section describing your problem & provide a link to this thread.

---

### Post by adorableedgar on 2008-02-29
okay i've tried booting with "irqpoll pci=moacpi noapic nolapic acpi=off" option....didn't work...i tried with just the "irqpoll noapic" and what i got was the followin......"[5.90400] Kernel panic- no syncing; attempted to kill init!

then it again and it said "checking root file system- segmentation fault (fail)" ....coud anyone interpret this for me?

---

### Post by Pumalite on 2008-02-29
Follow confused57 suggestion and try other distros to see if you are incompatible with Linux in general or Ubuntu in particular. Also try to install Hardy Heron Alpha5.

---

### Post by adorableedgar on 2008-02-29
> **Pumalite said:**
> Follow confused57 suggestion and try other distros to see if you are incompatible with Linux in general or Ubuntu in particular. Also try to install Hardy Heron Alpha5.
:( i can't believe that there is no way to get this thing working ......is there anyway to download anyother Linux distro directly from online and install directly to the computer? because i was able to get the Ubuntu Live CD to work again, so is there any way that i can download it directly to the computer using the Ubuntu Live CD and install directly without having to burn a CD?

---

### Post by adorableedgar on 2008-02-29
or....I've been reading around and could my AMD Athlon 64x2 be the problem?? 

also, I'm getting ready to give up on Ubuntu...is there anyway to download any other distro DIRECTLY onto the pc i want to install it in using the Ubuntu Live CD? and then just install it directly without burning a CD?

---

