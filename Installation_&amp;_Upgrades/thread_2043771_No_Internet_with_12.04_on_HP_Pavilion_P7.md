---
title: "No Internet with 12.04 on HP Pavilion P7"
date: 2012-08-17
forum: Installation &amp; Upgrades
---

### Post by jistanidiot on 2012-08-17
I hope it is ok to ask this question here.  I asked it at some place called askubuntu.com but there have been no answers.  

I just bought an HP Pavilion P7-1235.  After playing with Win7 for a few days I decided it would be best to put linux on it.  I of course chose ubuntu 12.04. 

During the install it complained about not having an Internet connection.  There didn't seem to be any way to fix this so I let it go ahead and do the install without Internet.

Once installed, the main problem is that it doesn't seem to know there is a wired network card.  Also while it seems to think there is a wireless card, it will not connect to my network. I really want the wired to work since you can only configure my router with a wired connection and this is the only computer near the router. However I'll settle for making the wireless work.  

The wireless icon in the taskbar indicates no connection.  When you right click and choose network management settings, it will not let you confgiure any wired connection.  It will let you configure a wireless connection.  However using it will not connect to my network (WPA2 Personal security, IPv4, everything else defaults). 

What do I do to fix this?

Thanks in advance.

---

### Post by darkod on 2012-08-17
Usually it's the other way around. The wired network cards are mostly supported and you get wired internet working out-of-the-box.
Then using that you can make your wireless card working if it didn't by default.

Are you sure it doesn't detect the wired card at all, or maybe only the settings are not correct and it can't use the internet? There is big difference between internet not working and the card not being detected at all.

You should be able to check all interfaces with something like:
ifconfig -a

---

### Post by jistanidiot on 2012-08-17
ifconfig -a

shows two interfaces:

lo and wlan0.  Only lo has an inet addr (127.0.0.1).  

What do I do now? Still no internet.

---

### Post by darkod on 2012-08-18
You are right, it doesn't seem to detect any wired adapter.

What is wrong with connecting to the wireless? Where does it fail? When you click the networking icon top right, it should show you all detected wi-fi networks. If you are broadcasting your SSID your network should be there. Just click on it and it will ask you for the password. Enter it and that should be it.

---

### Post by jistanidiot on 2012-08-18
It finds no networks to connect to (Win7 on that same box finds 5 as does my laptop).  Just in case, I entered my network settings anyway and checked the connect automatically box.  However it never connects.

I'm ok if I can get it to connect wirelessly, but I really wanted this to be the box that manages my router which requires a wired connection for that.

---

### Post by darkod on 2012-08-18
If you open terminal and execute:
lspci

That will show you the network cards detected (among other PCI devices). Then you can google if there are any known issues/solutions for your wired and wireless cards and ubuntu.

You can also post them in the Networking section of the forum and some networking expert might have an advice.

---

### Post by jistanidiot on 2012-08-18
lspci gave a lot of info.

I think the relevant items were

01:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)

and 

04:00.0 Network controler: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)

Does this help any?

---

### Post by darkod on 2012-08-18
This link says the driver for BCM43225 is the STA:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Note the section how to install the STA driver with no internet access, not sure if it looks complicated or not to you. Basically it says you can use the ubuntu cd as a source.

