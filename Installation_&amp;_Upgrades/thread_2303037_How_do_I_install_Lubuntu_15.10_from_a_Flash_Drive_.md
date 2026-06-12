---
title: "How do I install Lubuntu 15.10 from a Flash Drive to a Hard Drive?"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2015-11-15
Is there a simple way to install Lubuntu 15.10 utilizing a Flash Drive and then installing it to a Hard Drive?

Do i simply download the .ISO to a Flash Drive, let's say, at the Library (the Library has a really fast connection) and then when I get home make sure the BIOS is set to boot from the Flash Drive? Or do I have to format the Flash Drive in a certain way so that the OS will install to the Hard Drive from the Flash Drive? I am not doing a dual boot. Lubuntu will be on a separate computer.

To do this will be a lot easier for me, considering that the Library does not have a way to burn to a DVD and the size of the OS is too large to fit on a CD.

Any assistance would be greatly appreciated!

Thank you!

---

### Post by oldfred on 2015-11-15
Most have to use software to extract ISO, format flash drive, copy files to flash drive and convert it to a bootable device.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[URL="http://www.ubuntu.com/desktop/get-ubuntu/download"]http://www.ubuntu.com/desktop/get-ubuntu/download
[/URL]
 Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[URL="http://rufus.akeo.ie/"]http://rufus.akeo.ie/
      [/URL]
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

Generally better to have Internet connection when you install. You may need to download extra drivers of additional software.

Some of this is now really old, and I think it may have changed:

 [http://askubuntu.com/questions/168352/how-do-i-generate-a-package-download-list](http://askubuntu.com/questions/168352/how-do-i-generate-a-package-download-list)
[http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline/129543#129543](http://askubuntu.com/questions/974/how-can-i-install-software-or-packages-without-internet-offline/129543#129543)
 The .deb files are stored in /var/cache/apt/archives
[https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/](https://cortman.wordpress.com/2012/07/08/download-packages-with-windows/)
Apt-offline in repository for offline updates
[http://www.debian-administration.org/article/648/Offline_Package_Management_for_APT](http://www.debian-administration.org/article/648/Offline_Package_Management_for_APT)
Setting up your own APT repository with upload support - 2005
[http://www.debian-administration.org/articles/286](http://www.debian-administration.org/articles/286)
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository)         [ ]("http://rufus.akeo.ie/")  [ ]("http://www.ubuntu.com/desktop/get-ubuntu/download")

---

### Post by Vladlenin5000 on 2015-11-15
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

Doing your homework, i.e., a simple Google search would give this results and a few more...

---

### Post by roler2 on 2015-11-15
@Vlad-

I didn't post to be criticized. I don't have a Ubuntu installation, so option #1 is not applicable. I will not be running Lubuntu from a USB stick so option #2 is not applicable. I don't have a Mac so option #3 is not applicable.

@oldfred-Thank you!

I posted because I thought maybe a Member had already performed a transfer from a Flash Drive formatted on a Windows computer to installing Lubuntu or Ubuntu on another Hard Drive on a completely different Computer and could guide me so I don't mess up. I got really confused when I did a Google search and it appeared to me that the process is a lot more difficult than my limited skills will allow. Vlad-you may be an expert. I am not. And that is why I posted for help.

I have to use my Windows Computer to format the Flash Drive so as to make it bootable. I have to go to the Library to download the ISO. So I will be going from formatting the Flash Drive from a Windows computer and installing Lubuntu on a completely different computer. It might not work. I don't know. I am not that skilled. I don't have a fast Cable connection. I have 768 DSL because that is all my Apt. Complex will allow as the wiring is at least 15 years old and the Landlord doesn't want to upgrade because it costs too much money.

---

### Post by Vladlenin5000 on 2015-11-16
> **roler2 said:**
> I will not be running Lubuntu from a USB stick so option #2 is not applicable.

It is actually. All 3 options give the same result, you just need different software for different OSs. However, considering you will be doing it in Windows then I second oldfred's other options/tools: **Rufus** and **Unetbootin**. Rufus is often recommended.

> I posted because I thought maybe a Member had already performed a  transfer from a Flash Drive formatted on a Windows computer to  installing Lubuntu or Ubuntu on another Hard Drive on a completely  different Computer and could guide me so I don't mess up.

Many did, of course, and those were/are mostly non-experts. Real experts tend to have Ubuntu or some other Linux already :-) therefore they'll be using Ubuntu/Linux tools
The links provided - forget about other OSs and focus on Windows instructions - should be enough as a guide. Please read and feel free to post any question you may have regarding the instructions / something you don't understand / any other question ...

---

### Post by sudodus on 2015-11-16
***Please tell us details about your computer,***

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- what Windows version you are running
- if you are running the computer in UEFI or BIOS mode.

All these things make a difference, and some advice details depend on your answer. It can even make a difference of which iso file to download.

-o-

Here is a general outline of the steps from getting the iso file to an installed Lubuntu system.

1. ***Download*** the Lubuntu iso file to the pendrive at the library.

2. Download and install the Windows program ***md5summer*** (if you can at the library, otherwise at home). Check the ***md5sum*** with md5summer in Windows, that the download was successful, that the md5sum matches the listed value.

3. ***Copy*** the Lubuntu iso file to the hard disk drive in your Windows computer.

4. Download and install a tool to create a USB boot drive. ***Rufus*** and ***Unetbootin*** have been recommended, and I think both are good tools.

5. Check that you have a ***FAT32*** partition file system on the USB pendrive.

6. ***Delete all files*** from the USB pendrive.

7. Use Rufus or Unetbootin to ***create a USB boot drive*** with Lubuntu from the iso file.

-o-

8. ***Check how to boot from USB***. See this link

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

9. ***Boot from USB***. I suggest that you [try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

10. ***Finally install*** Lubuntu, if you are happy with how it works 'live' booted from the pendrive :-)

---

### Post by grahammechanical on 2015-11-16
Do library administrators allow anyone to download files on to library machines? Well, I never knew that. If using the library machine's browser to download the ISO image the browser's default download location will have to be changed to point to the USB memory stick which will need to be formatted in Windows to FAT32. Otherwise, you will need to find the ISO image and the use a File manager to cut (move and delete at the same time) the ISO image on to the USB stick.

Regards.

---

### Post by roler2 on 2015-11-18
Thank you all so very very much for all the great advice! Really. . .I do mean it. . .Thank You!

The Library installed a Cloud-based Windows System. . .I am not sure what it is I think it is a Server System of some sort. . .so yes it is allowing to download files (well. . .the files they will allow anyway) on the actual Cloud-based Desktop. It is very fast actually. I also am going to use Rufus as that appears easy to use and I will be able to do that at the Library as well. I already have formatted the never-used Flash Drive as FAT32. Then I will try and install at home. My Computer is very old P4 that still runs really good and I think I am able to boot to the Flash Drive. . .I think. . .have never tried this so I really appreciate all the advice and guidance. . .Thank you again!

---

### Post by sudodus on 2015-11-18
Good luck :-)

---

