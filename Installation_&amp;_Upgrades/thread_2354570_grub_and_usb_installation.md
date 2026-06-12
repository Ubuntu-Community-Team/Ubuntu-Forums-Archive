---
title: "grub and usb installation"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by mefuzion on 2017-03-04
hello there

i am new to these forums, in need of some guidance, after days of googling i am frustrated on the specific installation i want to do! 

i have a business laptop with windows 10 and efi boot (elitebook 1040 g3) on which i want to run ubuntu for personal use, as the windows os is full of logging stuff for the company. the bios is also locked but i dont care.

i created a live usb and i have a second usb drive i want to install ubuntu on, BUT i want it to run only when i plug it and select boot from usb in bios boot menu...

so far i tried the following:

-installed by selecting "something else"
-installed ubuntu then on sdb, with boot loader on sdb or sdb1 (made no difference for me)
- aefi entry was created always, that was deleted when i tried to change boot order from windows or linux with efi editors. anyway i didnt want it there.
- without the efi entry, the boot from usb did nothing and continued to boot in windows10

today i started digging into the grub2 on the usb i installed on the ubuntu, from the live usb ubuntu... but the files on the usb installed were read only, and also i have no idea on what to change.

i simply want to boot from this usb that i have ubuntu installed on, when i have it on the laptop, without any efi entries or something to indicate i have ubuntu or other os on the laptop when the usb isnt there.

i read that as i install ubuntu on sdb (as there is an sda there) the grub configures boot for sdb and it doesnt boot by itself?

anyway i am lost there. any help appreciated

edit-- to add another description to what i want to achieve, i want to have something exactly like the live usb (select to boot from it when i want from bios boot menu) but having a normal ubuntu installation there and not a live version... closest i got was a live usb with persistence, but thats not enough :)

---

### Post by sudodus on 2017-03-04
Welcome to the Ubuntu Forums :-)

1. A persistent live system with a ***partition*** for persistence (not only a 4 GB file) might be enough for you.

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

2a. Another alternative is to have an installed system. You can do it yourself, if you [can] remove the internal drive from the elitebook. 

2b. Otherwise the EFI partition in the internal drive with be used (and tampered with). If you cannot remove the internal drive, you can use a compressed image file with an already prepared installed system, that you can clone to your USB drive.

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

3. It makes a big difference if you have a fast USB 3 pendrive, not an average one.

[help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

---

### Post by mefuzion on 2017-03-04
i like the idea of removing the internal drive and install. i can do that.

what will happen to the system then? it will see the usb (which yes is a usb3) as sda and install there, and when i plug the  laptop drive and remove the usb it will work normally like nothing happened?

i might test that but i need to do some reading on uefi. i dont want something to happen to the windows boot at all.

---

### Post by sudodus on 2017-03-04
> **mefuzion said:**
> i like the idea of removing the internal drive and install. i can do that.
:-)> 
what will happen to the system then? it will see the usb (which yes is a usb3) as sda and install there, and when i plug the  laptop drive and remove the usb it will work normally like nothing happened?
Yes> 
i might test that but i need to do some reading on uefi. i dont want something to happen to the windows boot at all.
What you do, when the internal drive is removed cannot damage the internal drive. You can enter the UEFI/BIOS menus and change things, but I don't think you need that, as long as you can boot into your USB drive via a hotkey to get a temporary boot menu.

If you must change some setting in the UEFI/BIOS menus, you should make a note of it, and store it where you are likely to find it, if you have to reset that setting later on.

---

### Post by mefuzion on 2017-03-04
ok thanks for the advice. i dont have access to the bios settings anyway, so i guess i am ok. i will try today and report.

---

### Post by mefuzion on 2017-03-04
so i removed the drive, installed from live usb to a usb3, used "something else" to partition, doesnt boot :@@@@

i am trying again using default erase everything and install ubuntu now.

the only good news - i put the ssd in and it boots to windows directly. logical but you never know. lets see

---

### Post by sudodus on 2017-03-04
What happened? What do you mean by doesn't boot? Please describe with as many details as possible, because it makes it easier to help you.

It will also help if specify the computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Can you test booting from the USB drive in another computer?

-o-

Which version of Ubuntu did you install (16.04.2 LTS or some other version)? Maybe you should try

