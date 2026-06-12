---
title: "Should I install with Dell's ISO"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by vellamike on 2014-02-01
I am installing Ubuntu on a Dell e7240 and I was wondering if I should use the dell ISO here: [http://linux.dell.com/files/ubuntu/precise/12.04-OSP1/](http://linux.dell.com/files/ubuntu/precise/12.04-OSP1/) ?

On a [driver update post]("http://www.dell.com/support/drivers/us/en/04/DriverDetails/Product/latitude-e7240-ultrabook?driverId=0WKFN") Dell suggest it but it's not mentioned anywhere else on the internet.

Does anyone have any idea about this?

---

### Post by tfrue on 2014-02-02
If you have a power edge server, or a precesion desktop, then I would install using that image. I've never had a case where it mattered, but that image might contain certain drivers like NIC or Ethernet drivers. The best way is to try both options and see which one works, and I don't think it matters friend. I've live booted on many Dell, Toshiba, HP, and Acer machines with the same image I downloaded from Ubuntu.

---

### Post by oldfred on 2014-02-02
That now is an old image with 12.04.2. In a couple of weeks 12.04.4 will be out.
Someone posted that all of the Dell sputnik updates were in 13.10.
See details in communitydell site also, applies to many Dells not just Precision.

       Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by vellamike on 2014-02-03
Thanks guys, I'm going for the standard 12.04.

---

### Post by vellamike on 2014-02-03
It looks like installing the standard 12.04 was a pretty bad idea. Wireless doesn't work - I think the dell driver fixes [here]("http://www.dell.com/support/drivers/us/en/19/DriverDetails/Product/latitude-e7240-ultrabook?driverId=0WKFN") would solve this issue but they don't seem to be easy to install unless you used that prepackaged version of dell.

I am dual booting and would like to replace my current Ubuntu OS with the dell one - does anyone have any advice on how to do this?

---

### Post by oldfred on 2014-02-03
Only use manual install or Something Else. Then from installer choose your existing ext4 / (root) partition as the new / partition. It should find swap.
I think 13.10 or wait for 12.04.4 would be better.

 Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik

[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)

---

### Post by vellamike on 2014-02-03
The Dell ISO was definitely not the way to go in the end - LAN didn't even work! The instructions on that website were misleading too, 

I'm going to install 13.10 and see if the wifi gets fixed - if not I'll have to look at what's already been done on this and start a new thread.

---

### Post by vellamike on 2014-02-03
**UPDATE**: I installed 13.10 and everything seems to be working really nicely - Wifi and touchpad (which wasn't working quite perfectly in 12.04). Wonderful!

---

