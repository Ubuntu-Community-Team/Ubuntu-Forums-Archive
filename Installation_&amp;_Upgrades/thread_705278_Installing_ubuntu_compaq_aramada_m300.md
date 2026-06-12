---
title: "Installing ubuntu compaq aramada m300"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by luichi on 2008-02-23
Hi, i have compaq aramada m300 which dosen't have cd, can't boot cd (i have verison 1.02 of the bios and i have searched and i think i can't), has usb, can't boot usb, hasn't any operating system installed, has grun installed, have floopy and can boot it. It has

---

### Post by dstew on 2008-02-23
Your post is incomplete, but it seems your question is how to install on a system without a bootable CD or USB drive. Assuming you can connect to the internet, the easiest way in my opinion is to do a network installation. If you can boot a floppy, you can use the [unetbootin]("http://lubi.sourceforge.net/unetbootin.html") utility.

If you do a network install, be aware that the installer will sit at 6% with a "Please wait..." message for an hour or two while it is downloading packages. Lots of people abort the installation, thinking nothing is happening, because the installer gives you no feedback. If this makes you uncomfortable, you can install the server (base) system, with a generic kernel, which takes a half hour or so. Then you can boot into the base system, and using the command line install the rest of the Ubuntu desktop:```
sudo apt-get install ubuntu-desktop
```This takes about an hour on a DSL line, but you get to see all the messages.

---

### Post by luichi on 2008-02-23
Before having no operating system installed i had ubuntu and i was able to connect to internet with a cable like this: [http://www.ictcompany.com/Products_icn/3Com/Cable/3cpc-com-cbl.jpg](http://www.ictcompany.com/Products_icn/3Com/Cable/3cpc-com-cbl.jpg) and with another cable like this [http://www.superinventos.com/images/S180558.JPG](http://www.superinventos.com/images/S180558.JPG). Connecting these two cables on my laptop and  with my router thompson tcw710 i will be able to install ubuntu with unetbootin? I will have to open any port on my router? 
I searched if i find a bios upgrade for my laptop but the only website i found was this: [http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=96720&lang=en&cc=us&prodTypeId=321957&prodSeriesId=96234&taskId=135](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=96720&lang=en&cc=us&prodTypeId=321957&prodSeriesId=96234&taskId=135) but i don't know what i have to do in this page anyway i think i have the latest version (1.02) and i think i only can boot from a floopy anyways i don't have a cd reader but i have one usb port. Also, i searched if i found the brand of the bios but i hadn't found it. And like i said i have grub installed.

Finally i found this: [http://www.pendrivelinux.com/2008/02/13/pendrivelinux-2008-install-from-windows/](http://www.pendrivelinux.com/2008/02/13/pendrivelinux-2008-install-from-windows/) which i think it will work but i've downloaded 2 or 3 times with problems anyways i'll try to download one more time.

According to my laptop which desktop would you recommend me?

I think this is all i can say. Please answer :D




Thanks.

---

### Post by dstew on 2008-02-24
> Connecting these two cables on my laptop and with my router thompson tcw710 i will be able to install ubuntu with unetbootin?I am not sure. It looks like your first "cable" is an adapter of some kind. I don't know if unetbootin will be able to establish an internet connection through that adapter, especially if the adapter requires special software. I know it works with a regular network card though. As far as your router goes, it should be configured as a DHCP server.
> According to my laptop which desktop would you recommend me?Probably you would be best off with Xubuntu. The more memory you have, the better. If you have only 64Mb of RAM, even Xubuntu will be a little slow. Better to have 128Mb if possible. But you can try Xubuntu even with 64Mb.

---

