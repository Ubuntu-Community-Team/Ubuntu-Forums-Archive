---
title: "How can I Install Ubuntu to a Secondary Hard Drive?"
date: 2006-05-19
forum: Installation &amp; Upgrades
---

### Post by muffinhead on 2006-05-19
The title of the thread means exactly what it says. My main Hard Drive, is C:\ , the one with Windows XP on it. I recently decided That I want Ubuntu on a seperate partition on a secondary Hard Drive, while still installing the grub boot loader, to the master boot record of my main hdd.

This is so I can use all the space on my C:\ Drive, my main hdd, for Windows XP, and programs. Also I'm a bit worried about having Ubuntu on the same Hard drive as my windows installation, although I don't mind installing the grub boot loader to it, because it doesn't take barely any space. This has absolutely nothing about Ubuntu, it's just I want too keep my main drive free for programs, and utilities.

How would I do this without Losing my current data, or messing both ubuntu, and windows XP up? is there a way to back up my installed .deb, and other packages, so I don't lose them during a reinstall?

Much Thanks to anyone that can let me know and help, Links are appreciated, Thank You:)

---

### Post by Ted D. on 2006-05-19
Should not be a problem. Just answer the questions when installing and Kubuntu should install according to your preferences

---

### Post by aysiu on 2006-05-19
Read these three links:

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

P.S. Same rules that apply to partitions apply to drives.

---

### Post by confused57 on 2006-05-19
If you haven't already installed Grub onto the windows mbr, you could take a look at these 2 links("lha" has some great instructions):

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper)

[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)

---

### Post by muffinhead on 2006-05-19
Thanks for the Links;)  , But my other question was, Is there a way I can back up my currently installed packages, and tranfer them back, once I do the reinstall?

I am asking that, because I'm on a 56k Dial-Up connection, and it takes forever to download anything, so I thought it would be better if there was a way I could backup, my already installed packages, and restore them once I do the Reinstall.

Thanks if you can let me know;)

---

### Post by aysiu on 2006-05-19
Use PartImage, and you won't even have to reinstall Ubuntu.

It copies your entire partition as is.

If I'm understanding you correctly, you currently have Ubuntu and Windows installed but on one drive.

You want to move Ubuntu to the second drive and make more space on the first drive for Windows.

From Ubuntu, install GParted and format the second hard drive as Ext3.

Boot up a live CD, "install" PartImage (it's really be installed to your computer's RAM, though) and copy the Ubuntu image to somewhere else (an external hard drive or iPod or blank DVD). Then, load up PartImage again and restore the Ubuntu image to the second hard drive. 

Restore Grub to the MBR. I think PartImage has a utility for backing up the MBR as well, but you can always go [the old-fashioned route](http://ubuntuforums.org/showthread.php?t=24113).

Make sure you can boot to the second drive okay and that your "new" Ubuntu installation works. Then, when you're satisfied it does work, use GParted on your *new* installation to delete the old Ubuntu from your first hard drive and give the rest of the space to Windows.

---

### Post by muffinhead on 2006-05-20
Thanks for the Links;)  , But my other question was, Is there a way I can back up my currently installed packages, and tranfer them back, one I do the reinstall?

I am asking that, because I'm on a 56k Dial-Up connection, and it takes forever to download anything, so I thought it would be better if there was a way I could backup, my already installed packages, and restore them once I do the Reinstall.

Thanks if you can let me know;)

---

### Post by aysiu on 2006-05-20
If you use PartImage, you won't have to do a reinstall, and you'll be copying your entire Ubuntu installation *as is*, including the packages and **everything**.

---

