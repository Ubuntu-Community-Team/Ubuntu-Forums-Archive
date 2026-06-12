---
title: "Just a few simple questions, nothing complex"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by throese on 2011-02-14
So, I'm still trying different backup methods, so far it saves my OS into an ISO file (Remastersys). Now, about Remastersys, I hear it cannot save the OS if it is bigger than 12 GB, but why is that the limit?

Is it possible to install a Linux distro directly onto a USB device such as this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822145323](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145323) OR this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820148154](http://www.newegg.com/Product/Product.aspx?Item=N82E16820148154)

I know that this can be installed directly onto the flash drive: [http://www.dreamlinux.net/download.html](http://www.dreamlinux.net/download.html)

Any other Linux distros that can be installed and run (or is it ran) from a Flash Drive or External USB Hard Drive?

Any suggestions for external hard drives, looking for around 320 to 750GB of disk storage space.

Thanks for all of the help.

---

### Post by dabl on 2011-02-14
> **throese said:**
> 

 Now, about Remastersys, I hear it cannot save the OS if it is bigger than 12 GB, but why is that the limit?



Sorry, I have no idea whether that is true or false, or why it would be limited. Sounds like a question for the remastersys devs.

> 

Is it possible to install a Linux distro directly onto a USB device such as this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822145323](http://www.newegg.com/Product/Product.aspx?Item=N82E16822145323) OR this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820148154](http://www.newegg.com/Product/Product.aspx?Item=N82E16820148154)



_Installing_ -- absolutely yes; provided that _booting from_ such a device depends on things like BIOS and your partitioning scheme, etc. etc.  Possibly this will interest you:  [http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

> 

Any other Linux distros that can be installed and run (or is it ran) from a Flash Drive or External USB Hard Drive?



Yes, actually I'm not aware of a distro that cannot be installed and booted from a USB storage device.

> 

Any suggestions for external hard drives, looking for around 320 to 750GB of disk storage space.



Being a cheapskate, I bought a big (but not very fast) Samsung Spinpoint SATA drive, and then bought an external enclosure/interface, and assembled it myself. Something like this:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6324331&Sku=R12-40924](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6324331&Sku=R12-40924)

Fair warning -- backing up hundreds of GiB of data will take hours, due to the USB bus throughput.  Pay no attention to the burst speed of the USB 2 bus -- throughput over time is painfully slow.

Hope that helps.

---

### Post by ankspo71 on 2011-02-14
Hi,
See these links for tutorials and downloads for installing Ubuntu (and other distributions) on USB drives:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Ubuntu has the ability to burn 'live cds' on USB drives too. Start Up Disk Creator. If it not installed in Ubuntu you can install it by installing "usb-creator-gtk" 

I have never done either of the above before though. I know people who have though and they like doing it. They are using the smaller USB drives like the one in your second and third picture.

Ubuntu sells Ubuntu on USB too (but they are small)
[http://shop.canonical.com/index.php?cPath=16](http://shop.canonical.com/index.php?cPath=16)

I'm only guessing now.... but Remastersys might be limited to 12gb because the compressed image size might exceed the size of a DVD (4.7gb), or is limited by the size that can be handled by the compression software (squashfs?).

Hope this helps

---

### Post by ankspo71 on 2011-02-14
Hi again,
I found the info your looking for:
> Your system size cannot exceed 4GB as that is the maximum filesize supported by ISO9660. Of course this also applies when using squahsfs. But the differece is that a 4GB squashfs can contain roughly 12GB of data within it.
 [http://remastersys.sourceforge.net/tips.html](http://remastersys.sourceforge.net/tips.html)

---

### Post by presence1960 on 2011-02-14
Back up your OSs with [Clonezilla]("http://clonezilla.org/")

---

### Post by throese on 2011-02-14
I had a bad experience with Clonezilla. =(

---

### Post by presence1960 on 2011-02-14
> **throese said:**
> I had a bad experience with Clonezilla. =(

That was probably due to user error. Clonezilla works.

I had a bad experience with my first installation of ubuntu. I wiped my entire disk. That also was user error. That did not stop me from using ubuntu. I try to learn from my mistakes.

---

### Post by throese on 2011-02-14
Me too. Oh, question about .deb installation packages. I DLed the Oracle Virtual Box software a month or so ago. Saved that .deb package to an external drive, just tried installing it through that file and it said "Error: Package may not exist or is out of date". What is the point of saving those .deb packges if they 1) Won't work 2) Have to be re-downloaded everytime you do a fresh install via Software Center or Synaptic Package Manager?

Thanks for the help so far.

---

