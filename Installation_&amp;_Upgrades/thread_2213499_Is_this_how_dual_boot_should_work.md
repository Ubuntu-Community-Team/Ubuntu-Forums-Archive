---
title: "Is this how dual boot should work?"
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by ratibars on 2014-03-26
I have a Lenovo Z580 laptop and I have installed Ubuntu 12.04 LTS along with  Windows 8. The Windows is not a preinstalled version but a clean install using the MSDN version and by using  the product key retrieved from the BIOS using RWEverything utility.

I'll be grateful if someone could answer these questions:

If I boot through Ubuntu there is a pause for around 30 seconds with a  blank screen before Ubuntu start screen comes up. Is this normal or is there a way I can fix this? It's an i5 processor with 8GB RAM and so this slowness makes me wonder if this is not normal. 

In the BIOS setup Ubuntu shows up as the first boot option (I know I can change this order) and so by default it boots through Ubuntu and it works fine. But the Windows boot option doesn't appear in the Grub boot menu (I hope I'm using the correct terminology).  But if I choose Windows boot option in the BIOS Boot Menu (there is a small button in the Lenovo laptop to go to BIOS options that includes Boot Menu) then it boots through Windows and it works fine as well. Is this how it works on the Lenovo  laptops? It's fine with me and in fact it's more desirable for me so  that I can kinda hide Windows which I rarely use. But I'm curious to  know if this is how it works and it's not related to the problem  described in my first question.

---

### Post by su:bhatta on 2014-03-27
Ideally, this should not be the case. 
Are Windows and Ubuntu in the same HDD but on different partition? If yes then, after successful installation of Ubuntu, Grub should have recognised your Windows partition and added a Grub menu to boot into Windows.
You should not have to go into BIOS to choose to boot Windows. 

This is a very old image but this is how the Grub2 screen almost looks like in dual-boot setup : [http://upload.wikimedia.org/wikipedia/commons/c/cf/GRUB_with_ubuntu_and_windows_vista.png](http://upload.wikimedia.org/wikipedia/commons/c/cf/GRUB_with_ubuntu_and_windows_vista.png)

When logged into Ubuntu you can run the following commands After mounting the Windows partition :

```
sudo update-grub
```

Then see if the Windows boot loader is recognised. If you look the the terminal after executing the command and giving your password , if Grub recognises the Windows boot loader, you will see it in the lines following your command in a matter of about a minute or less. On reboot the Grub menu should have both the Ubuntu & Windows choices.

If it does not show, please revert back.

---

### Post by mastablasta on 2014-03-27
no 30 sekond delay is not normal. can you press in Esc key to see what is going on in the background?

Furthermore linux logs everything in it's logs. there should be a logviewer of some sort in the OS (i dont' use Ubutnu but Kubuntu so my logviewer is a bit different i believe). see if there is anything unusual (like any errors) on boot.

---

### Post by fantab on 2014-03-27
The delay could be a Framebuffer issue which delays splash loading, try:
```
sudo -i
echo FRAMEBUFFER=y >> /etc/initramfs-tools/conf.d/splash
update-initramfs -u
```

Post the output of:
```
sudo parted -l
sudo fdisk -l
```

Did you use Boot-Repair?

---

### Post by ratibars on 2014-03-27
Thanks so much everyone. I tried everything suggested but still the problem persists.

I have not run boot-repair at all at any point in time because boot-repair messed up everthing earlier and I lost my preinstalled Windows and partitions. So I had to scramble to get a copy MSDN version to install Windows back again. Had a very bad experience and never imagined that Ubuntu support will recommend something that could really mess up things. Probably I'm not savvy enough but then what's the point in creating an OS which creates nightmares for ordinary users (sorry for the rant!).

After mounting Windows I ran update-grub and got the following:
[FONT=courier new] Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found memtest86+ image: /boot/memtest86+.bin
Adding boot menu entry for EFI firmware configuration
done
[/FONT]But nothing changed.

I ran the FRAMEBUFFER command as mentioned by Fantab. And I got this:
[FONT=courier new]update-initramfs: Generating /boot/initrd.img-3.11.0-18-generic[/FONT]
After this there is almost no blank screen and Ubuntu screen comes up after a flicker in the screen but this time the startup screens lingers a bit longer (the dots get filled twice). May be that's how it would work.

Here is the result for sudo parted -l (Note: I have left around 400GB of hard drive as unallocated space as I want to format that as NTFS later and use it from both the OS) :

[FONT=courier new]Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  316MB  315MB   ntfs            Basic data partition          hidden, diag
 2      316MB   420MB  105MB   fat32           EFI system partition          boot
 3      420MB   555MB  134MB                   Microsoft reserved partition  msftres
 4      555MB   210GB  209GB   ntfs            Basic data partition
 5      210GB   260GB  50.0GB  ext4
 6      260GB   360GB  100GB   ext4
 7      360GB   380GB  20.0GB  linux-swap(v1)[/FONT]


