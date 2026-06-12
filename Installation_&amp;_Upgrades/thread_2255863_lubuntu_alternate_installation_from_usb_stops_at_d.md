---
title: "lubuntu alternate installation from usb stops at detecting cdrom"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by legendaryman on 2014-12-08
lubuntu alternate installation from usb stops at detecting cdrom and after that it says cd rom detection fails check the disk and  guys i cant use my cd to install as dont have cd rom drive 
my pc has 512mb ram ,,,p4 3.19 ghz and tell how to install it through usb

---

### Post by sudodus on 2014-12-08
Pentium 4 and 512 MB RAM should work with Lubuntu, even if the performance will be slow. It is easier to help if you also tell us about the graphics chip and wifi chip.

Please tell us which version of Lubuntu you are trying to install and which tool you use to make a USB boot drive!

- Maybe you need another version of Lubuntu
- Maybe you need to make the computer boot from the USB instead of the CD drive
- Maybe you need another tool

See this link and links from it for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by legendaryman on 2014-12-08
lubuntu-14.10-alternate-i386.iso this is exactly the version and also note that i have tried several software to make it bootable like unetbootin ,lili , 
**Linux Live Usb Creator,win32 disk image,using cigwin dd command**

 and several others but result is same ...and i can surely say that my computer is booting usb only as it first  say the option to select language and then the installation menu and then it says keyboard language selection .....etc but it stops at detecting cdrom ....bla,bla..
there is no wifi chip i have in my pc .,,actually i dont have any knowledge about graphic card but sending you a image of graphic card[IMG][IMG]http://i.imgur.com/tY1bisV.png[/IMG][/IMG]

---

### Post by mörgæs on 2014-12-08
Have you tried disabling the CD drive in BIOS?

---

### Post by sudodus on 2014-12-08
> **legendaryman said:**
> lubuntu-14.10-alternate-i386.iso this is exactly the version and also note that i have tried several software to make it bootable like unetbootin ,lili , 
**Linux Live Usb Creator,win32 disk image,using cigwin dd command**

 and several others but result is same ...and i can surely say that my computer is booting usb only as it first  say the option to select language and then the installation menu and then it says keyboard language selection .....etc but it stops at detecting cdrom ....bla,bla..
there is no wifi chip i have in my pc .,,actually i dont have any knowledge about graphic card but sending you a image of graphic card[IMG][/IMG]

Check that the download was good so that the iso file is correct. You can check with ***md5summer*** in Windows and compare with the listed string in

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If there are problems with the graphics driver or some other driver, maybe you should try **nomodeset** or some of the other boot options. See

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) 

-o-

It might also be a general problem, that 14.10 is too new for your old computer. To check that you can download and try an Ubuntu flavour or a community re-spin based on 

- Ubuntu 14.04.1 LTS: Lubuntu 14.04.1, which might work better than 14.10.

- Ubuntu 12.04 LTS or some other distro, which is known to work well with old hardware.

Xubuntu 12.04 LTS (end of life April 2015, not much time left)
LXLE, Bodhi, Bento (versions based on 12.04 LTS with end of life April 2017)

Still under development, but very promising for old hardware: ToriOS

- Other distros:

ultra light: Wary Puppy, Tiny Core

medium light, but good recognition of hardware: Knoppix

---

### Post by legendaryman on 2014-12-11
> **sudodus said:**
> Check that the download was good so that the iso file is correct. You can check with ***md5summer*** in Windows and compare with the listed string in

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If there are problems with the graphics driver or some other driver, maybe you should try **nomodeset** or some of the other boot options. See

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) 

-o-

It might also be a general problem, that 14.10 is too new for your old computer. To check that you can download and try an Ubuntu flavour or a community re-spin based on 

- Ubuntu 14.04.1 LTS: Lubuntu 14.04.1, which might work better than 14.10.

- Ubuntu 12.04 LTS or some other distro, which is known to work well with old hardware.

Xubuntu 12.04 LTS (end of life April 2015, not much time left)
LXLE, Bodhi, Bento (versions based on 12.04 LTS with end of life April 2017)

Still under development, but very promising for old hardware: ToriOS

- Other distros:

ultra light: Wary Puppy, Tiny Core

