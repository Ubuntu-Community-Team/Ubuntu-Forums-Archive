---
title: "PLZ HELP!Installing Problem for partition /dev/mapper"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by eamekwok on 2012-10-12
I'm really new to Linux. I downloaded the ISO file and then built a USB boot disk. And i get it boot from the U-disk. Actually I'm on this live disk now. I have win7 installed earlier. I have only one disk which is SSD. And i saved 40GB free space for Ubuntu. 
The problem comes when i choose to install for "something else".  I have all the previous partitions like "/dev/mapper/isw_cgebcggiab_volume****". I selected the free space and create partitions for / and /home and swap. Then i press install there's a dialog box with nothing but "????". And i could not continue. 
I searched some topic for this and it seems that i have a fakeRaid. And i have no idea how to partition this in the right way. Do i have to pre-partition this? or the installation software can't support this fake Raid thing? 
Could someone please tell me what to do to install this thing right? And for the "Device for boot loader installation" what do i choose? "/dev/mapper"??

PS the installation does not recognize win7 there are only two installation options erase everything and something else.

---

### Post by ronparent on 2012-10-13
The /dev/mapper/ partitions indicate that your disk was previously formatted for use in a raid setup. Since it appears you are not now using raid, the metadate on your ssd marking it as a raid drive should be erased. Verify that you do not actually have two ssd's and erase the raid metadata on it.  This can be done from a live session either on a cd or usb. You need to open a 'terminal' and write the instructions into the terminal session. 
> 
sudo **sudo dmraid -rE /dev/sda**

I haven't browsed this forum in months and am unlikely to return soon. So please excuse me if I don't return for additional guidance. But others will probably be able to assist you in addressing your problems from this point. I am sure that once the unneeded metadata is removed you should have little problem with a normal install! Good luck.

---

### Post by darkod on 2012-10-13
+1

Remove the fakeraid meta data with the above mentioned command. After that the installer will see the disk correctly. The device for bootloader is always the disk itself, in other words /dev/sda.

---