Here is the result for sudo fdisk -l:

[FONT=courier new]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x533ab857

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.[/FONT][FONT=courier new][IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG][/FONT]

Also please note that when I boot from Ubuntu, just at the very start for a split of a second an error appears which reads something like: [FONT=courier new]error: efdisk read error[/FONT]

---

### Post by fantab on 2014-03-27
> **ratibars said:**
> Thanks so much everyone. I tried everything suggested but still the problem persists.

I have not run boot-repair at all at any point in time because boot-repair messed up everthing earlier and I lost my preinstalled Windows and partitions. 
...

I ran the FRAMEBUFFER command as mentioned by Fantab. And I got this:
[FONT=courier new]update-initramfs: Generating /boot/initrd.img-3.11.0-18-generic[/FONT]
After this there is almost no blank screen and Ubuntu screen comes up after a flicker in the screen but this time the startup screens lingers a bit longer (the dots get filled twice). May be that's how it would work.

Yep, that is how it works.

Run a ['chkdsk']("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html") on the NTFS partitions from Windows. Then run update-grub to check if Grub finds Windows...

If it doesn't then install an run Boot-Repair and '*Create BootInfo Summary*'. BR will generate a URL LiNK to the Bootinfo summary file. Copy that URL and paste it here. We need to see what is going on during boot.

**Boot-Repair does NOT work on Partitions, so it could NOT have messed with any Partitions. If anything is messes with is the BOOT. It is a very good utility, especially if we are working with EFI boots.

---

### Post by mastablasta on 2014-03-28
> **ratibars said:**
>  Had a very bad experience and never imagined that Ubuntu support will recommend something that could really mess up things. Probably I'm not savvy enough but then what's the point in creating an OS which creates nightmares for ordinary users (sorry for the rant!).




as mentioned boot repair only touches the sector of the disk that loads right after BIOS/UEFI and before any OS loads. it won't touch partitions.

the whole mess is not because of Ubuntu but because windows trying to make sure that the only thing that runs on x86 mashcines is windows. which is where their "secure boot" comes in and apparently one of their latest updates even removes GRUB. after the huge uproar form the various insititutions MS "solved it" by requiring that the windows certified PC have the option to disable the secure boot, so that other OS can ibe installed. it seems to me some manufacturers don't respect that and that MS doesn't really oversee it.

i wouldnt' expect this from lenovo though.

---

### Post by fantab on 2014-03-28
```
[FONT=courier new]Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  316MB  315MB   ntfs            Basic data partition          hidden, diag
 2      316MB   420MB  105MB   fat32           EFI system partition          boot
 3      420MB   555MB  134MB                   Microsoft reserved partition  msftres
 4      555MB   210GB  209GB   ntfs            Basic data partition
 5      210GB   260GB  50.0GB  ext4
 6      260GB   360GB  100GB   ext4
 **7      360GB   380GB  [COLOR=#b22222]20.0GB[/COLOR]  linux-swap(v1)**[/FONT]
```

Also, 20GB SWAP is an overkill. 2-4Gb of SWAP is plenty. 
However, if you 'Hibernate' your Ubuntu then SWAP should be equal to or greater than the amout of RAM you have in the machine.
In Ubuntu 'Hibernate' function has some issues, and we usually avoid it, unless necessary.

---

### Post by ratibars on 2014-03-28
Mastablasta, thanks for taking time to explain. It helps.

Fantab, I ran chkdsk and then update-grub but they didn't fix. So I ran boot repair and it fixed it. Thanks so much!

I still have the "error: efidisk read error" appearing for a second at the start before the grub boot menu appears. I googled and found that it's kinda common with dual boot with 12.04. It seems this problem might go away if 13.10 is installed. I even noticed that you replied to someone on the same question. Here are some of the links that I came across:
[http://ubuntuforums.org/showthread.php?t=2200110](http://ubuntuforums.org/showthread.php?t=2200110)
[http://ubuntuforums.org/showthread.php?t=2201239](http://ubuntuforums.org/showthread.php?t=2201239)

Also the booting is a bit slow when compared to my Ubuntu Desktop which has a bit older hardware (but it has a 7200 rpm drive vs my laptop's 5400 rpm; the desktop also has a separate hard drive for Ubuntu).

Please note that I installed Ubuntu using a UEFI bootable USB. I used Rufus utility to create the image. When I ran boot repair I used that same USB stick to boot and then ran it.

May be I will wait until 14.04 LTS is released, get that installed and then try to tackle the "efidisk read error" problem if it still persists.

Thanks again for all your help. I'll mark this as solved.

---