This looks like the solution for the AR8161 ethernet but it assumes you already have a working internet access:
[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

Basically the AR8161 is so new that its driver is still not included in ubuntu.

---

### Post by oldfred on 2012-08-18
It looks like you have a Catch-22. Both of these assume the other is working so you can download the drivers.

[http://ubuntuforums.org/showthread.php?t=1970012](http://ubuntuforums.org/showthread.php?t=1970012)

[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

Did liveCD work on your system? If so one or the other drive must be in liveCD?

---

### Post by jistanidiot on 2012-08-23
Everyone thanks for the help so far.  However I'm still without any network connection.

Using the infromation linked to above, I followed the instructions for installing the broadcom without Internet.

After booting up and logging in, I inserted the install disk. I did the following from the terminal

```
cd /media/Kubuntu\ 12.04\ LTS\ amd64/pool/main/b/b43-fwcutter/ 
sudo dpkg -i b43-fwcutter*
```

As instructed, from a computer with Internet I downloaded files from openwrt.org and copied them to my home folder.
In the same terminal I did

```
cd
tar jxvf broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mino.o

```

The insturctions then said to to System->Administration->Hardware/Additional Drivers However I don't have such choices.  There was System->Additional Drivers.  Opening that gave an error about downloading failed and that drivers would not be available.

It listed no drivers what-so-ever.

I then rebooted, but still no drivers and no internet.

After rebooting I also tried
```

sudo modprobe -r b43 ssb
sudo modprobe b43
```
They did not appear to do anything.  

I'm still without any kind of Internet.

What can I do now?

---

### Post by darkod on 2012-08-24
The b43-fwcutter is for the b43 driver/module, not for the STA. Look more carefully in the STA section:

> 
**STA - No Internet access**

 If you do not have any other means of Internet access on your computer, you will have to install the bcmwl-kernel-source package from the [restricted]("https://help.ubuntu.com/community/Repositories/Ubuntu") folder under **../pool/restricted/b/bcmwl** on the Ubuntu install media. 
**Note:** Systems installed from CDROM can simply add the install CD as a [package source]("https://help.ubuntu.com/community/Repositories/Ubuntu") and install bcmwl-kernel-source, automatically installing the required dependencies. 
**Note:**  The following instructions are for a stock Ubuntu 10.04 LTS Edition via  USB install. Netbook edition, other variations and matured systems may  require more/less packages be installed to satisfy dependencies of  bcmwl-kernel-source. 
**Note:** The GUI front end for dpkg will automatically display required packages that need to be installed to satisfy the bcmwl-kernel-source  dependencies. To use the front end, navigate the file system using the  file manager and double click on the packages to install/list required  dependencies. 
**Step 1.** 
Navigate the install media and install the packages listed below by double clicking **or** navigate the install media and install these packages consecutively in a **terminal** (under the desktop menu **Applications > Accessories > Terminal**): 
../pool/main/d/dkms 
:/dkms/$ sudo dpkg -i dkms*../pool/main/p/patch 
:/patch/$ sudo dpkg -i patch*../pool/main/f/fakeroot 
:/fakeroot/$ sudo dpkg -i fakeroot*../pool/restricted/b/bcmwl 
:/bcmwl/$ sudo dpkg -i bcmwl-kernel-source***Step 2.** 
Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **STA** drivers can be activated for use. 
**Note:** A computer restart may be required before using the wifi card. 
 
**LiveCD/LiveUSB**

 **Note:** The install media contents are mounted under **/cdrom** of the filesystem. 
**Step 3.** 
For  temporary use with the LiveCD and LiveUSB environments, instead of a  computer restart, in a terminal issue the following commands: 

~$ sudo modprobe -r b43 ssb wl ~$ sudo modprobe wl[B]

Note:[/B] Allow several seconds for the network manager to scan for available networks before attempting a connection. 


---

### Post by jistanidiot on 2012-08-24
> **darkod said:**
> The b43-fwcutter is for the b43 driver/module, not for the STA. Look more carefully in the STA section:

Thanks.  I tried that just now.  I installed the four packages. And then went to look for System > Administration > Hardware/Additional Drivers I don't have that.  I only have System->Additional Drivers.  It starts but complains that the download failed and no drivers were available.  

Rebooting didn't give me any Internet.  Running the two modprobe commands also did nothing. 

What can I do now to get a network connection?

Thanks in advance.

---

### Post by jistanidiot on 2012-08-27
So I gave up on the broadcom crap.

From another computer I downloaded the stuff for the Atheros card.

The directions again were very wrong when it came to using the gui.  They were also wrong about needing to install a bunch of packages as they seem to have already been installed.  

The part about 
```
cd compat-wireless-2012-07-03-pc
./scripts/driver-select alx
make
sudo make install
```

and then 

```
sudo modprobe alx
``` was correct. 

Magically after doing that last command my Internet started working.  Unfortunatly it stopped right after I downloaded and installed the updates.  However doing it all over again fixed that too.

I'm not exactly thrilled that it breaks on updates, but I've written a script to execute those commands.  It will do for now.

---

