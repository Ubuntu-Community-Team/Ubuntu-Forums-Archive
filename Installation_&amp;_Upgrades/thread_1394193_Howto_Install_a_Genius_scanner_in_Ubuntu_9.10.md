---
title: "Howto: Install a Genius scanner in Ubuntu 9.10"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by DawieS on 2010-01-30
Installing a Genius ColorPage-Vivid 1200XE flat-bed scanner in Ubuntu 9.10 
 
When I first plugged the scanner into a USB port, I could see that it is detected by Ubuntu, however Xsane did not correctly connect and communicate with the scanner. After doing a lot of research on the internet, I found that it is a question of a missing driver file. I have now installed the scanner in Ubuntu 9.10 and it is working perfectly. If you follow these **[COLOR=Red]3 steps[/COLOR]**, it will be easy.

[SIZE=3][COLOR=Red]**Step 1**.[/COLOR][/SIZE]

Locate a small firmware file named 'CCD569.fw' with size 8KB and dated 29 September 2003. This binary file is included in the driver CD that came with the scanner, and is required by the XSane scanning package to correctly communicate with the scanner. The firmware file can be located by any [COLOR=SeaGreen]**1**[/COLOR] of the following **[COLOR=SeaGreen]3 methods:[/COLOR]**

**[COLOR=SeaGreen]Method 1.[/COLOR]**
If you have an existing Windows XP installation with the scanner installed, and you clicked on the default values when installing the driver, the firmware file will be located in the folder 'C:\Program Files\ScannerU'.

**[COLOR=SeaGreen]Method 2.[/COLOR]**
If you don't have an existing Windows installation with the scanner installed, but still have the CD, you can extract it from the compressed 'data?.cab' files within the '32bits' folder on the CD. Create a 'temp' folder in your home folder using your file browser. Copy the following 3 files from the '32bits' folder on the CD into the 'temp' folder that you have just created, using your file browser:
data1.cab
data2.cab
data1.hdr
Install the 'unshield' package (if you don't have it already) using Synaptic Package Manager. Open a terminal and type the following commands:

cd temp
unshield x data1.cab

The firmware file will be located in the folder /home/yourname/temp/DRV_USB_GT6816.

**[COLOR=SeaGreen]Method 3.[/COLOR]**
If you don't have the original driver CD, you may download the driver file '1200xe.exe' from the website http://www.geniusnet.com. You now have 1 of 2 choices:
**Choice 1.**
Install the driver into any existing Windows XP installation. The firmware file will be located in the folder 'C:\Program Files\ScannerU'.
**Choice 2.**
Install the 'wine' package (if you don't have it already) using Synaptic Package Manager. Install the driver file in 'wine'. The firmware file will be located in the folder 'C:\Program Files\ScannerU'. (I have not tried this myself, but have read of others that has done it).

[SIZE=3]**[COLOR=Red]Step 2.[/COLOR]**[/SIZE]

Now that you have located the firmware file, open a terminal. Type the command 'sudo nautilus'. This will open a file browser with root permissions, which are required since you will be saving the file outside your home folder. Use the file browser to copy the file 'CCD569.fw' from where you have located it, into the folder '/usr/share/sane/gt68xx'.

[SIZE=3]**[COLOR=Red]Step 3.[/COLOR]**[/SIZE]

Close the file browser (with elevated permissions) and the terminal. Delete any 'temp' folder that you may have created. You are now ready to start scanning. Click on the Applications/Graphics/Xsane Image Scanner tab. You may now experiment with different settings to find a good balance between quality and file size to suit your needs. Tip: Xsane requires the destination folder, where images will be saved, to be private (not readable by others). Click on the stiffy icon (left of the filename) and choose 'Create Folder' on the next screen. You may name it 'scan', or whatever, and the permissions will be correctly set upon creation. Alternatively you may use a file browser to create and set the permissions of the destination folder.
I have found Xsane to be a much better scanning package than the original software on the driver CD. You now have complete control of all possible parameters, which are automatically saved on exit. Enjoy your scanning !


**[COLOR=Black]Note:[/COLOR]**
 If you have a different scanner, and it did not work out of the box, the chances are good that you can get it working using this procedure. Note that there will be some variation in the name of the firmware file and folders as described in **[COLOR=Red]Step 1[/COLOR]**. If you can get a different scanner working using this procedure, please post the following to help others with their installations:

name of firmware file
name of folder where it can be located

**[COLOR=Black]Note:[/COLOR]**
When you upgrade to a new scanner, remember to delete the old firmware file from the folder '/usr/share/sane/gt68xx'.

---

### Post by ZeratulAyuris on 2010-04-05
Additional choice for method 3 is to use unrar & unshield to get this file from archive.
First, unrar the 1200x.exe to some directory:
```
unrar e 1200x.exe SomeDir\
cd SomeDir
```Second, do 
```
unshield -d DestinationDirectory x data1.cab
```in directory mentioned above to extract .cab file to DestinationDirectory.
At least, grab the CCD569.fw file from directory DRV_USB_GT6816 under the DestinationDirectory. ???? profit )

If you don't have unrar and unshield, just do
```
sudo apt-get install unrar unshield
```

---

