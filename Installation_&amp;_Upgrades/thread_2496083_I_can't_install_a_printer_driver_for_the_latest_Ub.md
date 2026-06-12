---
title: "I can't install a printer driver for the latest Ubuntu"
date: 2024-03-13
forum: Installation &amp; Upgrades
---

### Post by Gins on 2024-03-13
My computer was broken. I had only Ubuntu on it. It was nearly 10 years old. I threw it away. Now I bought a new Lenovo computer, which has Windows 11 . I succssfully installed Ubuntu on it. It is the version 22 .0 . 

When the computer starts, Ubuntu is the default operating 
system. I am pleased with it. I have used Ubuntu for more than 10 years.

My printer is HP Laser Jet Pro M 15 a . I can't get the printer working. There is a problem with drivers.
I have successfully installed snaps by following the following instructions. So snap works.
Your thoughts are welcome

......................................................................................................................................................................................
Enable snaps on Ubuntu and install hp-printer-app

Alternatively, snapd can be installed from the command line:

sudo apt update
sudo apt install snapd
Either log out and back in again, or restart your system, to ensure snap’s paths are updated correctly.

Install hp-printer-app
To install hp-printer-app, simply use the following command:

sudo snap install hp-printer-app****

---

### Post by ajgreeny on 2024-03-13
That printer which is USB only should be fully supported by **hplip** available from the repos of 22.04.

There is also a useful GUI to help you use it named **hplip-gui**.

I have no idea about the hp-printer-app snap package so can't help with that.
However, many printers are usable without any drivers so for a start, with the printer attached and switched on run command ```
driverless
```

---

### Post by Gins on 2024-03-14
Thanks for the reply.
I got the following output :
nissanka@nissanka-IdeaCentre-3-07IMB05:~$ driverless
ipp://HP%20LaserJet%20M15a%20(B27047)%20(USB)._ipp._tcp.local/
nissanka@nissanka-IdeaCentre-3-07IMB05:~$

---

### Post by ajgreeny on 2024-03-14
So the printer is detected by the system.
Have you actually tried printing anything and have you checked what is found using [http://localhost:631/](http://localhost:631/) from your web-browser?

---

### Post by Gins on 2024-03-15
Thanks ajgreeny for taking time to reply.
I got the following output from the URL you have mentioned.

**Queue Name**
HP_LaserJet_M15a_B27047_USB

**Description**
HP_LaserJet_M15a_B27047_USB

**Location**

**Make and model**
HP LaserJet M14-M17, driverless, cups-filters 1.28.15


**Status**
Idle

What is the meaning Idle status ?
Why is the location empty ?

---

### Post by ajgreeny on 2024-03-15
The empty location field is unimportant and simply means that you have not added a location in the printer setup. The location for mine is simply Home.
You did not say what happens if you try to print a document. Do you see nothing, not even a print dialog box?

I don't use Ubuntu but if you search for Printers in the Activities menu top left, it may give some clues. Does that show any printers as detected or listed as installed?

---

### Post by Gins on 2024-03-16
Thanks ajgreeny for the comments.
It was my mistake that I did not write more details.
1) I switch on printer.
2) I write a small letter using the wordprocessor.
3)  Afterwards, I use the 'Print' command on the wordprocessor.
4) The printer starts **blinking.** ( This is the output )
5) I go to Settings and look at the printer's icon, it says '**processing** '
 Even if I wait one hour, the printer's power button continuously blink. And the message ' processing' is there.
**The printer is detected. That is why I get the message processing.**
There is a small issue. Your thoughts are welcome.

---

### Post by ubfan1 on 2024-03-16
Recently having gone through a new printer setup (Cannon lbp 6030), I tried the various protocols offered by CUPS (off port 631), but could only get LPD to work.  Probably some matching options needed to be set on the printer to select for the newer protocols, but I could print whatever I needed, so didn't bother looking.

---

### Post by Gins on 2024-03-16
Probably Canon is easy to find drivers.
Your help is appreciated.
I don't know how to go ahead with this issue.

---

### Post by gezzer2 on 2024-03-17
this a link to the HP web site with the HP drivers.
use the drop down menu to click on Ubuntu and the drivers should download as a deb file.
[https://developers.hp.com/hp-linux-imaging-and-printing/gethplip](https://developers.hp.com/hp-linux-imaging-and-printing/gethplip)

---

### Post by Gins on 2024-03-17
Thanks gezzer2 for replying me.

I looked at it.
It has Debian and Ubuntu.
Which is the correct one for me ? 
Please reply me when possible.
I am using the latest Ubuntu Desktop version.

---

### Post by gezzer2 on 2024-03-18
Ubuntu would be the correct choice ..

---

### Post by Gins on 2024-03-18
Yes, I have tried it.

It opens Source Forge website. And struggled to download . 

I clicked Download HPLIP . Then I selected Ubuntu
The message was 'unverified download blocked'.
I can't fathom it.
I have registered in Source Forge website. So it should a legal download.

---

### Post by ubfan1 on 2024-03-18
I don't know about the source forge download, but have you just tried the browser local url localhost:631  and select install new printer?  Should find what printer is attached, and give you choices on protocol to use for connection.

---

### Post by MAFoElffen on 2024-03-19
I still have an old HP LaserJet II in my storage... It has extra memory, and a network adapter in the printer. 

As per ajgreeny's Post #2... I used and never had a problem using the 'hplip' driver straight from the Ubuntu Repo's. I would attach the printer viaUSB to set it up, then (later) use it as a network printer.

I don't see where you have tried to use the Repo's 'hplip' printer driver(???)

*** One note- I found that that printer series requires #22 paper. If I tried to use cheaper #20 paper, I would occasionally have jams. Never has jams using heavier paper.

---

### Post by Gins on 2024-03-19
Thanks MAFoElffen for taking time to reply me.

I bought a new Lenovo Windows computer.

Windows 11 works fine. And the printer works fine.

I installed Ubuntu. The problem is on Ubuntu side. I don't like Windows. I have used Ubuntu since 2010 .

My old computer was purely a Ubuntu computer. It went to hell. I used it for almost 10 years. I threw it away and bought a new Lenove computer. Lenove sells computes with Windows .
There is no issue with papers because it works fine with Windows 11 .

The following are the details I get from Printer dialog .
**Details of the printer**
HP_LaserJet_M15a_B27047_USB@localhost

Location 

Address   localhost

Driver:  HP LaserJet M14-M17, driverless

Serch for Drivers
Select from Database
Install PPD File

Why is loation empty ?
When I click Search for Drivers, the message is 'no suitable driver found'.
When I click Select from Database, I get drivers for lots of HP models . My printer is not there .
When I click Install PPD File, it will open all the files on my computer . There are printer drivers.

---

### Post by Gins on 2024-03-23
Hi Friends

I have not solved this problem . Your thoughts are welcome.  The printer works fine on Windows 11 side .

---

### Post by him610 on 2024-03-24
I have used an old laserjet printer, Dell 1700N, for about 17 or 18 years now. When setting it up using CUPS, I use the Raw, Generic laserjet driver. It always works. Never was able configure it using Dell laserjet driver. There have been no updated drivers for Dell 1700N from MS or Dell since before Win7.

---

