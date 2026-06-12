---
title: "Problem Using UNetbootin"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by OceanBitz on 2011-05-20
Time to upgrade from Windows to Ubunu.  UNetbootin does not see my USB connected hard drive, an old WD400, connected via a SATA/IDE to USB 2.0 Adapter.  The drive has 20 MB formatted as Fat32. I have selected on the first screen the distribution (Ubuntu), the Type (USB Drive) but the Drive down arrow does not display my H drive where Windows Explorer has placed.   I can attach a memory stick and it sees that ("I").  WD400 is definitely there and I can access. 

I am running Windows 7 Home  SP1 on a Dell 546.  The Bios indicates that 1st Boot Device is [Removable Dev.]. 

  

Appreciate some guidance.

---

### Post by jerrrys on 2011-05-20
download the iso and use unetbootin 'manual load option' also with manual option its not even necessary to format the device

---

### Post by OceanBitz on 2011-05-20
Thanks, I would hate to screw up at this point.  See all sorts of places to DL Ubundo but none indicate an ISO image.  Appreciate if you had a site to offer.  
I am surprised it cannot see my USB drive now yet will if I simply indicate I am going to grab the iso from my hard drive.

---

### Post by jerrrys on 2011-05-20
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by OceanBitz on 2011-05-20
Got the ISO - just did not realize that was behind the download button, expected an exe.  Howeve3r, no better off.  Of course with UNetbootin, I now chose and provided location for my iso.  Still you have to direct the install to a USB Drive.  The down arrow shows none.  If you just hit OK the error display" No USB Flash drive was found...." and advises you might try formatting as Fat32.  Mine is Fat32.  

Admittedly my external is a conventional inboard drive just hooked via the USB and provide with an external power supply.  See no reason why that would be different than any drive attached via USB.  Now it is not a Flash, mentioned in the Error, but there is no mention of that limitation in the UNetbootin instructions.

---

### Post by Shibblet on 2011-05-20
Unetbootin has worked less for me over the years.  Go to: [www.pendrivelinux.com](www.pendrivelinux.com) and use that instead.

---

### Post by jerrrys on 2011-05-20
[ATTACH]192721[/ATTACH] don't understand why its not giving you this option

---

### Post by OceanBitz on 2011-05-20
I certainly have no idea why the Drives drop down list box is empty.  So I tried the suggestion to try the Universal USB Installer offered by Pendrivelinux.com.  Very similar screen again again no H drive in their drop down listbox.  However they have another option which shows all drives and of course a warning to be careful.  I used that the the cmd scrip ran its course and placed a lot of files on my H (USB) drive.  

However it boots into Windows.  Note my Bios appears to offer to boot from the USB first as indicated in my original question.  Now I have no idea what to expect at this point or what to look for.  I was a fair DOS user a few years ago<g> and have been with Window ever since.  Appreciate another nudge.  Sure would like to explore Ubuntu but do not even know what to expect on booting.

---

### Post by jerrrys on 2011-05-20
so you now have the iso loaded to your usb drive, but something is amiss in bios?

---

### Post by ppv on 2011-05-20
How old is the computer you are trying to boot on. 

External hard drives are seen differently than flash drives. This is why you were not getting the option to select your USB HDD while writing the iso.

You could also try other options in bios such as USB ZIP, or USB FLOPPY and see if one of those works. If you have a flash drive it would be simpler to do this on it.

---

