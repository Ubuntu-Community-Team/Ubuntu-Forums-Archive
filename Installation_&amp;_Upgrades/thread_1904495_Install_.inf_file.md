---
title: "Install .inf file"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by UltimateCat on 2012-01-04
Hi:D
I am using Windows Wireless Drivers and in the process of trying to install the drivers.
Windows Wireless Drivers shows me a small box that says: Install New Driver
Well, when I select the file with the driver in it and click install a small window opens and says:
Not a valid driver .inf file
What is a  " inf file" ?
How would I know where this  (.inf file) is to alert Windows Wireless Drivers Mgr to install it?


I have opened the folder with the driver in it and see a file " debian - binary" 2.0; I am 
clueless on what this is.  I installed the ndiswrapper-common_1.56-1_all.deb and installed the nsidwrapper - utilis 1.9_ 1.56-1_136.deb and Ubuntu told me that the install was successful. 

I found this website in the "Ubuntu Linux Bible"
[http://sourceforge.net?apps/mediawiki/ndiswrapper/index.php?support.html](http://sourceforge.net?apps/mediawiki/ndiswrapper/index.php?support.html)
So I'm going to visit the site and see if it helps.
Any feedback and insight would be music to my ears.:(

---

### Post by ottosykora on 2012-01-05
.inf file is a script that gives the windows the commands what has to be installed and configured for some specific device driver.

In windows there is somewhere under system even a directory with many .inf files. you can open one in any text editor and see what is inside.

With a windows driver mostly also this inf file is coming and the installation is going then according the steps given in it.
The inf file has to be in some default position or you have to point the installation to it.

I am not sure what are you trying to do. Install linux driver on linux? Install windows driver on windows? Install windows driver via ndiswrapper?

---

### Post by UltimateCat on 2012-01-05
> **ottosykora said:**
> .inf file is a script that gives the windows the commands what has to be installed and configured for some specific device driver.

In windows there is somewhere under system even a directory with many .inf files. you can open one in any text editor and see what is inside.

With a windows driver mostly also this inf file is coming and the installation is going then according the steps given in it.
The inf file has to be in some default position or you have to point the installation to it.

I am not sure what are you trying to do. Install linux driver on linux? Install windows driver on windows? Install windows driver via ndiswrapper?

I am trying to install the inf file that is inside of the RAR zip file on my Windows partition in a folder while I am on the Ubuntu side. I don't understand how to get that Ndiswrapper driver that I installed on my windows side while in Ubuntu.
I also have the driver for the Linksys Adapter WUSB54GC ( RT73 driver) on my Gnome desktop.
And also on my desktop is the driver for the NIC made by Realtex but it's the Linux driver for the Realtex card. ( The card keeps kicking me offline)
I have sucessfully installed the 2 Ndiswrapper's 1.56-1_all.deb and 1.5 6-1_136.deb
   When I go to Admin> Windows Wireless Drivers a window opens
The Window gives me the option to Install New Driver
But when I highlight the driver another window opens and tells me 
" Not a valid driver .inf file"
I am having a hard time finding this inf file that Ubuntu wants. I don't know how to look at my Windows partition from the Ubuntu side to grab that other Ndiswrapper file that I downloaded. 
Been trying to get my Linux/Ubuntu 10.04 Ultimate Edition 2.7 online for 6 weeks now.
I have only been able to get online with the Windows side.

---

### Post by ottosykora on 2012-01-06
I would suggest to copy the files from the download place to your linux home folder and start playing there instead trying it to unzip it from linux on the windows partition.

And if the inf file is the correct one I do not know, if the hardware is not described in the inf file then it is simply not made for that hardware.

---

### Post by Mark Phelps on 2012-01-07
MS .inf files are very specific to individual makes and models of hardware.  Each device has info in Windows Device Manager identifying it.

So see what yours are, go into Windows, open Device Manager, right-click each Network device, open the Details tab, and select the Hardware IDs under the Property pulldown.  Write down that info.

Then, look inside the .inf file you're trying to install.  If it does not have the same Hardware IDs, it will not work.

---

### Post by UltimateCat on 2012-01-10
> **Mark Phelps said:**
> MS .inf files are very specific to individual makes and models of hardware.  Each device has info in Windows Device Manager identifying it.

So see what yours are, go into Windows, open Device Manager, right-click each Network device, open the Details tab, and select the Hardware IDs under the Property pulldown.  Write down that info.

Then, look inside the .inf file you're trying to install.  If it does not have the same Hardware IDs, it will not work.

I will try that
Thank You

---

### Post by UltimateCat on 2012-01-10
> **ottosykora said:**
> I would suggest to copy the files from the download place to your linux home folder and start playing there instead trying it to unzip it from linux on the windows partition.

And if the inf file is the correct one I do not know, if the hardware is not described in the inf file then it is simply not made for that hardware.
I took your advice and put the zipped driver on my usb memory stick and carried it over to my Gnome desktop.
Windows Wireless Driver assisted me with the rest of the install of that driver and the inf file. The install was successful.
Thank You

---

### Post by ottosykora on 2012-01-10
hmmm, it is always a bad idea to try to run anything directly from a compressed archive.
The problem is, that often the file manager gui , like under windows suggest us to do so and does display the contents of such archive as it was not packed at all and could be used straight away. 
They even display it open if the file is located on some drive on other side of the world and suggest one can run such things via any sort of dta connection. All this is seldom the case, and particularly running scripts which needs to call up other files and their contents and place results in predefined positions will fail.

---

