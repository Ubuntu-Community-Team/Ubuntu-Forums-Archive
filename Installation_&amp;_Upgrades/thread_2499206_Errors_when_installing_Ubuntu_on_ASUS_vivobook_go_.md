---
title: "Errors when installing Ubuntu on ASUS vivobook go 15 e1504g"
date: 2024-07-18
forum: Installation &amp; Upgrades
---

### Post by sidylaye on 2024-07-18
Hello I am having trouble with the installation of ubuntu 24.04 lts on my ASUS laptop as standalone when I tried first all looked good but when I reboot instead of accessing my Ubuntu desktop , there was unit frame and when I tried exit command I was shown some line like in this photo [ https://askubuntu.com/questions/538115/ubuntu-busybox-initramfs-error-14-04]( https://askubuntu.com/questions/538115/ubuntu-busybox-initramfs-error-14-04)
Also I have already disabled QuickBoot/FastBoot and Intel Smart Response Technology (SRT) but it is always showing that.
Afterward I tried what was here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
The part with the title Installing Ubuntu for Single Boot with a Random Boot Mode
So am here to share you what boot-repair gave me and I will be waiting for your help thank you 
[https://paste.ubuntu.com/p/R3qxNghSwx/](https://paste.ubuntu.com/p/R3qxNghSwx/)

---

### Post by sidylaye on 2024-07-18
It seems like my problem is from my ssd hard disk wd3200bevt-22zct0

---

### Post by yancek on 2024-07-19
In the image you posted with the ALERT message, it is pointing to a partition with the UUID beginning with 2df110c2.. which should be the UUID of the device on which Ubuntu is installed.  Line 163 of boot repair shows that to be:  sdb2     ext4     054586f5-fb7d-4acd-b0a1-d7e5728f636e.  Line 61 of boot repair shows your Ubuntu install on sdb2.

Boot your Ubuntu install USB and use the Try Ubuntu option, open a terminal and mount the EFI partition (sdb1) and check to see what files are there.

```
sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
```

After doing that, you should be able to navigate there either in a terminal or file manager.  In a terminal, just use sudo ls /mnt/usb/boot/efi/EFI and see if there is an ubuntu directory there and what files it contains if any.  Beginning at line 45 of boot repair, it shows information on the EFI partition where the ubuntu directory and its files should show but do not.  THe files on a standard Ubuntu EFI install in that directory should be:

>  BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

If you go to the grub.cfg file on the EFI/ubuntu partition, it will show the UUID and it should be the one I posted above for sdb2.  Not knowing what choices you made, it is difficult to know why Grub was not installed properly and why no ubuntu EFI files are showing.  You might try the default repair suggested by boot repair.

---

### Post by sidylaye on 2024-07-19
Thx for your reply I will try that and tell you what&#8217;s happen

---

### Post by sidylaye on 2024-07-19
[https://ibb.co/wBr7t5r](https://ibb.co/wBr7t5r) here is what happened and also the si folder changed because I recreated the problem because I was trying some thing but no progress

---

### Post by sidylaye on 2024-07-19
[https://ibb.co/wBr7t5r](https://ibb.co/wBr7t5r)[COLOR=#000000] here is what happened and also the si folder changed because I recreated the problem because I was trying some thing but no progress[/COLOR]

---

### Post by oldfred on 2024-07-20
Do you have latest firmware fro both UEFI and SSD/NVMe drive?
Compare to vendors's support site
sudo dmidecode -s bios-version
udisksctl status

Another Vivobook, issues by brand often common across multiple models
Asus Vivobook S14 Also Zenbook
[https://askubuntu.com/questions/1432177/issues-with-dual-booting-of-asus-vivobook-zenbook-series-laptops-with-ubuntu-22](https://askubuntu.com/questions/1432177/issues-with-dual-booting-of-asus-vivobook-zenbook-series-laptops-with-ubuntu-22)

---

### Post by sidylaye on 2024-07-20
Hi sir thank you for your help but I&#8217;m trying to have Ubuntu 24.04 as stand alone without windows and I looked troughs the threads you mentioned but I don&#8217;t see my case 
here is the result of the command tou gave [https://ibb.co/YZY5TH8](https://ibb.co/YZY5TH8)

---

### Post by sidylaye on 2024-07-20
For more information sdc is the internal ssd hard disk where I want to have my Ubuntu , the sda is the external hdd hard disk where I have ventoy installed and where the Ubuntu iso file is and finally the sdb is an internet modem I plugged in to have lan connexion

---

### Post by oldfred on 2024-07-20
Please just copy & paste terminal output in code tags.
Easy to add code tags with Forum's Go Advanced editor & # icon.

But I am not going to research if your firmware versions are latest or not, you can go to vendor's sites and compare. 
If newer available, then best to update.

Link was because user had multiple issues with his Ubuntu install. And posted solutions to most of them.
But newer version of Ubuntu should in most cases resolve issues seen in older versions.

---

### Post by sidylaye on 2024-07-23
Hi hope you&#8217;re well so the thing is I saw what my problem was, it because my laptop have a ufs ssd so needed to mention the ufshcd-pci pilote to update initramfs 
[https://www.linuxquestions.org/questions/ubuntu-63/can%27t-find-uuid-4175738330/page2.html](https://www.linuxquestions.org/questions/ubuntu-63/can%27t-find-uuid-4175738330/page2.html) Here is the link to the answer and thanks a lot for your support

---

### Post by sidylaye on 2024-07-23
NB: I misspelled it is ASUS Vivobook go 15 e1504ga

---

