---
title: "Dual-boot XP-Gusty problems"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by degeusjordan on 2008-03-08
Hey everyone,

I'm new here so sorry if I ask some stupid newbie questions.

I have an acer aspire 9300 laptop.
here are the specs. Its not a 1.6 processor its a 2ghz and the graphics card is a Go6100 not a 7300.
[http://www.afterdawn.com/hardware/product_details.cfm/2972/acer_aspire_9300-5005]("http://www.afterdawn.com/hardware/product_details.cfm/2972/acer_aspire_9300-5005")  

i installed xp and ubuntu. i didn't want ubuntu on the main hard drive so i installed it on a 80gb exernal hard drive. I was planning on using ubuntu at home and when i am out and about i would use XP. But i have come to realize that when i turn the computer on without the external hard drive plugged in i find it has some Grub error i believe its called. The problem is the only way i can boot into XP is if i have the hard drive plugged in.

Is there anyone that can help me fix this problem? i would like to be able to boot into XP when the external hard drive is NOT plugged it.

any information would be of great help.

Jordan

---

### Post by Pumalite on 2008-03-08
Fix your XP MBR with your Installation CD>Recovery>FIXMBR>FIXBOOT.
Or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Here is a guide:
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
Make sure that Grub gets installed to external drive.
You can find out with your Live CD; at the Terminal:
sudo fdisk -lu
That will tell you what /dev is your external, and then you change it from (hd0) in step 8 'Advanced' tab.

---

### Post by degeusjordan on 2008-03-08
> **Pumalite said:**
> Fix your XP MBR with your Installation CD>Recovery>FIXMBR>FIXBOOT.
Or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Here is a guide:
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
Make sure that Grub gets installed to external drive.
You can find out with your Live CD; at the Terminal:
sudo fdisk -lu
That will tell you what /dev is your external, and then you change it from (hd0) in step 8 'Advanced' tab.

alright when i reboot with the install disk, and i go through and get to where i have to press "R" it loads and asks what directory or something i would like to load. I press 1 and it goes on and asks for a admin password. I've tried everything i would ever use. Nothing works. I don't remember making a admin password. But the very first time i did this i wasn't asked for a admin password. So anyone have any ideas?

Jordan

---

### Post by degeusjordan on 2008-03-09
I finally couldn't figure it out so i just reinstalled ubunutu. I changed the GRUB location from (hd0) to (hd1). Now when i reboot with the external hd plugged in and i select starting with gusty it gives me the error 17. It says something like selected partition not able to mount.

what does this mean??

JOrdan

---

### Post by Pumalite on 2008-03-09
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

