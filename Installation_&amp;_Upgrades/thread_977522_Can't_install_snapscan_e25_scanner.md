---
title: "Can't install snapscan e25 scanner"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by paddy1 on 2008-11-10
_**I tried the following in a previous post: **_

Lightbulb  HOWTO: Epson Perfection 1670 Scanner (and other SnapScan scanners)
HOWTO: Epson Perfection 1670 Scanner

The scanner firmware comes in a file called ESFW30.BIN, which apparently is only available if you install the software on the CD-ROM provided with the scanner. Unfortunately, the software only installs under Windows and then you have to copy the software from the Windows machine to the linux machine. Or you can follow this simple process to download the firmware (provided by Jeff Silverman) and then update your /etc/sane/saned.conf

Code:

$ wget [http://www.commercialventvac.com/~jeffs/ESFW30.BIN](http://www.commercialventvac.com/~jeffs/ESFW30.BIN)
$ sudo cp ESFW30.BIN /etc/sane.d

Edit /etc/saned.d/snapscan.conf and change the line...

firmware /path/to/your/firmware/file.bin

...to point to /etc/sane.d/ESFW30.BIN

Code:

$ scanimage -L

You should see that your scanner is now detected. If so, you can now scan using XSane.

Other Similar Scanners - [http://snapscan.sourceforge.net](http://snapscan.sourceforge.net)

The process should be the very similar (you should just need to appropriate firmware) for other snapscan scanners. See the SnapScan Backen

**_This is what happened when I ran the code:_**

user@user-desktop:~$ wget [http://www.commercialventvac.com/~jeffs/ESFW30.BIN](http://www.commercialventvac.com/~jeffs/ESFW30.BIN)
--09:49:03--  [http://www.commercialventvac.com/~jeffs/ESFW30.BIN](http://www.commercialventvac.com/~jeffs/ESFW30.BIN)
           => `ESFW30.BIN'
Resolving [www.commercialventvac.com](www.commercialventvac.com)... 8.15.7.107, 63.251.179.17, 65.200.200.47
Connecting to [www.commercialventvac.com|8.15.7.107|:80](www.commercialventvac.com|8.15.7.107|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
09:49:13 ERROR 404: Not Found.

Would anyone have the proper install instructions please.

---

### Post by Partyboi2 on 2008-11-11
Looks like the site is down. So instead of using
```
wget [http://www.commercialventvac.com/~jeffs/ESFW30.BIN]("http://www.commercialventvac.com/%7Ejeffs/ESFW30.BIN")
``` grab the file from another source
```
wget [http://leroybrown.glassmelter.com/binaries/ESFW30.BIN](http://leroybrown.glassmelter.com/binaries/ESFW30.BIN)
```then continue with the instructions.

---

### Post by paddy1 on 2008-11-11
I tried the above web address, and I get the same response. error 404 not found. If I go to Leroybrown website, I can get the esfw30.bin file, and I downloaded it to my desktop. Now, how do I install it please?

---

### Post by Partyboi2 on 2008-11-11
Open a terminal and change to where the file is:
```
cd ~/Desktop
``` then copy the file to its new location (etc/sane.d)
```
sudo cp ESFW30.BIN /etc/sane.d
```Then open up the /etc/sane.d/snapscan.conf file
```
gksu gedit  /etc/sane.d/snapscan.conf
```then change the line
```
 firmware /path/to/your/firmware/file.bin
```to
```
firmware /etc/sane.d/ESFW30.BIN
```then save the changes and back in the terminal check to see if the scanner has been detected
```
scanimage -L
```

---

### Post by paddy1 on 2008-11-11
I tried this:

Then open up the /etc/saned.d/snapscan.conf file

Code:
gksu gedit  /etc/saned.d/snapscan.confthen change the line

Code:
 firmware /path/to/your/firmware/file.bin

When the config file opened, there was nothing in it to edit, just a blank sheet.

---

### Post by paddy1 on 2008-11-11
Ifound a typo in the line; gksu gedit  /etc/saned.d/snapscan.conf

Should read;  gksu gedit  /etc/sane.d/snapscan.conf

Contents of snapscan.conf;

#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /etc/sane.d/ESFW30.BIN
# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
# /dev/usb/scanner0 bus=usb

When I entered the following;
user@user-desktop:~/Desktop$ scanimage -l
[snapscan] Cannot open firmware file /etc/sane.d/ESFW30.BIN.
[snapscan] Edit the firmware file entry in snapscan.conf.
scanimage: open of device snapscan:libusb:001:004 failed: Invalid argument

Any reason that it doesn't work now?

---

### Post by Partyboi2 on 2008-11-12
It seems to not be able to open the firmware file. If you have the windows driver for it, you could try using the esfw30.bin file from that and see if it works.

---

### Post by paddy1 on 2008-11-12
I cannot download the file from [http://www.commercialventvac.com/~jeffs/ESFW30.BIN](http://www.commercialventvac.com/~jeffs/ESFW30.BIN), and the file ESFW30.BIN from leroy must be corrupt. I did all of the above, redownloaded the file, and I keep getting the same results.

I get the error; 
Cannot open firmware file /etc/sane.d/ESFW30.BIN. Edit the firmware file entry in snapscan,conf. scanimage: open of device snapscan:libusb:001:003 failed: Invalid argument

Is it possible that there is a bug in the system?
Totally frustrated.

---

### Post by Partyboi2 on 2008-11-13
Is ESFW30.BIN the correct file for your scanner or should you be using the
Snape25.bin?
If you have the scanners installation disk for windows you can use the correct file from that by copying it over to the /etc/sane.d directory.
Another thing to do is to remove the # from infront of ```
# /dev/usb/scanner0 bus=usb
``` of the /etc/sane.d/snapscan.conf file so it would look something like:
```
#------------------------------ General -----------------------------------

# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /etc/sane.d/ESFW30.BIN
# If not automatically found you may manually specify a device name.

# For USB scanners also specify bus=usb, e.g.
   /dev/usb/scanner0 bus=usb
```

---

### Post by paddy1 on 2008-11-14
Thanks so much Partyboi2. It was the Snape25.bin file I needed. It was confusing because all this info I gathered said to use ESFW30.BIN. I donate refurbished computers to needy children, and this would have been a nightmare for them to install. It would be nice if the developers took a step back and tried to adapt the same program used to search for printers, to work for detecting "ALL" hardware, like windows.

Thanks again for your help.

---

