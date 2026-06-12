---
title: "Ubuntu 1604 full encryption : how to boot from usb to reinstall or reformat"
date: 2016-06-25
forum: Installation &amp; Upgrades
---

### Post by iscandarster on 2016-06-25
Just installed ubuntu 16.04 with full encryption (with a passphrase I can access) on a laptop with only usb and wifi. The disk is a SSD welded. Looking with gparted how the disk has been set up, there is no swap and 3 partitions : /dev/sda1 /boot/efi fat 32, /dev/sda2 /boot ext2, and /dev/sda3 crypt-luks . I can't boot from a usb cause the boot setup doesn't give me the possibility to do so (or I don't know how). I wonder if I format /dev/sda3 to ext4, the system will allow me to reinstall it ? Or do I need to do something else ? Got a backup of the data so I don't care to reformat every thing. The only thing is I don't want to have a brick ! 
Any advice ? I have searched internet for that but haven't found not even a clue

---

### Post by Geoffrey_Arndt on 2016-06-25
Worth a shot.   But, you should have a swap, and you don't need a boot partition (I've never used one, but I also have never run on a UEFI system).   Anyway, convert the boot to swap if it's big enough, try reformatting to ext4 sda3, and see if you can find in the uefi firmware how to change the boot order (often there is also a 1 time boot key-combo).    If you can find that, a reinstall is in order.   Remember, you can also use a portable USB dvd drive if you can't get the system to boot from USB.   I use one from Amazon (Amazon Basics . . ) and it works great for booting or watching movies, etc.   Also wouldn't hurt to get a copy of Parted Magic and/or Dariks Nuke & Boot.

BTW, almost all newbies make  a common mistake with their first post or two on Ubuntu Forums.   They don't include the detailed specs of their system.   Maybe a reader has your make and model and can reply with . . . "this is how to change boot order" etc.

---

### Post by oldfred on 2016-06-25
To use full drive encryption, you have LVM which is logical partitions inside the physical partition. And you have / & swap inside the one partition you see with gparted.
LVM is also normally configured with a separate /boot partition, but that and perhaps some server type installs or RAID may be the only other time you need a separate /boot. Better to have separate /home or a /mnt/data partition to separate operating system from most data.

If UEFI system you do need the ESP - efi system partition which is FAT32 formatted with the boot flag.

How you boot install media UEFI or BIOS/CSM is then how it installs. So if system is UEFI hardware better to boot installer in UEFI mode and have hard drive set to boot in same UEFI mode.

See also link below for more UEFI info:

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

---

### Post by iscandarster on 2016-06-26
Thx guys for helping me out. The thing is I can't boot but on my encrypted ubuntu partition. All the parameters where chosen automatically with the ubuntu install process. And I don't know much about UEFI, legacy, Grub, etc. 

