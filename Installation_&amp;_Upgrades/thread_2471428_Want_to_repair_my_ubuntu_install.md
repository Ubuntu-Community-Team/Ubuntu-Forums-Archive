---
title: "Want to repair my ubuntu install"
date: 2022-01-30
forum: Installation &amp; Upgrades
---

### Post by sam-2s on 2022-01-30
I installed ubuntu in a dual-boot in a lenovo ideapad flex 5. It worked fine when I installed it but when I turned it off and tried to access windows it acted out and didn't let me access my previous windows installation. Then I tried ubuntu again and it gave me the intramfs error, so I tried the fsck on the files I thought were corrupted but that only left me with "Failed to mount early API filesystems ... Freezing Execution" and I couldn't do much from there. Here is my diagnosis from the boot repair: [https://paste.ubuntu.com/p/7QqcWf7SXM/](https://paste.ubuntu.com/p/7QqcWf7SXM/)

---

### Post by tea for one on 2022-01-30
[COLOR="#0000FF"]Line 66 - 68[/COLOR] - One OS detected  OS#1:   Ubuntu 20.04.3 LTS on nvme0n1p5
[COLOR="#0000FF"]Line 33 [/COLOR] - Failed to mount '/dev/nvme0n1p3 No such file or directory

It looks like your Windows partition did not mount possibly due to filesystem damage.

It is generally accepted that Windows tools are used to repair Windows systems and Linux tools for Linux systems.
Do you have backups of your data?
If not, organise your back-ups now.

Do you have a Windows repair/installation disk?

---

### Post by ajgreeny on 2022-01-30
Did you make sure that Faststart (a type of hibernation instead of full shutdown) was disabled before installing Ubuntu?

That is essential for dual booting as far as I remember, though I've not used Windows except for virtual installs since my XP in 2005.

---

### Post by sam-2s on 2022-01-30
I bakced up some data. Some of it is in the cloud via OneDrive, some of it is in another computer, but I think some of it might be lost. Do you know how I would go about oganizing my back-ups now that I don't have access to Ubuntu or Windows? I also don't have a Windows installation disk, how do I make one?

---

### Post by sam-2s on 2022-01-30
No I did not make sure of that. I'll have it in mind for next time

---

### Post by tea for one on 2022-01-30
> **sam-2s said:**
> I bakced up some data. Some of it is in the cloud via OneDrive, some of it is in another computer, but I think some of it might be lost. Do you know how I would go about oganizing my back-ups now that I don't have access to Ubuntu or Windows? 

Boot into a live session using your Ubuntu usb stick.
Locate the files/folders in both Ubuntu and Windows partitions.
Copy the data you wish to keep to another usb device.

---

### Post by sam-2s on 2022-01-30
Thank you so much

---

### Post by tea for one on 2022-01-30
> **sam-2s said:**
> I also don't have a Windows installation disk, how do I make one?

In essence, it is very similar to making an Ubuntu usb device.

If Windows 10, download the ISO from [https://www.microsoft.com/en-gb/software-download/windows10iso](https://www.microsoft.com/en-gb/software-download/windows10iso)
Minimum 8GB usb stick
Burn the ISO using a suitable utility.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) in Ubuntu
[https://www.ventoy.net/en/index.html](https://www.ventoy.net/en/index.html) 
[https://rufus.ie/en/](https://rufus.ie/en/) if you can access another Windows PC

I used Rufus via a Windows 10 VM with good results.
I tried Ventoy but did not have a successful outcome.

There are plenty of other utilities and innumerable online tutorials/guides.

---

