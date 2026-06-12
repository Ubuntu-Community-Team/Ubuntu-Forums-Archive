---
title: "Lubuntu 13.10 Installer does not detect Windows 7 or any partitions &amp; black screen du"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by harrington.james.j on 2013-12-01
[COLOR=#333333][FONT=UbuntuRegular]I know this question has been asked numerous times and has been answered;[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://ubuntuforums.org/showthread.php?t=1604074&page=4&p=10022223#post10022223](http://ubuntuforums.org/showthread.php?t=1604074&page=4&p=10022223#post10022223)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][Why doesn't Ubuntu 12.04 recognize my Windows 7 partition?]("http://askubuntu.com/questions/265132/why-doesnt-ubuntu-12-04-recognize-my-windows-7-partition")[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular](these are just a couple of the articles/threads I have read) however none of the solutions provided seem to solve my problem.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have a Samsung ATIV Book 9 Lite with a 128GB SSD with Windows 7 64-bit installed. I created an unformatted partition where I intended to install Lubuntu to.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I then created a USB boot disk using unetbootin, now when I boot to this and hit 'install Lubuntu' the Lubuntu splash screen appears and then the screen simply goes blank. I got round this by changing the settings to 'nomodeset' which then take me to the standard Lubuntu install/setup. However the installer does not detect my windows 7 OS or the partition I created and sees the SSD as just one partition.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have tried clearing any RAID data - I have read that this can cause issues, and tried using sgdisk/gdisk to 'zap' the partition however the installer still cannot see windows 7 or the partition.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The strange thing is I used the exact same USB to install to my PC which had no problem with a black screen or detecting my windows 7 installation. The only difference being that I have multiple HDD so installed Lubuntu to a HDD of its own (no partition nonsense - except for the swap area).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any help you guys can give me would be appreciated as I am out of ideas.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]QP[/FONT][/COLOR]

---

### Post by oldfred on 2013-12-02
Most Windows 7 systems are installed in BIOS boot mode, a few are UEFI. Which is yours?
Post this and from partitions we can tell.
sudo parted -l

Often Windows 7 in BIOS mode uses all 4 primary partitions.
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