Here are more details about my system and the installation : I have a Asus Zenbook UX305LA with 8G RAM 250 SSD and i7-5500U CPU. The boot setup is AMI Aptio Setup Uitility v2.17.1249. I bought the laptop with windows on it and I installed ubuntu 16.04 from USB with the downloadable .iso. And it was straight, every thing worked fine. When I rebooted the first time, after the initial screen asking for the password (because it's full encryption), every thing was working great. Just the wifi took some time to setup but once I get it right it's really reliable. So am really happy with my buy and with ubuntu. The only thing is I shouldn't have chosen to encrypt all the file system. 
 
Below is a few shots of the boot menu showing different options : 

The first pic shows I have only one possibility : to boot on the encrypted ubuntu (2 identical choices)
[ATTACH=CONFIG]269786[/ATTACH]

This one is the security top menu
[ATTACH=CONFIG]269789[/ATTACH]

This one once entered in the secure boot menu
[ATTACH=CONFIG]269787[/ATTACH]

This one in the key management option
[ATTACH=CONFIG]269788[/ATTACH]

Does it shows you a possibility to disable the encryption or an option to solve my problem ?

If there is 3 partitions maybe because there was windows on it first. Next pic is the partitions from gparted. 
[ATTACH=CONFIG]269790[/ATTACH]

@ [COLOR=#000000]Geoffrey : I can install soft from internet but it I do that and I wipe out my disk, will it solve my problem or make it worst ? And really have for now no option for booting anything from usb. 

[/COLOR]@ [COLOR=#000000]oldfred : With these pic of boot setup, can you see an explanation or a solution ? What if I delete the all the secure boot variables ? Has it something to do with my encryption problem, or the only choice I have to boot on my encrypted ubuntu ? [/COLOR]

---

### Post by oldfred on 2016-06-26
Do not change anything related to keys.
Ubuntu uses the default Microsoft key and that just works. But many of us just turn off secure boot.

With Secure boot on, you may not be able to boot USB flash drive. Many UEFI consider that insecure. But you should somewhere then have a setting allow USB boot. But may need secure boot off to see it or a supervisory password in UEFI. If you set a UEFI password, never forget it or you may brick system, or reset to no password after changes.

Often best to turn off the UEFI fast boot setting, at least until fully reconfigured. UEFI then assumes all hardware & settings are identical and skips checks for changes & boots very fast. Usually so fast you do not even have time to get into UEFI to make changes with UEFI key like del or f2.

The two choices ubuntu are not identical. One is shimx64.efi and the other grubx64.efi. Shim is the version of grub for UEFI secure boot. If Secure boot is on, only the shim entry should work. But even with secure boot off the shim entry still works, so do not know why two?
To see details of which is which:
sudo efibootmgr -v

So turn off fast boot, turn off Secure boot and see if somewhere you then have an option to boot USB. If not try setting UEFI password and see if you get new options.

Asus uses Aptio across many models, with different options/setting, but often otherwise very similar.
Did you have to use the pci=nomsi setting? Many recent posts from newer Asus needed that setting to be able to boot and to prevent run-away log files(errors fill drive).
Do you have newest Aptio UEFI from Asus for your model? But that resets all settings to defaults. My old BIOS systems I had to take screenshots with camera to remember them. New UEFI system gives me list of changes before I save them, which I then copy. It also does screen shots.

 Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570) 

        UEFI may have setting that is Windows 8 or Windows 7, which probably is to turn off secure boot
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)

---

### Post by banceu_sergiu_ione on 2016-06-26
On your first SS, I can see you still have to disable the fast boot. Then a bit down you have the option ' Add New Boot Option ' access it and add USB boot option then move it on top to other options.I don't have the same UEFI so i can not tell what will pop up and how to set it when you go for 'Add New Boot Option ', but that should be how to get an USB bootable option up. Leave secure boot enable, ubuntu key must work.

If you get it, then you can simply run a USB live boot and reinstall all if you said you not need to back up the data you already have. If all go good, you can the install it as like.

I suggest you get the most easy install without LVM and crypt. You can add them after if want. If you really want you can encrypt just 1 folder and more even hide it, if you really have special information and you are afraid of a leak.

---

### Post by Geoffrey_Arndt on 2016-06-26
Methinks the OP now has more than enough info to solve the issue of usb bootup AND how to resinstall Ubuntu.   But, this would be a great learning thread if the final result and solution is posted.    I know I've already saved this thread for future reference, so, the resolution would make it better yet.   Great input re posts #5 & 6 . . .

---

### Post by iscandarster on 2016-06-26
Seeing the light at the end of the tunnel and hope it's not headlights of a car :)

Typing [COLOR=#000000]sudo efibootmgr -v get me the 2 different options shimx64 and grubx64 :
[/COLOR]BootCurrent: 0006Timeout: 1 seconds
BootOrder: 0006,0005
Boot0005* ubuntu    HD(1,GPT,7628d728-0244-4e69-a44c-ef047d7cb644,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0006* ubuntu    HD(1,GPT,7628d728-0244-4e69-a44c-ef047d7cb644,0x800,0x100000)/File(\EFI\UBUNTU\GRUBX64.EFI)..BO

But no difference when I boot on one or on the other.


So I disable fast boot and now can see grub2 menu at startup with 3 choice : ubuntu, special options for ubuntu, and boot setup (haven"t put the pic because only 5 pic/post)

And if I type "e" I can see the code with a possibility maybe to modify it and then launch it, or to go to command line with "c". At this point I really don't know what to do.
[ATTACH=CONFIG]269799[/ATTACH]

On the row I also disabled the secure boot but nothing seem changed.

Then I tried to go for "add a new option" and bellow are the different steps :
At first I have only one choice :
[ATTACH=CONFIG]269800[/ATTACH]
So there :
[ATTACH=CONFIG]269801[/ATTACH]
There
[ATTACH=CONFIG]269802[/ATTACH]

And then there with 4 options MokManager.efi, shimx64.efi, grubx64.efi, fwupx64.efi and dir fw with nothing in it :
[ATTACH=CONFIG]269804[/ATTACH]

I tried all of them but with almost no difference I always go back to the grub 2 menu with 3 choices : ubuntu, special ubuntu, and boot menu. 

So there, it seems to me there are a few things that I could try but first :


[LIST]
[*]What does mean "[COLOR=#000000]pci=nomsi [/COLOR]"in my case and where would I have to type it ?
[/LIST]


[LIST]
[*]Also I could try to understand the grub script at the grub screen, and maybe there is a possibility to update it.
[*]Or do some thing at the command line ?
[*]And also as suggested I can try to install a new release of the Aptio : have seen different release on Asus web site I have to check which is mine and I could upgrade (or maybe just reset ?)
[*]And there is also the possibility to change something from inside (because at least ubuntu on my laptop is great and even with encryption it works enough fast, 8Go RAM and SSD though). Am I right that /dev/sda1 was the boot partition for windows ? Although its around 500 Mo size is there something to do with it ? Or modifying the /dev/sda2 (this one is the one used by ubuntu ?) ?
[/LIST]

Any preferred or safer direction ? 
Thanks a lot guys for your guidance

Alex

---

### Post by iscandarster on 2016-06-26
Just saw that the first pic been wiped out, so there it is : 
[ATTACH=CONFIG]269805[/ATTACH]

---

### Post by banceu_sergiu_ione on 2016-06-26
If you have a LVM PV encrypted mounting and repair grub is not as easy as you think. As for a reinstall it maybe more esy but still hard, [Check documentation]("https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity"). [Or this]("https://help.ubuntu.com/community/EncryptedFilesystems"). 
You can check that documentation and find the way for you how to get all work good. I can't help further with that because I did not used encrypted on full install or LVM. Maybe wait for someone with more experience to replay with how too.

What i can suggest is to get a new install without encrypt or LVM * you can encrypt and get LVM after you got a good and stable install *. It's also recommend that grub don't make part of encrypt/LVM because if you have any issues in future, then you can run boot-repair and repair the boot. [Boot-repair do not work with encrypt/LVM]("https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system#LVM_on_LUKS") and for that you need to do it all manually. 

In order to make that new install you have to figure out how to 1st boot from a Live USB. And you never know if you will need it in future again. So better get one issues resolve at time.

1. Boot from USB * important to get it now working, so in future if you may need it, you wont going to get this issues up again *

- turn off you pc
- plug in the Live USB ( I should had say it on previous post )
- turn on your pc and log in UEFI
- go to Add New Boot Option and search for the USB * now, you had seen all type you got from with the SSD you have, try search for the USB hardware name * 
hope you find it and you set it as 1st boot so you can even run as Try Without Install and try to fix it or you chose for a new install.

* the /dev/sda1 is not the windows partition but the EFI partition

EFI partition is created each time you made an install on a new SSD/HDD and contain all UEFI information. It interact with kernal and give all hardware information to OS in order to set the best configuration.
If you get the SSD and you do a full format of it with GParted, then install Ubuntu again, you will notice that the EFI partition will be created back. ( i have it too )

* pci=nomsi ( MSI is [Message Signaled Interrupts]("https://en.wikipedia.org/wiki/Message_Signaled_Interrupts") ) 
you will set it off with that command. if you did not get any error that lead you to it i wont change it for the moment. once your stitem is stable you may see if search that even the cpu could be related at msi module

- for now focus on how to get your pc boot from USB

---

### Post by oldfred on 2016-06-26
If you did not need the pci=nomsi before, then do not worry about it.

You should be getting USB boot options, but are only showing/seeing the hard drive boot options.

My Asus is a Asus motherboard that has more details than typical laptop.
And screenshot with Toshiba is a Toshiba flash drive that someone posted.

You may still have setting somewhere to allow USB boot.
And on my systems USB boot is under hard drive, not USB choices.

---

### Post by iscandarster on 2016-06-27
@banceu_sergiu_ione : thx for your help. With you and others, I know have a more clear of what my problem is and in which direction search.
All the best.

---

### Post by iscandarster on 2016-06-27
@oldfred :
After looking at your boot scrren looking in my boot setup if there is any other options.
 
Also having done a boot checkup with boot repair : sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update; sudo apt-get install -y boot-info && boot-info
-> [http://paste2.org/d9Bvhg8s](http://paste2.org/d9Bvhg8s) 
Does it ring a bell on what I could do to get a solution ...
Reading again older post of the thread to see if I haven't missed something ...

---

### Post by banceu_sergiu_ione on 2016-06-27
I lost same info. From beginning. How did you first installed ubuntu if you can not boot from a live USB ?

Now i would like you check this:

when you go inside bios - Add New Boot Option, the last option is 'Create'  ---- What do you find there?

If nothing, then:

I would like to ask you also if you shut down the pc, plug in the live USB, power on----What happen ?

if not boot from USB, then leave the USB plugged and go into bios. At boot options do you find any #3 ? or at Add New Boot Option , do you find anything more then without USB plugged in ?

---

### Post by iscandarster on 2016-06-27
After rereading the thread, trying to understand and follow all the explanations given and navigating in the different links, found this post : [http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/)


So I disabled CSM (Compatibility Support Module) in the boot setup for a legacy mode (or what I understand of it). Tried a few times to see if there where differences cause I have USB 2.0 and 3.0 and I thought maybe there could be differences ...
In the process a "USB option" appeared but don’t really remembered if it was really USB or but another option appeared and chosed it. Unfortunately couldn’t boot from it cause message some thing like improper device led me to a black screen asking me to put a proper device to boot on.


In the way for trying different options I entered the boot mode with ubuntu in recovery mode (from grub screen) which let me see at least the end of the process which I took a pic where we can see that the system can see my USB key San disk contour ? As scsi ??? Here is an important thing who saved me (And come back later on it). 

Here is the pic where we can see that Sandisk Cruzer has been recognized. 
[ATTACH=CONFIG]269814[/ATTACH]


After that I went to recovery mode too see if something interesting could be done. And I don't if something has...


So for writing this post I thought I have to turn back and try again to explain exactly what was my process. So went back in the boot setup and there enabled CSM boot again to take a pic of the option. And then again don't really remembered if "save and exit and reboot and back in the boot setup" or found the new boot option : USB Sandisk :))))) Which I choosed. And now I have a brand new computer with Xenial Xerius on it running perfectly. 

At the end don't know what was the exact name of that option, but succeed to reinstall the system really straight ahead :) with LVM and NO FDE
In the process I also email a guy part of Ubiquity team asking him if there could be a BIG WARNING on the difficulty to uncrypt or boot from USB at least for some configurations and newbies. And for that this maybe shouldn't jump into that option as quick as I did

Thanks all of you
All the best

Alex

---

### Post by iscandarster on 2016-06-27
Have you seen my last post ? 
For me the solution was in enabling CSM (legacy boot) option but I'm no expert so ... cannot explain why it worked like that and if it will work for you. 
What is your configuration ?

---

### Post by banceu_sergiu_ione on 2016-06-27
I'm gland you got it up to work. Mark it at solved if tis all good.

So in order to run it, you had secure boot off / fast boot off /CSM enable.

---

### Post by banceu_sergiu_ione on 2016-06-27
> **iscandarster said:**
> Have you seen my last post ? 
For me the solution was in enabling CSM (legacy boot) option but I'm no expert so ... cannot explain why it worked like that and if it will work for you. 
What is your configuration ?

Mine work good on UEFI but I have a Toshiba ( L50D-C-18X ) and the UEFI let me to get boot order as the old bios do. ( secure boot on ).

Since you run a SSD, i suggest you give a shout to same[ wiki]("https://wiki.archlinux.org/index.php/Solid_State_Drives"), for its maintenance and tuning.
My SSD is a HyperX Savage 240GB and as partition :
/dev/sd1 - EFI 537 MB
/dev/sd2 - EXT4 158GB
/dev/sd3 - swamp 17GB ( swampiness set to 30 ) ( i know is alot of, but at the moment i dont need more space. to reallocate if need )
65GB free space ( to reallocate if need )
* free space left to not add discard option and [as this article]("http://www.kingston.com/us/ssd/overprovisioning") say it improve the performance and the life of SDD.
[here are my phoronix disk test if want to see and give a shot]("https://openbenchmarking.org/result/1606246-HA-HYPERXSAV65").

---

### Post by iscandarster on 2016-06-27
Yes all three options. And also navigating in recovery mode from grub2 menu, moving USB port, trying different options, going back and forth, and doing that a couple of times on and on : Shaking it ! (Not sure it's really help ...) 
Thx for your support : alone I couldn't have done it.

---

