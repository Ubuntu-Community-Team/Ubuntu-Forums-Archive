---
title: "complete ubuntu21.10. does not boot from USB-device (but live-usb boots fine)"
date: 2021-11-01
forum: Installation &amp; Upgrades
---

### Post by sciro16v on 2021-11-01
Hello everybody,
I am new with Linux/Ubuntu and try to install ubuntu21.10. on an USB device. I am struggeling since days with google and youtube, but I don't succeed.

What's the problem?

- I start my Lenovo t460s
- I hit Enter to interrupt booting
- I hit F12 to select booting from USB-drive
- I select my USB (it appears there with the correct brand name), screen is getting dark for some seconds and I see the same (lenovo)-menu (device-selection) again. Nothing happend.

Note: the same process works fine with my ubuntu-live-usb-device, which I used for the installation. After selecting my USB-device grub launches with several boot options, I hit the enter key and ubuntu-live starts fine.

What I tried:

- I created an ubuntu-live-usb with rufus in windows
- USB-booting works fine
- I deleted all partitions on my second (target) USB drive with gparted.
- I hit the icon "Install Ubuntu21.10".
- I tried several things, let the installer create partitions on his own ("erase disk and install ubuntu"). I also tried "somethings else" and created primary partitions for EFI and ext4 on my own. I tried the option "Update during installation...." and "install third party software...."). Nothing works. I have done at least 10 installations in the last days. Have anybody some hints for me?

During installation the message occurs "sbd1 as ESP" and "sbd2 as ext4". Furthermore I can read "Running grub-install /dev/sdb". I am not familiar with EFI. Should grub run in the EFI partition? The live-USB has only one Fat32 partition.

 I was afraid if the USB drive has a problem. But it's brand new. I bought 3 in one package and used the other two ones for a windows-rescue-usb and the ubuntu-live-USB-drive some days ago. Both are bootable and work without any problem.

I hope somebody has an idea.

greetings from germany.

---

### Post by grahammechanical on 2021-11-01
When you attempt to install Ubuntu to the second USB stick do you get any messages that the installation process has failed or has finished? You say "nothing works." Does that mean that after every completed attempt to install Ubuntu on the second USB stick it is the loading of Ubuntu from that second USB stick that does not boot? I just want clarification.

Do you remove the first Ubuntu USB stick? Is it not better to set the boot priority to the USB stick so that the BIOS/UEFI looks to the USB drive before looking for an OS on the hard drive?

Regards

---

### Post by ubfan1 on 2021-11-01
Did any bootloaders  actually get copied into the EFI partition (under /EFI/ubuntu and /EFI/Boot)?  Be aware of longstanding launchpad bug 1396379, where grub gets installed to the wrong disk (but your progress messages seem to indicate grub went to sbd (sdb?)).

---

### Post by sciro16v on 2021-11-02
> **grahammechanical said:**
> When you attempt to install Ubuntu to the second USB stick do you get any messages that the installation process has failed or has finished? You say "nothing works." Does that mean that after every completed attempt to install Ubuntu on the second USB stick it is the loading of Ubuntu from that second USB stick that does not boot? I just want clarification.

Sorry for bad communication from my side. Every attempt was running perfect without errors. It ended with the "Restart now"-Window. But if I restart, I can not boot from the second stick. It is recognized by the laptop and can be selected with "boot from there" but then nothing happens. Live-USB-device has no problems. I can boot it, how often I want.

> **grahammechanical said:**
> 
Do you remove the first Ubuntu USB stick? Is it not better to set the  boot priority to the USB stick so that the BIOS/UEFI looks to the USB  drive before looking for an OS on the hard drive? 

Yes maybe better, but I removed the first one, so this shouldn't have any impact.

> **ubfan1 said:**
> Did any bootloaders  actually get copied into the  EFI partition (under /EFI/ubuntu and /EFI/Boot)?  Be aware of  longstanding launchpad bug 1396379, where grub gets installed to the  wrong disk (but your progress messages seem to indicate grub went to sbd  (sdb?)).

