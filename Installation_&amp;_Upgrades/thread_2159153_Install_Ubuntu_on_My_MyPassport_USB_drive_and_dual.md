---
title: "Install Ubuntu on My MyPassport USB drive and dual boot with Windows 7 Laptop"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by wdavro on 2013-07-02
Can someone perhaps point me to the thread that documents setting up the following scenario.  I know it's here somewhere but I just can't figure out how to find it.

I have a company provided Win 7 laptop (Lenovo T420s-64bit).  I also have a 500GB portable USB drive with Ubuntu 12.04 (actually, an 80GB Ubuntu boot partition and a 400GB NTFS partition).
When the USB drive is NOT plugged into the laptop, the laptop boots directly to Win7.
When the USB drive is plugged in, it boots to a grub menu asking me to choose between Ubuntu 12.04 (on the usb) and Windows7 (on the laptop).
I also have a powered USB3 hub that plugs into the laptop and I can plug in and see both USB drives, from both Ubuntu and Windows.

I just bought a 2TB MyPassport USB3 drive.  
I also have a Ubuntu 13.04 64bit desktop CD (although I'm not married to it - I need to be functional more often than not so I'd be fine with putting 12.04 on the 2TB drive if that would be safer).

I want to make the 2TB usb drive duplicate the above boot characteristics.
I can NOT afford to mess with my laptop drive in anyway.  I have no recovery material for Windows 7.  If it gets damaged I will have to ship it back to corporate (and explain!). Which is what happened the first time I tried to set this scenario up on my own. :(  My boss wasn't happy about my down time.

What would be the best appropriate steps to accomplish my goal?

---

### Post by fantab on 2013-07-02
You can and MUST create Windows7 'Repair Disk'/'Recovery Disk. Plus you can make a complete back up of your Windows partitions: [Try This Tool]("http://www.macrium.com/reflectfree.aspx").

Installing Ubuntu on an external device is similar to installing on HDD. During install you have to take manual contorl of the installation by choosing 'Something Else' at the 'Installation Type' dialog. Additionally you have to make sure that you are installing GRUB-Ubuntu Bootloader on the external device only. 

Since you can already boot into USB device when it is plugged in and to Windows when it is not, you don't have to do anything more. If you forgot how you managed that- its the Disk boot order/priority in BIOS settings set to boot USB devices first. 

Regarding Partitions:
20-30GB Primary Ext4 for '/' (where Ubuntu system files are installed 20GB is more than enough and 30GB is plenty)
To store your data you can either have separate '/home' partition or have a simple ext4 formatted partition to house your DATA. You can also have an NTFS partition to share data between Windows and Ubuntu.
Do not forget to have atleast 2GB of SWAP partition. If you hibernate your Ubuntu then SWAP size should be equal to or more than your RAM in GiB, not GB.

I am sure you are aware of the 4 Primary Partition limit on 'msdos' partition table. To have more partitions you can make your 4th Primary Partition as EXTENDED and create Logical partitions within it.

Good Luck....

---

### Post by oldfred on 2013-07-02
+1 on fantab's suggestions.

You must not use any of the auto install options as they will install grub2 to sda which is the internal drive.
Even with Something Else you have to change the combo box on the bottom of the partitioning screen from the default of the internal drive to the external drive but not any partitions shown also. Grub2's boot loader must be in the MBR of the new drive.

Also with external hard drives you should keep the / (root) partition fully within the first 100GB. If you folllow fantab's suggestion of a smaller root that should be fine. Some systems have issues with BIOS or grub and very large / partitions.
This shows combo box open with several drives and partitions. Your version may be slightly different but work the same way.
 Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

