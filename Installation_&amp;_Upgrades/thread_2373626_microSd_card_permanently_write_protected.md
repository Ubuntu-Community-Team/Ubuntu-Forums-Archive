---
title: "microSd card permanently write protected?"
date: 2017-10-08
forum: Installation &amp; Upgrades
---

### Post by mrbawse on 2017-10-08
I have a 2x rasp 3's both using  32GB Lexar micro SD cards as the main storage for the Ubuntu Mate OS.  After running them for a few months now doing various projects with each unit.  I'd like to start from scratch and format and re-install the Ubuntu OS on both of them.  I popped the sd cards into my win10 machine and tried to format the cards using windows drive tools.  It gave me a cannot format card is write protected error.  I checked the switch on the side of the micro to SD adapter and it was in the write position. Tried a partitioning app to format the card, still gave me an error that its write protected...what?  I even popped them into my smart phone and tried to get android to format it and even the phone said it couldn't complete the format. I've never encountered this before...anyone seen this?


Thanks

---

### Post by jglen4902 on 2017-10-08
What partitioning app were you using?

I've seen errors on SD cards and usually an error flag is set on the file system due to a bad write or incomplete write.  Sometimes all it takes is opening the card under something like gparted, unmounting the card in gparted, and fixing some of the flags set on the card or reformatting and partitioning within gparted.  At the worst, hit the card with a hammer and sweep the pieces into a trash can.  I had to do that on a 64GB card recently, but I've had good luck fixing others within gparted.

---

### Post by mrbawse on 2017-10-08
Thanks. I was using Ease US Partition Manager. Never heard of gparted

---

### Post by Frogs Hair on 2017-10-08
For Windows, the noobs tutorial for Rpi recommends the following. I've not tried with Ubuntu. 

  [https://www.sdcard.org/downloads/formatter_4/](https://www.sdcard.org/downloads/formatter_4/)

---

### Post by mrbawse on 2017-10-08
> **Frogs Hair said:**
> For Windows, the noobs tutorial for Rpi recommends the following. I've not tried with Ubuntu. 

  [https://www.sdcard.org/downloads/formatter_4/](https://www.sdcard.org/downloads/formatter_4/)

I booted into a Live ubuntu OS from a flash key and used the built it Gparted partitioning tool. And no go still gives me an error when trying to delete the partitions.  I also gave that sdcard formatter app you posted up a try and it too says write protected.  I posted this up on the RaspPi forums and apparently this is a common problem with the Pi eating SD cards and not allowing them to be formatted again.  Nobody has a definitive answer as to why this happens but I have two 32GB lexar cards that are now bricked after only 5 months of use.

---

### Post by Frogs Hair on 2017-10-08
I reinstalled recently due to Raspian dist upgrade which would be the third installation of an OS. Thanks for the warning.

---

### Post by sudodus on 2017-10-10
You can try according to the analysis and tips in the following link,

[**Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem**](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

- **Let us hope that there is 'only' confusion** - Try to restore the drive to a standard storage device

- **What to do if mkusb fails** - If mkusb fails, the drive is either not found by the system or read-only. In this case you should try according to the following list.

-    On some pendrives and on many memory cards there is a small mechanical switch for write protection, that can toggle between read/write and read-only. You might have set it read-only without intention.

-    Reboot the computer and try again to restore or wipe the first megabyte with mkusb.

-    Disconnect other USB devices. Sometimes USB devices can disturb the function for each other.

-    Try other USB ports and another computer.

-    Try another operating system (Windows, MacOS) in another computer.

-    If you still cannot wipe the first megabyte of the drive, and the drive is read-only, it is probably 'gridlocked', and the next stage is that it will be completely 'bricked'. There is a limit, when you have to accept that the pendrive is damaged beyond repair, at least with tools available to normal users like you and me. See this link: [Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

[hr][/hr]
**How to install mkusb**

If you run standard Ubuntu, you may need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi

---

### Post by mrbawse on 2017-10-10
> **sudodus said:**
> You can try according to the analysis and tips in the following link,

[**Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem**]("https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035")

- **Let us hope that there is 'only' confusion** - Try to restore the drive to a standard storage device

- **What to do if mkusb fails** - If mkusb fails, the drive is either not found by the system or read-only. In this case you should try according to the following list.

-    On some pendrives and on many memory cards there is a small mechanical switch for write protection, that can toggle between read/write and read-only. You might have set it read-only without intention.

-    Reboot the computer and try again to restore or wipe the first megabyte with mkusb.

-    Disconnect other USB devices. Sometimes USB devices can disturb the function for each other.

-    Try other USB ports and another computer.

-    Try another operating system (Windows, MacOS) in another computer.

-    If you still cannot wipe the first megabyte of the drive, and the drive is read-only, it is probably 'gridlocked', and the next stage is that it will be completely 'bricked'. There is a limit, when you have to accept that the pendrive is damaged beyond repair, at least with tools available to normal users like you and me. See this link: [Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[HR][/HR]
**How to install mkusb**

If you run standard Ubuntu, you may need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi

Thanks for that


[B]On some pendrives and on many memory cards there is a small mechanical switch for write protection, that can toggle between read/write and read-only. You might have set it read-only without intention.

[/B]Thanks this was the first and obvious solution I looked at.  I even tried several different adapters and it could only be read.

[B]Reboot the computer and try again to restore or wipe the first megabyte with mkusb.

[/B]Tried this as well. Nope 

[B]Disconnect other USB devices. Sometimes USB devices can disturb the function for each other.

[/B]Performed this while reading the caard in my laptops built in sd card reader. Used an external usb reader on my desktop, and also tried on an android tablet. Nothing changes.

[B]Try other USB ports and another computer.

[/B]Nope

[B]Try another operating system (Windows, MacOS) in another computer.


[/B]Attempted to fix on a windows laptop/desktop, ubuntu Live boot, and on an Android tablet. Same outcome...permanently write protected...and that's with two fairly new cards.

For anyone running Ubuntu mate on a rasp3. Try the change boot method to sda2 (forces Rasp3 to boot from USB device instead of card slot). Using an SSD connected through a SATA to USB adapter.  Machine runs faster and is more stable.  Better solution than continually going through sd cards as these can only handle so much read  and write for a limited amount of time in an OS environment.

---

### Post by sudodus on 2017-10-10
I agree that an SSD via USB is a better solution (but more expensive at least in the short term). It is possible to boot via a boot partition in the card slot and with the root partition in the SSD (that's where there will be a lot of write operations).

---

