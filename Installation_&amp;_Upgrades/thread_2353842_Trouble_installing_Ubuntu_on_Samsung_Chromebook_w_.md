---
title: "Trouble installing Ubuntu on Samsung Chromebook w/ ARM processor"
date: 2017-02-25
forum: Installation &amp; Upgrades
---

### Post by moseph on 2017-02-25
Hi, I´m trying to get the latest long term release of either MATE or Unity installed on my Samsung Chromebook. 

   I´ve tried the crouton method with many distros (unity, xfce, gnome) & releases (precise, trusty, xenial, etc), but the most stable & usable of them (unity-precise in my case) still leaves me with a lot of applications that don´t work properly.

   Then I created a bootable USB with MATE using a Windows computer. I entered the shell command to enable USB booting ([COLOR=#333333][FONT=Menlo]crossystem dev_boot_usb=1), but when I rebooted and held ctrl-u, it didn´t recognize it.

  I then came across a detailed set of instructions designed for my specific chromebook model to install arch-linux on a USB or SD card. I don´t understand much of this, though it entailed commands partitioning the drive. I followed this procedure and was successful installing arch-linux onto an SD card and consequently loading it up by pressing ctrl-u.

  I´m hoping that I could use this method to install MATE or Unity onto the SD card. But I´ll need some help in knowing what to replace the download commands with to install MATE/Unity rather than arch-linux. 

  Following are the commands that I followed from [/FONT][/COLOR]https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook-2     (I didn´t proceed with the Mainline Kernal option)                             

    Any help would be greatly appreciated, thanks.



[h=1]Samsung Chromebook 2[/h]
[LIST]
[*][Overview]("https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook-2#overview")
[*][Installation]("https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook-2#installation")
[/LIST]
[COLOR=#333333][FONT=&quot]
[LIST]
[*]These instructions will create a dual-booting environment where you can switch between booting Arch Linux ARM and the stock ChromeOS. No changes are made to the internal eMMC drive, and your new Arch Linux ARM install will run completely from external storage. This is the recommended setup for those that just want to take a test drive, or don't want to give up ChromeOS.
[*]You must be running the latest ChromeOS prior to installation.
[/LIST]
[h=2]Switch to developer mode[/h]
[LIST=1]
[*]Turn off the laptop.
[*]To invoke Recovery mode, you hold down the ESC and Refresh keys and poke the Power button.
[*]At the Recovery screen press Ctrl-D (there's no prompt - you have to know to do it).
[*]Confirm switching to developer mode by pressing enter, and the laptop will reboot and reset the system. This takes about 15-20 minutes.
[/LIST]
Note: After enabling developer mode, you will need to press Ctrl-D each time you boot, or wait 30 seconds to continue booting.
[h=2]Enable booting from external storage[/h]
[LIST=1]
[*]After booting into developer mode, hold Ctrl and Alt and poke the T key. This will open up the crosh shell.
[*]Type *shell to get into a bash shell.*
[*]*Type [I]sudo su to become root.*[/I]
[*]*[I]Then type this to enable USB booting:crossystem dev_boot_usb=1 dev_boot_signed_only=0*[/I]
[*]*[I]Reboot the system to allow the change to take effect.*[/I]
[/LIST]
[h=2]*[I]Create a root USB or SD for dual booting*[/I][/h][I][I]These instructions are written for installing to a USB drive with the [I]sda device, assuming no other USB drives are plugged in. For an SD card, [click here]("https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook-2#") to magically adjust the instructions for the [I]mmcblk1 device that an SD card will register as.
[LIST=1]
[*]Get a root shell as described in the previous section.
[*]Since ChromeOS will automatically mount any partitions it finds, unmount everything now:umount /dev/sda*
[*]Start fdisk to create a GPT partition table:fdisk /dev/sda
[*]At the fdisk prompt:
[LIST=1]
[*]Type g. This will create a new empty GPT partition table.
[*]Write the partition table and exit by typing w.
[/LIST]

[*]Partition the micro SD card:cgpt create /dev/sda
cgpt add -i 1 -t kernel -b 8192 -s 32768 -l Kernel -S 1 -T 5 -P 10 /dev/sda
[*]To create the rootfs partition, we first need to calculate how big to make the partition using information from [I]cgpt show. Look for the number under the [I]start column for [I]Sec GPT table which is 15633375 in this example:localhost / # cgpt show /dev/sda
       start        size    part  contents
           0           1          PMBR
           1           1          Pri GPT header
        8192       32768      1   Label: "Kernel"
                                  Type: ChromeOS kernel
                                  UUID: E3DA8325-83E1-2C43-BA9D-8B29EFFA5BC4
                                  Attr: priority=10 tries=5 successful=1

    15633375          32          Sec GPT table
    15633407           1          Sec GPT header[/I][/I][/I]
[*]*[I][I]Replace the xxxxx string in the following command with that number to create the root partition:cgpt add -i 2 -t data -b 40960 -s `expr xxxxx - 40960` -l Root /dev/sda*[/I][/I]
[*]*[I][I]Tell the system to refresh what it knows about the disk partitions:partx -a /dev/sda*[/I][/I]
[*]*[I][I]Format the root partition:mkfs.ext4 /dev/sda2*[/I][/I]
[*][I][I][I]Download and extract rootfs tarball:cd /tmp
wget [http://os.archlinuxarm.org/os/ArchLinuxARM-peach-latest.tar.gz](http://os.archlinuxarm.org/os/ArchLinuxARM-peach-latest.tar.gz)
mkdir root
mount /dev/sda2 root
tar -xf ArchLinuxARM-peach-latest.tar.gz -C root[/I][/I][/I]
[*]*[I][I]Flash the kernel to the kernel partition:dd if=root/boot/vmlinux.kpart of=/dev/sda1*[/I][/I]
[*][I][I][I]Unmount the root partition:umount root
sync[/I][/I][/I]
[*]*[I][I]Reboot the computer.*[/I][/I]
[*]*[I][I]At the splash screen, instead of pressing Ctrl-D to go to ChromeOS, press Ctrl-U to boot to the external drive.*[/I][/I]
[*]*[I][I]After logging in as root (password is "root"), you can connect to a wireless network by running:wifi-menu*[/I][/I]
[/LIST]
[/I][/I][/I][/I]
[h=2]*[I][I]Mainline Kernel*[/I][/I][/h]*[I][I]The installation above will use the ChromeOS 3.8 kernel. The mainline kernel can be used instead, though some hardware may not be working yet. Two options are available to switch to the mainline kernel:*[/I][/I]

[LIST=1]
[*][I][I][I]Replace kernel packages after installation
[LIST=1]
[*]Install linux-armv7 packages, replacing the linux-peach package:pacman -S linux-armv7 linux-armv7-chromebook
[*]Type y and hit enter when prompted to flash the kernel to the kernel partition.
[*]Reboot.
[/LIST]
[/I][/I][/I]
[*]*[I][I]Perform a new installation with the above steps using the armv7-chromebook tarball:[http://os.archlinuxarm.org/os/ArchLinuxARM-armv7-chromebook-latest.tar.gz](http://os.archlinuxarm.org/os/ArchLinuxARM-armv7-chromebook-latest.tar.gz)*[/I][/I]
[/LIST]

[/FONT][/COLOR]

---

### Post by him610 on 2017-02-27
Hello moseph and welcome to the forum,

I also have a Samsung ARM Chromebook; although, I have not attempted to install Linux on it. I found the following links on the web that may address your issue...
[http://askubuntu.com/questions/356243/true-ubuntu-on-chromebook-arm-samsung]("http://askubuntu.com/questions/356243/true-ubuntu-on-chromebook-arm-samsung")
[https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook]("https://archlinuxarm.org/platforms/armv7/samsung/samsung-chromebook")
[http://askubuntu.com/questions/356243/true-ubuntu-on-chromebook-arm-samsung]("http://askubuntu.com/questions/356243/true-ubuntu-on-chromebook-arm-samsung")
[https://www.youtube.com/watch?v=tCUoxGTLgbE]("https://www.youtube.com/watch?v=tCUoxGTLgbE")

Good luck.

---

