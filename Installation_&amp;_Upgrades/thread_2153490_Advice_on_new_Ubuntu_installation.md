---
title: "Advice on new Ubuntu installation"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by MarcusL on 2013-06-11
UPDATE:
Bought Adapter controller and Installation completed OK

************************************

I am upgrading my Ubuntu server this week and I am seeking expert advice.

I have been running for the last 2 years the server with Ubuntu 11.04 and a raid 6 partition across 10x2TB drives and ext4 fs.

The server essentially is a backup space and multimedia storage.

The box is an old core 2 quad, Asus mobo, lsi sata card.

I will upgrade to the latest Ubuntu x64 server and install 10x4TB wd black drives.

Questions:
I want one partition raid6 (30TB). It needs to be accessible by windows pcs. What fs should I use?

Can this be done? A partition this size?

Any advice in the most efficient way to set up is highly appreciated.

Thank you in advance for your help!
MarcusL

---

### Post by Cheesemill on 2013-06-12
> **MarcusL said:**
> I will upgrade to the latest Ubuntu x64 server and install 10x4TB wd black drives.
Do you have a good reason for wanting to use 13.04 instead of 12.04? Support for 13.04 runs out in January so you would need to upgrade your OS again in around 6 months.
For servers it is recommended to only use LTS releases unless you ***have*** to have features that are only found in the newer versions. The current LTS release is 12.04 which is supported until 2017.

> I want one partition raid6 (30TB). It needs to be accessible by windows pcs. What fs should I use?
The fact that you want to access the files from Windows machines doesn't matter at all when choosing a filesystem. You can use whatever you want as the client machines talk to the server via Samba, not directly to the drives. The only native Linux filesystems that will handle a 30TB partition are ext4, XFS, JFS and btrfs. Personally I would go with ext4. Also make sure you use GPT partitioning with your drives instead of the old msdos style partitioning otherwise there is a limit of 2TB capacity per drive.

---

### Post by MarcusL on 2013-06-15
Hey Cheesemil,
Thanks for the reply! You are right, 12.04 is just fine. I will follow your advice on this.

I have run into a different problem now (of course!!) as I just finished (1/2 hr ago!) building the HW. I now have the issue of my old LSI 4 port SATA PCI card not working to see the drives as 4TB, it sees them as 2TB. The on board 6x SATA II ports of my P5K Deluxe (ASUS) are working just fine and even the OS sees the drives as 4TB.

I am researching for a PCI/PCIe 4 port internal SATA II controller to buy and replace my LSI. I have come across this one:

[http://www.dinodirect.com/4-Ports-SIL3124-SATA-II-3Gbps-PCI-RAID-Express-Card.html?vn=RGlub2RpcmVjdEZ1Y2s&cur=AUD&affid=97&utm_source=myshopping&utm_medium=cpc&utm_campaign=HDD+Accessories&utm_term=4+Ports+SIL3124+SATA+II+3Gbps+PCI+RAID+Express+Controller+Card&CA_6C15C=652531672](http://www.dinodirect.com/4-Ports-SIL3124-SATA-II-3Gbps-PCI-RAID-Express-Card.html?vn=RGlub2RpcmVjdEZ1Y2s&cur=AUD&affid=97&utm_source=myshopping&utm_medium=cpc&utm_campaign=HDD+Accessories&utm_term=4+Ports+SIL3124+SATA+II+3Gbps+PCI+RAID+Express+Controller+Card&CA_6C15C=652531672)

Is there a place I can find supported/compatible 4x Port PCI/PCIe SATA II controllers that work just fine with Ubuntu as well as see the 4TB drives?

Thanks for any help in advance!

M

---

### Post by Cheesemill on 2013-06-15
Before buying any new hardware it may be possible to flash the firmware of your current card to recognise the larger drives.

Can you post the exact make and model number of your card please.

---

### Post by MarcusL on 2013-06-15
Hi Cheesemill,
Thanks again for the help.

My card is an LSI manufactured, IBM branded, SAS3444E. Its FRU number (from a sticker on the card): 25R8071. During post I can see the following on the screen: "SAS 1068E-IR 1.30.1.00 NV 2D:13".

I had managed to flash this card 2 years ago when I first set up the server. The firmware gave me BIOS 6.30.00.00. 

I have found earlier tonight the following firmware (BIOS 6.30.02.00.): [http://delivery04.dhe.ibm.com/sar/CMA/XSA/036o1/2/ibm_fw_mptsas_3g-sashba-2.75_windows_32-64.chg](http://delivery04.dhe.ibm.com/sar/CMA/XSA/036o1/2/ibm_fw_mptsas_3g-sashba-2.75_windows_32-64.chg). When I try and upload the firmware (via DOS bootable) I get a msg: "ERROR: The firmware Image is for a 106e b3 LSI SAS Controller, but the target adapter is a 106e b1 LSI SAS Controller."

As a matter of fact, a sasflash -listall shows "LSI SAS 1068E(B1), FW: 01.30.10..00, NVDATA: 2d.13, x86-BIOS: 06.30.00.00, EFI-BSD: 03.16.00.06, PCI Addr: 00:04:00;00"

I have not been able to find anything else to flash the card with. 

I have booted to the partitioning step of the install process and Ubuntu can definately see 6x 4TB drives on the on board controllers, but the 4x on the LSI it lists at 2.2TB.

If I cannot get this thing flashed, what PCIe 4x Port SATA II controller can you recommend? 

Thanks again for your help!

M

---

### Post by MarcusL on 2013-06-15
Update:

Following the steps in this post [http://hardforum.com/showthread.php?p=1038602393](http://hardforum.com/showthread.php?p=1038602393) I managed to flash the adapter to a std LSI FW & ROM, of a later date than what I had. I got the rom from here [http://www.lsi.com/channel/support/Pages/downloads.aspx?r=productfacet%3D%22AR8BTFNJIFNBUyAzMDgxRS1SOyBMU0kgU0FTMzA4MUUtUgxwcm9kdWN0ZmFjZXQBAl4iAiIk%22]("http://www.lsi.com/channel/support/Pages/downloads.aspx?r=productfacet%3D%22AR8BTFNJIFNBUyAzMDgxRS1SOyBMU0kgU0FTMzA4MUUtUgxwcm9kdWN0ZmFjZXQBAl4iAiIk%22")

Sasflash now shows: [COLOR=#000000]LSI SAS 1068E(B1), FW: 01.33.10..00, NVDATA: 2d.03, x86-BIOS: 06.36.00.00, EFI-BSD: 03.16.00.06, PCI Addr: 00:04:00:00
[/COLOR]
Drives still seen as 2TB... Still cannot access the LSI Config Utility...

---

