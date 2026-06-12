---
title: "Installing graphics drivers"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by volksgewer on 2010-03-26
I an new to Ubuntu and I am trying to install the drivers to my ATI graphics card so that I can get Counter Strike Source to work fluiently.  Does any one know how to do this?

---

### Post by mikewhatever on 2010-03-26
System->Admin->Hardware Drivers.

---

### Post by volksgewer on 2010-03-26
It says "No proprietary drives are in use on this system"

---

### Post by quadproc on 2010-03-26
> **volksgewer said:**
> I an new to Ubuntu and I am trying to install the drivers to my ATI graphics card so that I can get Counter Strike Source to work fluiently.  Does any one know how to do this?
I am running a pair of HD4870 cards in crossfire mode and I have been through such an installation a few times.  Perhaps I can help.

First, you need to find out the versions of the ATI cards, the version of the fglrx driver that is compatible with both your card and the Ubuntu version, and the Ubuntu version.  Do an lspci | grep ATI if you don't know your card's particulars.  Check ATI's site for the downloadable drivers.  Be forewarned that older ATI cards require older ATI drivers which are no longer supported by ATI.  If you are in this circumstance then you are pretty much stuck with the "ati" open source driver or with getting new video hardware.  If your hardware is new enough then pick the driver that is suitable for everything that you have.

ATI seems to be taking a really serious interest in contributing to the open source drivers but it is premature for such a driver (ATI + FOSS) to be available.  I would suggest keeping your eyes and ears open on this subject.

Once you have located the correct driver then it is time to decide how to install the driver.  You could use the system > admin > hardware drivers utility (which is actually named jockey-gtk) to do this, but it combines all the operations into one single "black box" and doesn't give you any insight into what is happening.  It can also take a very long time during which you get no indication of what is happening.  I use a step by step procedure, below.

I suggest creating a directory for doing the driver installation.  The ATI file is bigger than 80 MB so it may take a while to download, depending on your Internet access speed.  Download the appropriate ATI file into this directory.  If this went OK then you can proceed directly to the installation by typing ```
./<name of downloaded file> --install --keep
``` Note that the file is a self-extracting file; the first three hundred lines or so are a shell script which prepares things to uncompress and organize the remainder of the file into numerous directories and files on your system.  Ordinary text editors choke on the compressed stuff so if you want to see the shell script use something like ```
head -n 305 <name of downloaded file>
```.

The --keep option leaves all of the files used during the installation on your system.  You can then study them if you like.  You can also remove all of them after the installation is successful.  The --install option is self explanatory.

Once the installation is complete, you need to be sure that the X server knows the correct driver to use.  Here is the part of my /etc/X11/xorg.conf file which specifies the driver:```
Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection
```Note that the BusID is probably unnecessary in your file, and is probably wrong for your hardware configuration so I would leave that out unless you have multiple video devices in the computer; in that case, use the correct BusID for your configuration.

Now, on to the jockey-gtk problem.  This utility** does no**t necessarily correctly report the situation in your system.  In my system, it reports that the driver is present but is not activated, and "no proprietary drivers are in use on this system".  Wrong.  It is working and is in use.  I turned in a bug on this subject but the response was, paraphrased, "it is working correctly". Do **not** press the activate button; it is not necessary and I do not know what it would do.

If your installation does not work after installation then probably your best bet for troubleshooting is to edit your xorg.conf file and to replace "fglrx" with "ati" so that you can at least use the system while you are figuring out what went wrong.  Note that you'll need to be privileged to change the xorg.conf file.

I hope that this sheds enough light on the subject.  Please ask if anything needs more explanation.

quadproc

---

