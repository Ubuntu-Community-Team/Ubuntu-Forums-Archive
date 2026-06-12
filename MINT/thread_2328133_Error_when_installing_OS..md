---
title: "Error when installing OS."
date: 2016-06-17
forum: MINT
---

### Post by Zack_Weinstein on 2016-06-17
I have an Acer Aspire One which I just upgraded the drive in, to a 1 TB SSD drive from a 160 GB HDD drive. I have prepared the drive with linux mint cinnamon 32bit using the dd tool on my mac. It boots up just fine but when I try to run the installation program I get the following message or something very similar to it: "The creation of swap space on partition #5 has failed" (it goes into a little more detail than that but that is pretty much it). Also when this message pops up underneath it the installation program asks me for my time zone but no matter how many times I hit the okay button on the message it will not go away.

I have been using linux for about year and a half so you do not half to answer as if I know nothing but do not make it to complicated.
-Thanks

---

### Post by howefield on 2016-06-17
Thread moved to the "*MINT*" sub forum.

---

### Post by yancek on 2016-06-17
It would be useful to know what the 'little more detail' actually is.  Had you already created a root partition on which to do the install before trying to create swap?  Is there unallocated space available on the drive?  Did you use the manual (Something Else) installation option?

---

### Post by Zack_Weinstein on 2016-06-17
Yes I did create a root partition and a swap partition using the install program. I had no option to install manually, it is possible that I was not yet at that step. Also there was really not that much more in the error message I just said that because I did not copy and paste it or copy it exactly, and I am pretty good with linux so I know that I got all the important parts of the message.

Thanks

---

### Post by yancek on 2016-06-17
Just to clarify, you said you made the bootable usb on your Mac.  Are you trying to install to a Mac or to a PC?  Is there another operating system on whichever computer you are trying to install to and if so, what? 

If you got to the point of selecting a partition for the root of the filesystem and swap then you previously had an option for Installation Type.  Select "Something Else" which is the manual option.  That is the third image at the Ubuntu link below.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

If you have another OS installed it will matter if it is UEFI or MBR and also the number of partitions if MBR and whether there is any unallocated space available.

---

### Post by Zack_Weinstein on 2016-06-17
I did make the drive on my mac and I am installing it on a pc. There is no other os on the drive. I did get to the installation type part of the install but I can not find any options for actually choosing the type.

---

### Post by yancek on 2016-06-18
If you see the Installation Type window as shown in the 3rd image at the link I posted, you just click the radio button to the right of the "Erase disk" option as you have nothing else on the drive, OS or data.  If you have anything on the drive, you need the Something Else option.  If you can't click the radio button, something is wrong with either the downloaded iso or the creation of the bootable medium.

---