1. 16.04.1 LTS from [http://old-releases.ubuntu.com/releases/xenial/](http://old-releases.ubuntu.com/releases/xenial/), or

2. a persistent live system via mkusb

3. an UEFI and BIOS installed system based on 16.04.1 LTS

See the links from post #2.

---

### Post by mefuzion on 2017-03-04
well things are weird. thanks for all the help btw.

i installed ubuntu (the LTS version that shows on the website without searching much) without the ssd on the laptop using defaults this time on installer (delete drive and install ubuntu...)

finished, shut down, removed the live usb, it booted nicely on ubuntu from the usb drive! i logged in, etc normally. i say ok that was it.

i put the ssd back on without the usb. boots to windows directly, so far so good.

and finally i plug the usb back in, press f9 for boot menu, select the usb, NO BOOT. goes back to bios select option, and has the windows boot on top of the list and boots only there. wtf??? is this efi on the ssd taking so much control over boot?

the laptop is an elitebook 1040 g3, i7 6600, 16gb ram, 256gb ssd, intel graphics card on the cpu, wifi i dont remember but it is working on ubuntu live. everything is normal also on ubuntu live no problems there.

i might settle for the persistent live usb in the end but i want to try this freaking simple thing there must be a way!!

---

### Post by sudodus on 2017-03-04
Some HP computers will not boot from USB, if the there is a GUID partition table, but will boot if there is an old style MSDOS partition table. This *might* be your problem.

If you make a persistent live drive with mkusb, select msdos partition table in the settings menu. See the attached screenshot.

---

### Post by mefuzion on 2017-03-04
ok. thing is it boots from the live usb normally whether i have the ssd on the laptop or not. does the live usb have an msdos partition table then? oh well.

---

### Post by oldfred on 2017-03-04
Even a standard install in UEFI mode will not directly boot from an external drive.
Grub installs to /EFI/ubuntu.
UEFI only boots external drives from /EFI/Boot/bootx64.efi. (different grub configuration, but same file name as installer and also Windows installer's file name).

So you should be able to copy /EFI/ubuntu files into /EFI/Boot and rename shimx64.efi to bootx64.efi. Both /EFI/Boot & /EFI/ubuntu are required as the full install version of grub expects more files in /EFI/ubuntu folder.

For may full installs to a flash drive, I normally copy files from internal drive, since my internal drive is booting Ubuntu I have to back up /EFI/ubuntu as it gets overwritten. So I then restore my backup & edit fstab while in live mode, before even rebooting after install to flash drive.

You also need to edit fstab with ESP - efi system partition on flash drive instead of UUID from internal drive's ESP.

 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad
And Ubuntu's UEFI grub only installs to the ESP on sda, or not the external drive and not to /EFI/Boot/bootx64.efi. For my PC UEFI full install to a flash drive I manually copied /EFI/ubuntu on sda's ESP to flash drive's ESP. Then copied it again to /EFI/Boot and renamed shimx64.efi to bootx64.efi. I then updated fstab to have correct UUID for ESP on external drive.

---

### Post by sudodus on 2017-03-04
> **mefuzion said:**
> ok. thing is it boots from the live usb normally whether i have the ssd on the laptop or not. does the live usb have an msdos partition table then? oh well.

In some cases, yes, in other cases there is an ISO 9660 partition/file system, which is used also in CD/DVD disks.

---

### Post by mefuzion on 2017-03-04
***here's a short evening story for all the people here who helped.***

i read the rest of the replies, with emphasis to oldfred's one, AND the link (wow), and then as i was tired enough with all this, i gave up. i also have a 1.5 YO kid here. you know...

kid's in bed so i start downloading LiLi on my windows 10 desktop, to start the process of creating a live usb with persistence, as this was my last resort.... i plug the usb (the one with ubuntu installed but never booted) to the win10 desktop, it shows the regular "the disk needs to be formatted bla bla..." BUT then it opens a drive with EFI folder inside... and ubuntu inside that...
 
i start to remember things "copy ubuntu to -boot-, rename files..." from oldfred. so i say what the heck i ll try something noobish. copied all the contents of ubuntu folder on a new Boot folder, and renamed shimx64.efi to bootx64.efi. GUESS WHAT. to my surprise, i put the usb in the laptop, hit f9, select usb to boot, purple ubuntu screen.... it booted... removed the drive restarted, windows 10 no problem. put the usb again and selected to boot, booted!!!!

i got lucky i think...

thanks everyone. great forum support i may say!

---