On the (target-) USB device:

/boot/efi    empty
/boot/grub  not empty, grub.cfg, etc.

sudo fdisk -l  shows me "/dev/sbd1 512 M EFI System"

sudo mount /dev/sbd1 /mnt leads to an empty /mnt folder. Repeating the command leads to "/dev/sbd1 already mounted on /mnt". /mnt is still empty. What does that mean?

---

### Post by Impavidus on 2021-11-02
It looks like the installer put the bootloader files on the EFI partition of the internal drive. This is the bug referred to above. This makes the usb drive unbootable – although it may still be possible to boot the system there via the EFI partition on the internal drive. To avoid this, make sure you completely disable the internal drive. Maybe you can via EUFI settings, maybe you can physically disconnect the drive.

---

### Post by yancek on 2021-11-02
>  /boot/efi    empty

You indicate you have an EFI partition on the target USB but that it is empty.

>  /boot/grub  not empty, grub.cfg, etc.

Does the above mean that you have the expected grub files in the /boot/grub directory of the "2nd USB" you are trying to install to?

>  sudo mount /dev/sbd1 /mnt leads to an empty /mnt folder.

I don't know it this is simply a typo on your part or some other problem.  It is NOT and NEVER HAS BEEN sbd1 or sb anything, it is always sd as the first 2 letters on that type of drive.  This is very important and will never work if not entered correctly.  This is also something very basic to any Linux.
Are you running this command from the 'live' Ubuntu you used to install Ubuntu?

