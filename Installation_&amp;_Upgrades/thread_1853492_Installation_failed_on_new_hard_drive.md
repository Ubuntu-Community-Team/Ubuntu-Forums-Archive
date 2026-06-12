---
title: "Installation failed on new hard drive"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by fizdup on 2011-10-02
Attempting to install xubuntu 11.04 on a relatively old ASUS laptop.
I made a USB boot disc, and it works fine on the live boot (I am using it to post this) but when I attempt to install, I get a dialogue box that says 

"the attempt to mount a file system with type ext4 in SCSI4 (0,0,0), partition #1 (sda) at / failed" 

That message is preceded by an audible click from the hard drive.

This is on a nrand new hard drive that I purchased today. 

Is my laptop eating hard drives?

---

### Post by oldfred on 2011-10-02
I never like clicks from hard drives.

Does BIOS show drive ok? It does seem that system sees drive since it tries partition #1.

Have you tried partitioning in advance and then using manual install. It may tell a bit more if gparted has errors on formating. 

Does Disk Utility show a green status under Smart Status?

---

### Post by fizdup on 2011-10-03
I am new at this, so I may not understand your questions. But here goes (and thanks for asking them!)

When booting up, I hold esc to enter the boot menu. My hard drive shows up there, but I select USB, and enter live boot. So the BIOS can at least detect that there is a hard drive there.

In attempting to install, I went to the screen where it lets me choose partitions and tried messing about with them - I know very little about what I am doing. I essentially attempted to create an unused partition at the start of the drive, so if there was an error on the hard drive it would install in an area that was uncorrupted. Still no dice.

One thing occurs to me: I am writing my boot sticks on a very old windows laptop. It is reading the .iso off an external harddrive and writing it to the usb stick. Could the USB installer be corrupted but still allow the live boot to work?

Thanks again for taking the time.

---

### Post by oldfred on 2011-10-03
If the liveCD works that is a good sign. You can check that your ISO is correct with md5sum:

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I do not use Windows installer so I am not sure the boot screens you get now. Do you have a choice on check install. CDs have that as an option in the menu which helps to verify that CD was correct.

There have been some issues with BIOS, flash drives and versions of installers. Some combinations just do not seem to work together or some users at least are not able to make them work. I have not had an issue.

Sometimes just a different USB installer works better.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by gordintoronto on 2011-10-03
If the live boot works, open Accessories/Terminal and run gparted. You might have to change what drive it's looking at, but then you should be able to create partitions and format them on the hard drive.

Note that nothing happens with Gparted until you click on Apply.

---

### Post by fizdup on 2011-10-05
So, I used the live boot with an old hard drive, used gparted to completely erase it, then tried the install and it worked!

Thanks for all your help.

---

