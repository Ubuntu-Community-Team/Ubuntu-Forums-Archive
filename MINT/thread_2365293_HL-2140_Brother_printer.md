---
title: "HL-2140 Brother printer"
date: 2017-07-04
forum: MINT
---

### Post by Kevin McCready on 2017-07-04
My new version of Linux doesn't work with either my printer or my scanner. But I'd be grateful for help with the printer first.

When I try to print, the printer just spits multiple blank pages, although it seems to print a test page properly.

I've downloaded the drivers from Brother website (I didn't know if my linux was ppm or deb, so I tried both).
[http://support.brother.com/g/b/downloadhowto.aspx?c=nz&lang=en&prod=hl2140_all&os=127&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadhowto.aspx?c=nz&lang=en&prod=hl2140_all&os=127&dlid=dlf006893_000&flang=4&type3=625)

But when I got to the step :
```

bash linux-brprinter-installer-*.*.*-* HL2140

```

I got an error message saying 
"Driver-packages cannot be found.
 Confirm the model name."

I tried various name combinations: HL-2140, HL-2140-series, Brother-HL-2140-series 

Maybe the driver is stored somewhere that I don't know of?

My system is:
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=18
DISTRIB_CODENAME=sarah
DISTRIB_DESCRIPTION="Linux Mint 18 Sarah"
NAME="Ubuntu"
VERSION="16.04 LTS (Xenial Xerus)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 16.04 LTS"
VERSION_ID="16.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
UBUNTU_CODENAME=xenial

---

### Post by CatKiller on 2017-07-05
Yes, the script from the page you linked doesn't appear to accept that model of printer as an option, even though that page suggests that it should.

However, selecting .deb (which is what Debian-derived distributions like Ubuntu and Mint use for package management) takes you to a different page and gives you a different file. I have no idea whether that file will work or not, but it would be the appropriate one to try.

I have always steered clear of Brother printers.

---

### Post by deadflowr on 2017-07-05
*Thread moved to **MINT***

---

### Post by kurt18947 on 2017-07-05
I've had very good luck using Brother's installer script. I guess it's possible that there has been a glitch introduced or something.  Here are the drivers for the HL-2140 printer. When I did manual installs Brother recommended installing both the lpr and CUPS drivers. The instructions seem to indicate that only CUPS is required if CUPS is supported. The method I've used in the past recommended the lpr driver first then CUPS.

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl2140_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl2140_all&os=128)

Here are the manual install instructions:

[http://support.brother.com/g/s/id/linux/en/instruction_prn3.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_prn3.html?c=us_ot&lang=en&comple=on&redirect=on)

Those directions only talk about the lpr driver. You should be able to install the CUPS driver using the same line but substituting the CUPS name for the lpr name. I haven't had to do anything with the "pre-required" instructions in years. You could also use Gdebi, a .deb package installer rather than the command line instructions if you'd prefer.

---

### Post by Bucky Ball on 2017-07-05
Are you positively in the correct directory? You must navigate to the directory you have downloaded the script to.

---

### Post by Kevin McCready on 2017-07-05
Thanks everyone. No luck. It still spits out multiple blank pages (I'm saving on ink). I've installed the deb files separately (lpr, cups) with gedbi. Then when I run the installer (sudo bash linux-brprinter-installer-*.*.*-* Brother-HL-2140-series) it says "Driver-packages cannot be found. Confirm the model name." I'm doing it all from the same directory. I'm not convinced the installer is looking in the right place for the files. Is there a generic linux driver I can use instead of Brother. BTW I also see that Brother release the source code. But I don't have the skills to tweak that if that's the problem ([http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl2140_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl2140_all&os=128))[IMG]file:///home/k/Documents/BrotherPrinterProblem.png[/IMG]

---

### Post by Bucky Ball on 2017-07-06
It sounds like you are not putting the printer model at the end of the command line. YOU must do that. It doesn't happen 'automagically'. 

Your command, presuming you are in the same directory as the file and you have untarred the tar.gz file, should look something like this.

```
bash linux-brprinter-installer-2.1.1-1 HL-2140
```

You need the name of the file and the device model at the end of the line, NOT this.

```
bash linux-brprinter-installer-*.*.*-* Brother machine name 
```

That is just a generic example on the Brother site, NOT the command. Issuing that would likely output the error you are receiving and little else. YOU need to fill in the correct details for the printer and version of brprinter installer and I have a feeling, from the error you're getting, you haven't. ;)

All you need is the [brprinter-installer from here]("http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hl2140_all&os=128&dlid=dlf006893_000&flang=4&type3=625"), untar that tar.gz file and then run the untarred file as instructed above. The printer should be plugged in and switched on. (Read the instructions on that link carefully. It tells you the command to use to untar the file, but again, you need to fill in the correct details, probably '2.1.1-1' in place of '*.*.*-*'.)

Please post the exact line you are using to try and get brprinter to run. It is also essential you untar the tar.gz file that arrives when you download brprinter-installer. Nothing will happen until you do. The uncompressed file is what the command works on, not the tar file.

Once complete, open 'Printers' and delete any you have created there then 'Add'. When you get to the install driver part you will find the driver for your machine there if you have successfully installed it via the brprinter installer. Good luck.

My guess is you have the command wrong. The installer is 'one size fits all' and once you specify the printer you are using in the command above, the installer will select the correct driver for your model and the rest should go smoothly.

PS: Just to confirm, easiest to do this with the printer plugged directly into the computer via USB. Don't try using wireless or ethernet (although the latter can be done I believe, USB most straightforward).

Here it is in point form.

[LIST=1]
[*]Download brprinterinstaller
[*]Open terminal and navigate to downloaded file then untar it (see link instructions)
[*]Run ```
bash linux-brprinter-installer-2.1.1-1 HL-2140
```
[*]Open 'Printers'
[*]Delete any printers (meaning delete any previous failed attempts to avoid confusion)
[*]'Add' your printer.
[/LIST]

Fingers crossed.

* Incidentally:

[QUOTE=CatKiller]Yes, the script from the page you linked doesn't appear to accept that model of printer as an option, even though that page suggests that it should.[/QUOTE]

Extremely unlikely (and Brother make some of the most Linux friendly printers on the market so  wouldn't avoid unless the basis of the aversion has nothing to do with compatibility).

---

### Post by Kevin McCready on 2017-07-06
WOW. You're amazing Bucky Ball. It worked. Thank you so much. I've been tearing what's left of my hair out for a couple of days.

But I think the problem was the brother command:

```
bash linux-brprinter-installer-*.*.*-* HL2140
```

It should have been
```
sudo bash linux-brprinter-installer-2.1.1-1 HL-2140
```

with sudo and the exact install number instead of ***

Now for my scanner problem. LOL.

---

### Post by Bucky Ball on 2017-07-06
You got it. It was the command. Needs the correct details for brprinter version and printer model. ;)

Got there in the end. Now you can enjoy your Brother printer while you're growing your hair back! :)

(I'm on my second Brother printer from the HL series so familiar with the drill.)

---

### Post by kurt18947 on 2017-07-06
> **Kevin McCready said:**
> 

Now for my scanner problem. LOL.

Are you sure the scanner isn't already installed? The second portion of the installer script installs the scanner on my installs.

---

### Post by Kevin McCready on 2017-07-07
It's a different device. 
device `avision:libusb:006:005' is a Hewlett-Packard ScanJet 5300C flatbed scanner
I've started a new thread for help. 
[https://ubuntuforums.org/showthread.php?t=2365463](https://ubuntuforums.org/showthread.php?t=2365463)

---

