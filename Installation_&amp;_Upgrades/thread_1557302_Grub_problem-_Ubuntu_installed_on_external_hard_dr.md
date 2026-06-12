---
title: "Grub problem- Ubuntu installed on external hard drive"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by garycheng12 on 2010-08-20
This is the problem: I get this error: "error: no such device: .... grub rescue". 

I have Ubuntu installed on a partition in an external hard drive and Windows installed on the internal hard drive.

I only get the error when the external hard drive is not plugged in during the boot operation; otherwise, I get this nice menu that allows me to select which OS to boot (that is GRUB... right?)

How can I make it so that if 

A) External hard drive is plugged in, I get the menu (which is already the case)

AND 

B) If External hard drive is NOT plugged in, it will automatically boot into Windows?

I don't know how GRUB works at all, nor do I know how to install it or use it. Should it be installed on the external hard drive? If so, how?

Also, I've did some Googling and I was wondering if Startup Manager should be used to solve this specific problem.

Thanks, guys!!

P.S. I have a problem with "Desktop effects could not be enabled" when I selected "Extra" for visual effects, even after using the current graphics driver. It clearly worked before I reformatted (I have an 8800GT graphics card, it worked without lag).

---

### Post by iDignify on 2010-08-20
The point of installing Ubuntu on an internal hard drive is so you don't need the Live CD or USB to boot. Why would you install Ubuntu on an external hard drive anyways?

---

### Post by tommcd on 2010-08-20
> **garycheng12 said:**
> 
How can I make it so that if 
A) External hard drive is plugged in, I get the menu (which is already the case)
AND 
B) If External hard drive is NOT plugged in, it will automatically boot into Windows?
You have probably installed grub2 to the MBR of the internal hard drive. You should have installed grub2 to the MBR of the external hard drive. This would allow you to do what you want to do.
1. Boot your Windows install CD and fix the MBR. There are numerous tutorials on the net for how to do this for every version of Windows. This will allow you to boot Windows normally.

2. Next, boot the Ubuntu live CD with the external hard drive plugged in. Open a terminal and run:
```
sudo fdisk -l
```
This will list all of your partitions. 
If you only have 1 internal hard drive, the external hard drive will likely be /dev/sdb1 in the *fdisk -l* output. This assumes that there is only 1 partition on the external drive. The output of *fdisk -l* will list whether the partitions are linux or Windows.
Anyway, to install grub2 to the MBR of the external drive, see this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Just choose the MBR of the external drive and you should be all set.

---

### Post by tommcd on 2010-08-20
> **garycheng12 said:**
> 
I don't know how GRUB works at all, nor do I know how to install it or use it. Should it be installed on the external hard drive? If so, how?

You can learn everything you need to know about grub2 from:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
Everything I know about grub2 was from those 3 links.

---

### Post by presence1960 on 2010-08-20
> **garycheng12 said:**
> This is the problem: I get this error: "error: no such device: .... grub rescue". 

I have Ubuntu installed on a partition in an external hard drive and Windows installed on the internal hard drive.

I only get the error when the external hard drive is not plugged in during the boot operation; otherwise, I get this nice menu that allows me to select which OS to boot (that is GRUB... right?)
[COLOR="Red"]
How can I make it so that if 

A) External hard drive is plugged in, I get the menu (which is already the case)

AND 

B) If External hard drive is NOT plugged in, it will automatically boot into Windows?[/COLOR]

I don't know how GRUB works at all, nor do I know how to install it or use it. Should it be installed on the external hard drive? If so, how?

Also, I've did some Googling and I was wondering if Startup Manager should be used to solve this specific problem.

Thanks, guys!!



P.S. I have a problem with "Desktop effects could not be enabled" when I selected "Extra" for visual effects, even after using the current graphics driver. It clearly worked before I reformatted (I have an 8800GT graphics card, it worked without lag).

This should be a simple fix but I need more detailed info. Let's get a better look at your setup & boot process. With your external plugged in boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Then there should be a very simple two part fix for which I will give you exact commands to run to achieve the highlighted red text in your quote above.

---