medium light, but good recognition of hardware: Knoppix

):Pthanks for your reply ''yes i have checked the download for md5 verification and also tried nomodeset ..actually i have searched a lot before creating this thread but no solution worked .......did you know any linux distro  which does not have any problem during installation by using pendrive,and it have features like ubuntu 14 .. ...while search for my problem i have found that most users have installlation problems when they using pendrive...

---

### Post by sudodus on 2014-12-11
I still cannot tell the cause of your problem.

- Does the computer boot from USB? If it does not, no distro will work. If it does, it is worth testing different distros and versions according to my previous post. I hope and think that we can help you to make it work.

- I think booting from USB works most of the time, but we seldom find the success stories here. Most people post here in order to get help with problems.


Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

When we know these things about your computer, we can give better advice.

---

### Post by legendaryman on 2015-02-08
> **sudodus said:**
> I still cannot tell the cause of your problem.

- Does the computer boot from USB? If it does not, no distro will work. If it does, it is worth testing different distros and versions according to my previous post. I hope and think that we can help you to make it work.

- I think booting from USB works most of the time, but we seldom find the success stories here. Most people post here in order to get help with problems.


Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

When we know these things about your computer, we can give better advice.
mercury pi865d7
intel p4 3.20 ghz 3.19ghz ,504mb of ram
504mb ram
no external graphic card only on board graphics which is intel extreme graphics 2
no wifi card iam using wired internet

---

### Post by sudodus on 2015-02-08
It should work to install ***Lubuntu***. Maybe version 14.04.1 LTS will work better than 14.10. Try it live before installing. (You might need to try it with a desktop iso file, but install it with an alternate iso file).

See the following link with tips and look particularly for tips about Intel graphics [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

If still no go, I think you should try a community re-spin based on Ubuntu 12.04 LTS, ***Bodhi*** or ***LXLE***, which promise support until April 2017. (Lubuntu 12.04 has passed end of life.)

You might also try ***Knoppix***, ***Wary Puppy*** or ***TahrPup***.

---

### Post by legendaryman on 2015-02-08
> **sudodus said:**
> It should work to install ***Lubuntu***. Maybe version 14.04.1 LTS will work better than 14.10. Try it live before installing. (You might need to try it with a desktop iso file, but install it with an alternate iso file).

See the following link with tips and look particularly for tips about Intel graphics [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

If still no go, I think you should try a community re-spin based on Ubuntu 12.04 LTS, ***Bodhi*** or ***LXLE***, which promise support until April 2017. (Lubuntu 12.04 has passed end of life.)

You might also try ***Knoppix***, ***Wary Puppy*** or ***TahrPup***.
):Phi which to download from this page [http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/](http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/) ..so confused between .sfs and .iso file ....morever ,did it can be installed using pendrive....

---

### Post by sudodus on 2015-02-08
> **legendaryman said:**
> ):Phi which to download from this page [http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/](http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/) ..so confused between .sfs and .iso file ....morever ,did it can be installed using pendrive....

See this link.

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

I know that it works to download an iso file and install to CD/DVD. I have also treated Wary Puppy with isohybrid* in linux and installed it with mkusb.

I am not sure Unetbootin can make bootable pendrives of Puppy, I have not tried it. TahrPup is more modern and is more likely to work directly when installed to a USB pendrive. There are instructions and tips in this link, also to install from Windows, if you haven't got a linux computer running.

[http://puppylinux.org/wikka/InstallationIndex](http://puppylinux.org/wikka/InstallationIndex)

-o-

To sum it up: Puppy is easy to boot from CD/DVD. It may be harder to make a USB boot drive as a first step. But if you can use another computer, where the CD drive works, you can boot from the CD and install Puppy into a USB pendrive (using Puppy's own tools to do it).

[HR][/HR]*)

You can find this hybrid iso version of Wary Puppy at the following link[COLOR=#696969], but I have not done the corresponding treatment with TahrPup (yet).[/COLOR]

[http://phillw.net/isos/linux-tools/hybrid-isos/](http://phillw.net/isos/linux-tools/hybrid-isos/)

Check the download with the corresponding md5sum and install it to a USB pendrive with [mkusb]("https://help.ubuntu.com/community/mkusb") in linux and [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows.

---