Did you check if it is the error referenced in post #3 above?  Do you have Ubuntu or one of its derivatives installed n an internal drive?  Do you have windows on an internal drive?  Do you have an EFI partition on any internal drive?  What are the contents of the EFI partition on an internal drive if you have one?  Most likely scenario is the error referenced above.  If you have that problem and installed the Grub EFI files to an internal EFI partition, I would suggest you read through the links below several times to make sure you understand the process and maybe do an online search for "ubuntu installed Grub EFI to wrong partition" or something similar.  Read through several to make sure you understand it before proceeding..

 [https://askubuntu.com/questions/740253/how-to-install-grub-in-an-external-hard-drive](https://askubuntu.com/questions/740253/how-to-install-grub-in-an-external-hard-drive)

[https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition](https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition)

---

### Post by sciro16v on 2021-11-02
> **Impavidus said:**
> It looks like the installer put the bootloader files on the EFI partition of the internal drive. This is the bug referred to above. This makes the usb drive unbootable &#8211; although it may still be possible to boot the system there via the EFI partition on the internal drive. To avoid this, make sure you completely disable the internal drive. Maybe you can via EUFI settings, maybe you can physically disconnect the drive.

Hello Impavidus, I have also heard about that issue, but my internal drive with windows11 works without any problems and I tried the installation to the usb device so much times.

> **yancek said:**
> You indicate you have an EFI partition on the target USB but that it is empty.

Does the above mean that you have the expected grub files in the  /boot/grub directory of the "2nd USB" you are trying to install to?


On the second USB is a (I guess system-????)partition. There is a folder  /boot/efi and /boot/grub. My question was, if there should be a content  in it.


> **yancek said:**
> 
I don't know it this is simply a typo on your part or some other  problem.  It is NOT and NEVER HAS BEEN sbd1 or sb anything, it is always  sd as the first 2 letters on that type of drive.  This is very  important and will never work if not entered correctly.  This is also  something very basic to any Linux.
Are you running this command from the 'live' Ubuntu you used to install Ubuntu?

Should be a typo. I tried exactly the same some minutes ago again with sdb1.

> **yancek said:**
> 
Did you check if it is the error referenced in post #3 above?  Do you  have Ubuntu or one of its derivatives installed n an internal drive?  Do  you have windows on an internal drive?  Do you have an EFI partition on  any internal drive?  What are the contents of the EFI partition on an  internal drive if you have one?  Most likely scenario is the error  referenced above.  If you have that problem and installed the Grub EFI  files to an internal EFI partition, I would suggest you read through the  links below several times to make sure you understand the process and  maybe do an online search for "ubuntu installed Grub EFI to wrong  partition" or something similar.  Read through several to make sure you  understand it before proceeding..


In my opinion it's not the error from post #3 because my internal drive  (windows11 only, EFI partition with windows bootloader) shows no  different behavior since I started my "experiments". But I didn't check the efi-partition, because as mentioned above if I try to mount it in /mnt the folder is still empty.


 > **yancek said:**
> 
[https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition](https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition)

I want to try it, but I don't understand this line:

Note : sdX = disk | sdXX = efi partition | sdXY = system partition

I have my second USB device with full ubuntu21.10 (no live-usb). I have  an efi-partition and an ext4-partition with all folders, I expect in  linux. I guess the second one is the system partition, isn't it? What does he mean  with "disk"?

---

### Post by tea for one on 2021-11-02
> **sciro16v said:**
> I want to try it, but I don't understand this line:
Note : sdX = disk | sdXX = efi partition | sdXY = system partition
I have my second USB device with full ubuntu21.10 (no live-usb). I have  an efi-partition and an ext4-partition with all folders, I expect in  linux. I guess the second one is the system partition, isn't it? What does he mean  with "disk"?

Your Windows drive is sda
Your Ubuntu installation is sdb

sdb = disk
sdb1 = efi partition (fat32)
sdb2 = system partition (ext4)

---

### Post by ubfan1 on 2021-11-02
sda, sdb, ... are disks -- little boxes for storage (as opposed to Microsoft usage which they also include disk partitions as "disks").;
sdb1 is the first partition on the second disk -- likely your (empty) EFI partition since you checked it by mounting it at /mnt/something  and looking at it.  normally this EFI partition gets mounted at /boot/efi.  Before the mount, the /boot/efi is just an empty directory, after the mount you should see the top level of the EFI partition (just the EFI directory), so ls /boot/efi produces EFI.
Under /boot/efi/EFI, there should be directories Boot and ubuntu (and Microsoft on your internal disk).  
  The USB EFI partition is empty because the directories and bootloaders all got copied to the first internal disk (like the bug indicated).  These are just files, so the simple fix to make the USB boot work is to copy everything (well, ...Microsoft is not needed, but wont hurt anything) from the internal EFI to the USB EFI. Nothing else needs to be done to make the USB boot in EFI mode.  The grub (and shim) bootloaders in the USB EFI are not used after the boot, so the mount at /boot/efi is really just to allow for occasional updates of gurbx64.efi, etc.  Booting the USB uses the EFI/Boot/bootx64.efi bootloader which is a copy of either grubx64.efi or shimx64.efi (depending upon if secure boot was on when installed).  shimx64.efi needs a copy of grubx64.efi in the same directory to work, and looks for EFI/ubuntu/grub.cfg to pull in the grub menu (this grub.cfg is just a three line stub which pulls in the maintainted /boot/grub/grub.cfg from the system root).
  The installation of additional bootloaders do not interfere with each other, but they may replace the device default bootloader in EFI/Boot/bootx64.efi with themselves.

---

### Post by oldfred on 2021-11-02
Only post report for now.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by sciro16v on 2021-11-03
@ubfan1 Thanks for your reply, and thanks to all others who mentioned that grub is installed on the internal disk. You were right. I "found" the files on the EFI-partition of the internal drive. I copied the files BOOTX64.CSV, grub.cfg, grubx64.efi, mmx64.efi und shimx64.efi to the usb-efi-partition. Booting still doesn't work. Then I copied the files to /boot/efi, also no booting possible.

@oldfred Thank you for your post. Unfortunately I am not able to manage installing boot-repair.

[https://www.dropbox.com/s/gkr0ny4dtt64ty4/IMG_7245.JPG?dl=0](https://www.dropbox.com/s/gkr0ny4dtt64ty4/IMG_7245.JPG?dl=0)

---

### Post by oldfred on 2021-11-03
You need to copy /EFI/Boot to a new /EFI/Boot and copy /EFI/ubuntu to a new /EFI/ubuntu in the ESP on the external drive.

Then you boot from a drive entry, just like you do with the live installer.
Your internal ubuntu entry will work from the system you installed from,  unless you want to delete it and only use external drive's entry.

---

### Post by sciro16v on 2021-11-03
> **oldfred said:**
> You need to copy /EFI/Boot to a new /EFI/Boot and copy /EFI/ubuntu to a new /EFI/ubuntu in the ESP on the external drive.

I tried it exactly in this way just some minutes ago. No booting from this USB possible. But I'm not wondering because, as I mentioned some posts above, I have also no grub if booting from my internal drive. I am a complete newbie, so maybe I am wrong, but in my opinion I copied grub that doesn't work on my internal drive to my (target-) usb and it doesn't work also. Maybe this is why there is no ubuntu on the internal drive.

What about the other solution? What did I wrong with "boot-repair"? Have you seen the image in the link?

---

### Post by oldfred on 2021-11-03
You need to click on the Boot-Repair link from your Ubuntu live installer in live mode.
Then follow the instructions using ppa to install it:
2nd option : install Boot-Repair in Ubuntu

Only post link to Summary Report so we can see what is where on booting.

---

### Post by sciro16v on 2021-11-04
> **oldfred said:**
> You need to click on the Boot-Repair link from your Ubuntu live installer in live mode.

I don't know what "Ubuntu live installer" is. If I google that, I get results regarding ubuntu server. :confused:

> **oldfred said:**
> 
Then follow the instructions using ppa to install it:
2nd option : install Boot-Repair in Ubuntu


Yes but this didn't work.

[https://www.dropbox.com/s/gkr0ny4dtt..._7245.JPG?dl=0](https://www.dropbox.com/s/gkr0ny4dtt..._7245.JPG?dl=0)

---

### Post by oldfred on 2021-11-04
There are live installers now for server where there did not used to be. Google's second line for me is the Desktop version.
If you have installed Ubuntu, the installer you used also has a live mode. 

You need to boot the Ubuntu USB installer you used to install system.
If errors, you may have modified it, and then just need to recreate it.

---

### Post by tea for one on 2021-11-05
> **sciro16v said:**
>  Unfortunately I am not able to manage installing boot-repair.
[https://www.dropbox.com/s/gkr0ny4dtt64ty4/IMG_7245.JPG?dl=0](https://www.dropbox.com/s/gkr0ny4dtt64ty4/IMG_7245.JPG?dl=0)

Regrettably, there does not seem to be a boot-repair package available for Ubuntu 21.10.
However, you can use the Ubuntu 21.10 installation media and change the repository to download the previous Hirsute version of boot-repair.
It's a bit fiddly but here we go:-

Boot into a live session using Ubuntu 21.10 installation media.
Open a terminal and enter
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
```
```
cd /etc/apt/sources.list.d
```
```
sudo nano yannubuntu-ubuntu-boot-repair-impish.list
```
You should see the following text
```
deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ [COLOR="#FF0000"]impish[/COLOR] main
# deb-src http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ impish main
```
Change [COLOR="#FF0000"]impish[/COLOR] to [COLOR="#0000FF"]hirsute [/COLOR]
```
deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ [COLOR="#0000FF"]hirsute[/COLOR] main
```
Save the file with Ctrl O and exit with Ctrl X
```
sudo apt update
```
```
sudo apt install -y boot-repair
```
Boot-repair from the Hirsute repo should now be installed in your live session.
To run boot-repair via terminal
```
boot-repair
```

---

### Post by oldfred on 2021-11-05
Boot-Repair is only available for current versions of Ubuntu. But it looks like 21.10 not yet available.
I normally suggest using ppa with Ubuntu live mode as it often is updated more frequently.

But you can download the Boot-Repair ISO and create a bootable version.
[https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/)
[https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

---

