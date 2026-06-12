---
title: "Install Unbuntu 10.04 over MS Vista Home Premium"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by electronic.artifacts on 2010-04-05
All,
I have an Asus Notebook Series G71GX with Windows Vista Home Premium 64x. I want to install Ubuntu 10.04 32x version completely removing any trace of Windows.

I have set the bios to boot cd first and it does not see the iso file on the cd. I can see the same cd on my mac and it is readable there. I do not understand what the problem is.

The laptop has the following specs:
ACPI x64 based pc
Intel Core 2 P8700
6gb RAM
SATA AHCI Controller
iSCSI Initiator
PCI-E Gigabit NIC

Has anyone had experience installing 10.04 32x on a similar machine? Is there some hidden setting on Vista that keeps it from seeing an iso disk? I read on one forum that I need to change the sata drive settings in the boot menu so that Vista can see the iso files on the disk. Has anyone heard of this?

The laptop seemed like a good deal but I did not imagine Vista could be so hard to replace!

Thanks to any and all who might consider this post.

Regards,

Gene

---

### Post by zvacet on 2010-04-05
Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")? If doesn´t match download same iso with torrent and point download where your existing iso is.Torrent will check iso for bad files and replace them (if any) with good ones.After that run md5sum again.Burn iso on lower possible speed.But Ubuntu live CD and check disc integrity ( you will see that option in menu).When you come to the install stage you can delete Vista partition.I will use manual way to partition and make 

1. root = 10GB      ext4                     mountpoint /
2.swap = equal ram
3.home = rest of free space    ext4          mountpoint /home

---

### Post by electronic.artifacts on 2010-04-06
Thanks for your suggestion. I am using a DVD that I got from the Linux User magazine to Load the 10.04 so I did not do a check sum. Earlier, I downloaded an iso from the web site. I did not do a checksum on it either. Even though I was not able to get it to boot  from the cd either, I was able to load it into my test virtual machine.


But now it seems I have another problem. The DVD RW has failed. It will not read any disk at all so now I am going to have to fix this first.

Then I will do the check sum on the iso from the magazine. But, it sounds like that you not have difficulties doing and install of ubuntu over Vista.

Regards!

---

### Post by lisati on 2010-04-06
Did you remember to burn the ISO file as a "disk image"?

Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Edit: I have heard that -RW media don't always play nice when used for making an installation disk. Perhaps someone else can confirm?

---

### Post by electronic.artifacts on 2010-04-06
Thanks for sending the directions link. I had discovered a similar link earlier suggesting that software to burn the disk image with,which I did use. It did not however mention doing a check sum first.

When I could not get the boot disk for the CD to work, I used another tool mentioned in another link on this site, to put the boot image on a usb stick. It was an 8gb Corsair Flash Voyager. I changed the bios to boot on the usb and it would not boot from their either. I turned on the logging for the boot up and it shows the usb's turning on, then when it goes to boot it does not see the usb.

Because I could not get it to boot from CD or USB that was why I was focusing on the Vista operating system. I was thinking that there might be a Vista setting that I am missing.

I will not assume that the iso's that I have on the Linux user magazine DVD are good and will try to down load another iso and do the check sum on it.

Regards.

---

### Post by Mark Phelps on 2010-04-06
10.04 is still in beta testing, and therefore, buggy and unstable.  You would do better first booting from a LiveCD to ensure there are no hardware detection or driver problems -- before you do the install.

Also, since it IS still in beta testing, please post your 10.04-related questions to the proper beta testing forum: Development & Programming, Lucid Lynx Testing.  thanks

---

### Post by electronic.artifacts on 2010-04-06
Thanks for your comment, but I am more concerned about why I cannot get any distro to install on MS Vista versus which one that it is. So, that is why I went to the install and upgrade section. It could be version 9 or 10 and it will not install

Regards

---

### Post by Slim Odds on 2010-04-06
> **Mark Phelps said:**
> [COLOR=Sienna]10.04 is still in beta testing, and therefore, buggy and unstable.[/COLOR]  You would do better first booting from a LiveCD to ensure there are no hardware detection or driver problems -- before you do the install.
...

I believe that's most folks are finding it to be quite stable and only marginally buggy.

I agree that it's always good to try the Live CD first with any version, released or otherwise.

---