### Post by OceanBitz on 2011-05-20
This computer was purchased in August 2009, a Dell 546.  It has a Planar MB F896N.  I cannot say I understand the BIOS screen where is does list Boot Setting as 
 1st Boot Device           [Removable Dev.]
  2st Boot Device           [CD/DVD:TSST ev[ DV]
  3st Boot Device           [SATA:WDC WD3200 AAB]
  Boot Other Device      Yes
but then there is another entry that indicatges the HD is the primary bootable device.


Was the software I used suppose to create a MRB on my external and if so how might I confirm its presence or absence?


The errors certainly spell out "flash" but then all the documents simply discuss a USB drive - and you are correct as I noted, both software detected a 1GB flash drive I tested.

---

### Post by ppv on 2011-05-20
> **OceanBitz said:**
> 
The errors certainly spell out "flash" but then all the documents simply discuss a USB drive - and you are correct as I noted, both software detected a 1GB flash drive I tested.

Do you see any errors. What are they and where do you see them.

Apart from them, did you use administrator rights in Windows while creating the drive. Otherwise, in the start menu's search box, type the name of the program that you are using to create the drive, right-click the entry that shows up in the results and select "run as administrator" and then create the drive again.

---

### Post by OceanBitz on 2011-05-20
Sorry, this answer went into cyber space, so will try again.  My computer was purchased new in August 2009, a Dell 546.  The Bios offers Boot settings which are curreltnly specific as:
            1st Boot Device           [Removable Dev.]              2st Boot Device           [CD/DVD:TSST ev[ DV]
              3st Boot Device           [SATA:WDC WD3200 AAB]
              Boot Other Device      Yes


That to me suggests it capable of booting from a USB.


I did not realize there was a difference from the perspective of "bootable" between a flans and conventional HD.  Certainly the error mentions Flash but the rest of the instructions simply refer to USB hard drive. 



I think I have had it for unknown reasons - would have loved to learned a bit about Ubuntu.


Thanks for your efforts.

---

### Post by OceanBitz on 2011-05-20
Just read this which further confuses:
*"Some say when you put a drive on any sata port, the bios reverts to  that device as primary boot device, no work around I have ever found,  you might try flashing to the latest bios version available.  Most people wind up putting the OS on the Sata drive to solve it.."*

---

### Post by ppv on 2011-05-20
You do not need to flash the bios, atleast for now. Can you list down the following and we can try to get it booting.

- you created your usb hard drive with administrator privileges, have set the first boot device option in bios to removable device, but yet it does not boot. Is this how it is right now?
- If yes, what error does it give

Can you check around in the bios if there are options to set the order for removable devices as in removable device is where it should first boot from but there can be multiple removable devices on a computer.

And it is that you want it on the removable hard disk specifically or using the flash drive is fine.

---

### Post by OceanBitz on 2011-05-21
Sorry I confused - forgot about page 2 on this forum and ended up double posting without answering some questions.  I am making progress with your help - and "we" will succeed.
ppv - I have UAC turned off so no problem there.  The only error messages I have seen were with omitting the UNetbootin Drive entry (where there was no choice), hitting OK wihich then indicated it could not find a "flash" drive.  I got around that by using  Universal USB Installer which gave me the option of selecting my H drive.  I am not sure why ppv brought up flashing the BIOS - that has not been considered or an issue.

Now the good news, I have found confirmed that I may have to try all six of my USB ports - that all may not be activated immediately (anyone know how to cut that trial and error down?)

The next is that although my BIOS lists the order of boot with the USB first (as I indicated early) there is another option I overlooked "Hard Disk Boot Priority.  It now shows 1st Drive [my Dell SATA drive] and 2nde Drive [my USB WD400 that I have attached].  I do not understand why there seems to be this redundancy in options and worse, which one has priority.  Any of you have any knowledge in this area.  

Also I am still wondering how to tell if the Universal USB Installer did its job.  Here are the files it installed on my USB Drive:
FOLDERS
.disk
boot
casper
dists
install
pics
pool
preseed
syslinux
FILES
autorun.inf
ldlinux.sys
md5sum.txt
README.diskdefines
ubuntu
Uni-USB-Installer-Copying.txt
Uni-USB-Installer-Readme.txt
usb-creator.exe
wubi.exe
USB drive

Over the weekend I will start a trial and error approach - not comfortable.

---

### Post by ppv on 2011-05-21
> Just read this which further confuses:
*"Some say when you put a drive on any sata port, the bios reverts to   that device as primary boot device, no work around I have ever found,   you might try flashing to the latest bios version available.  Most  people wind up putting the OS on the Sata drive to solve it.."*

Flashing the bios was brought because of the above post. Anyways, you do not need to do it.

>  It now shows 1st Drive [my Dell SATA drive] and 2nde Drive [my USB WD400 that I have attached].

Just change the order here. Make your WD400 as the first drive and the Dell Sata drive as the second one.

You can use any USB port as long as you do not connect any other USB devices except the WD400 drive which has Ubuntu on it.

---

### Post by OceanBitz on 2011-05-21
Got it, I am now a Ubuntu user.  You guys certainly helped.  The first clue was the suggestion to try  Universal USB Installer rather than UNetbootin.  Although my drive still did not display in their drop down list box, the option to select from all drives present allow me to select H, my USB external.  The second clue was your advise to be persistent - it should work.  What I had overlooked was that the CMOS offered a Hard Disk Boot Priority which I did not examine because below was the "Specified boot sequence" which acknowledged my Removable as 1st.  Spent an hour Googling but discovering any discussion of the significance of Boot Device Priority vs Boot Sequence but finally just bit the bullet and change the order in the first where my SATA was listed first.  That did it without playing with my six ports.  I suspect from other info I have read they may just all work.

ppv I beat you by about an hour but you were right on - thanks for sticking with me.

Now to learn a new OS

Ed

---

### Post by ppv on 2011-05-22
So you now have Ubuntu running :)

---

### Post by djbigwillie on 2011-11-02
Hello I am new to mounting on ubuntu, I have an ISO for windows n want to make it bootable through USB I have configured the USB on Gparted to NTFS but then when I get to Unetbootin it does not show the SHOW ALL FILES check box in the options after I check the USB drive option. I have the newest Unetbootin is there something in the properties I need to configure to see this option?

---

