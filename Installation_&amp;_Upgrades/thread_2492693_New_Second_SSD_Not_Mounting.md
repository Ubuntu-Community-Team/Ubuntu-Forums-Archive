---
title: "New Second SSD Not Mounting"
date: 2023-11-20
forum: Installation &amp; Upgrades
---

### Post by thespeth on 2023-11-20
I've purchased  a second SSD and installed on my motherboard.

Motherboard is ASRock B450M Pro4 ([https://www.asrock.com/mb/AMD/B450M%20Pro4/index.asp](https://www.asrock.com/mb/AMD/B450M%20Pro4/index.asp)), and I installed the new SSD in the second M2 slot.

First SSD is an HP EX900 M.2 500GB ([https://www.newegg.com/hp-ex900-500gb/p/N82E16820326251](https://www.newegg.com/hp-ex900-500gb/p/N82E16820326251)) and has Ubuntu installed on it.  Second, new SSD is HP EX900 M.2 2280 1TB ([https://www.newegg.com/hp-ex900-1tb/p/N82E16820326786](https://www.newegg.com/hp-ex900-1tb/p/N82E16820326786)), essentially same SSD with just double the space.

Disks menu has my first SSD, an additional old 500gb drive I'm using for storage, and then lists a third pluggable SD card reader - the new 1TB drive doesn't appear at all.

Any suggestions here on how to get it appearing and formatted for use?

---

### Post by MAFoElffen on 2023-11-20
First, do this
```

lsblk -e7 -o name,model

```
Post the output within CODE Tags.

---

### Post by thespeth on 2023-11-20
I couldn't run fsblk (Command 'fsblk' not found), but this is the output for "lsblk -e7 -o name,model"

```

lsblk -e7 -o name,model
NAME        MODEL
sda         ST500DM002-1BD142
&#9492;&#9472;sda1      
sdb         SD/MMC/MS PRO
nvme0n1     HP SSD EX900 500GB
&#9500;&#9472;nvme0n1p1 
&#9492;&#9472;nvme0n1p2 
```

---

### Post by oldfred on 2023-11-20
So you have latest UEFI firmware?
Is drive shown in UEFI settings?

Does motherboard have limits on drives. Some prevent a SATA  port from being used if NVMe drive installed.
Check motherboard manual.

---

### Post by MAFoElffen on 2023-11-20
Sorry for the typo. See you guessed correctly...

@oldfred. Usually, if it shows in that output, then the UEFI BIOS see's it...

Next, I would look at the partition table, and filesystem type
```

sudo blkid | grep '/dev/sda'

```

---

### Post by thespeth on 2023-11-20
I've updated the firmware to the latest non-beta version, 5.7, from the ASRock website ([https://www.asrock.com/MB/AMD/B450M%20Pro4/index.us.asp#BIOS](https://www.asrock.com/MB/AMD/B450M%20Pro4/index.us.asp#BIOS)).

M2 port 2 shares lanes with SATA 3_3 according to the manual ([https://download.asrock.com/Manual/B450M%20Pro4.pdf](https://download.asrock.com/Manual/B450M%20Pro4.pdf)) - I've disconnected all of the SATA connections there (had one extra HDD and a DVD drive).

On the UEFI screen, the original 500GB drive is the only one that appears.  I thought maybe I didn't have it seated correctly, so I pulled it out and seated it again - seems (and did at the beginning) to be in the slot correctly.

Output code

```
/dev/sda1: LABEL_FATBOOT="asrockbios" LABEL="asrockbios" UUID="A437-3FD7" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="0069b612-01"
```

---

### Post by MAFoElffen on 2023-11-20
I asked for just /dev/sda, which would have included the drive and all partitions... Wait, that partition is formatted as vfat?

Fire up, GParted. Go to that drive. Does it show up?

If so, go to "Devices". Give it a new GPT partition table. That will clear that partition and ensure you have  a new, clean GPT partition.

Create a new partition and format it as ext4. Apply.

Close. Reboot so that the system re-reads the partition tables and filesystem uuid's.

Test to see if you can mount it.

Yes. My MSI board is the same. But with mine, it is M.2 slot #3. If I have an NVMe drive in that slot, then it disables SATA port #7. I first thought there was something wrong. Then found out that was just how it is. I figure vendors are still working out bifurcation technologies. ASUS does have the strangest "peculiarities" with that. I had to dig into the fine print of their manuals to really see what they were. They are not things that are stated out-front in their marketing.

EDIT: If I am adding storage to my own machines, as a general rule, I don't allocate all the space all at once. Things happen when you don't expect them. I usually leave some unallocated space for emergencies, where I can then use it where I need it. That strategy has saved my systems many times over the years.

---

### Post by thespeth on 2023-11-20
OK so there's definitely something quirky with the M2 slot - I swapped the SSD cards and the new 1TB in slot 1 works fine ( installed Ubuntu), and the old 500GB SSD in slot 2 doesn't show up at all.

Edit: New outputs for the above commands:

```
lsblk -e7 -o name,model
NAME        MODEL
nvme0n1     HP SSD EX900 1TB
&#9500;&#9472;nvme0n1p1 
&#9500;&#9472;nvme0n1p2 
&#9492;&#9472;nvme0n1p3 
```

```
sudo blkid | grep '/dev/nvme0n1'
/dev/nvme0n1p3: UUID="33ace5fc-e5e5-4ed1-8d6b-c4a2cc190e4b" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="bef39538-8eaf-444f-bbe3-02abc2f2417d"
/dev/nvme0n1p2: UUID="5DB7-442E" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="274d2137-ba0a-4213-b806-a3fde862fcaa"
/dev/nvme0n1p1: PARTUUID="b846074c-b836-49fe-94fa-6e13d48300da"
```

Edit 2: I've submitted this to ASRock to see if I can get assistance from their side with tech support, but I'm definitely open to suggestions and recommendations here, as well.

---

### Post by MAFoElffen on 2023-11-20
Here is what your manual says on pages 4 & 28:
> 
M2_2 and SATA3_3 share lanes. If either one of them is in use,
the other one will be disabled

In the BIOS section, there is only 3 setting for SATA, and nothing that really mentions the M.2 ports.

Yes, I would call their support and see what is going on. It is almost like there is a digital switch that is stuck, not recognizing that there is nothing in SATA port #3.

---

### Post by oldfred on 2023-11-20
[https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199](https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199)

Looks like type of video can interfere with M.2 slot.
If Vega GPU is built into the CPU, then the M.2_2 socket cannot be used.

---

### Post by thespeth on 2023-11-21
My CPU is an AMD Ryzen 5 2600 Pinnacle Ridge - I don't see anything specifically in the model information for it ([https://www.amd.com/en/product/7666](https://www.amd.com/en/product/7666)) that would be a red flag based on the requirements in the ASRock manual, but I might be missing it.

```
Vendor ID:               AuthenticAMD
  Model name:            AMD Ryzen 5 2600 Six-Core Processor
    CPU family:          23
    Model:               8
```

---

### Post by MAFoElffen on 2023-11-23
That says it has no iGPU...

Found this support Doc at ASUS Support: [https://www.asus.com/support/FAQ/1044083/](https://www.asus.com/support/FAQ/1044083/)

Note this other quark from it:
> 
M.2_2 port can only support PCIE mode and can't support SATA mode. Therefore, if you connect SATA mode M.2 SSD to M.2_2 port, the computer can't recognize.

But it further said that; "These sockets support IRST (Intel Rapid Storage Technology).

Which would mean that if your board supports IRST, to use the slot as m.2, you would have to ensure that IRST was switched off in the BIOS Settings. Right?

---

### Post by thespeth on 2023-11-28
Response from ASRock:

After reading from the user manual , your motherboard comes with two M2 
M.2 slot 1 support NVMe (PCIe) drives only
M.2 slot 2 support SATA drives only
Therefore you can not install NVMe drive in the second slot

[IMG]https://i.imgur.com/Ita1oGK.png[/IMG]

---

### Post by MAFoElffen on 2023-11-29
That explains that. Dang.

There are NVMe m.2 drives that are SATA... Such as: [KingSpec M.2 2280 1TB SSD NGFF M.2 SATA III]("https://www.newegg.com/kingspec-1tb-m-2-sata3-2280-ssd/p/0D9-000D-00136?item=9SIB1V8FND9878&source=region&nm_mc=knc-googlemkp-pc&cm_mmc=knc-googlemkp-pc-_-pla-kingspec+official++store-_-solid+state+disk-_-9SIB1V8FND9878&utm_source=google&utm_medium=paid+shopping&utm_campaign=knc-googlemkp-pc-_-pla-kingspec+official++store-_-solid+state+disk-_-9SIB1V8FND9878&id0=Google&id1=20802659459&id2=153836786057&id3=&id4=&id5=pla-2261361220071&id6=&id7=9033423&id8=&id9=g&id10=c&id11=&id12=Cj0KCQiA35urBhDCARIsAOU7QwlxSzhRBwT31wUG8ui1wNwouGLP6ttSueIUmbqdkzf_lHDGQyaj_rsaAiK4EALw_wcB&id13=&id14=Y&id15=&id16=682096980477&id17=&id18=&id19=&id20=&id21=pla&id22=454026778&id23=online&id24=9SIB1V8FND9878&id25=US&id26=2261361220071&id27=Y&id28=&id29=&id30=4582147042677740824&id31=en&id32=&id33=&id34=&gad_source=1&gclid=Cj0KCQiA35urBhDCARIsAOU7QwlxSzhRBwT31wUG8ui1wNwouGLP6ttSueIUmbqdkzf_lHDGQyaj_rsaAiK4EALw_wcB")

---

### Post by Dennis N on 2023-11-29
You can buy an inexpensive adapter to use an NVMe m2 drive with a PCIe slot instead of the SATA only m2 slot. I use one myself when I had only one m2 slot available. You can look into this.

---

### Post by MAFoElffen on 2023-11-29
> **Dennis N said:**
> You can buy an inexpensive adapter to use an NVMe m2 drive with a PCIe slot instead of the SATA only m2 slot. I use one myself when I had only one m2 slot available. You can look into this.
I have 2 each PCIe x1 NVMe PCIe M.2 cards (that have 1 slot each) that I have in one of my servers to bump it up to 7 NVMe's. They run full speed and I am very happy how they worked out for me.

They are NVMe5 & NVMe6 below. I'm using both as disk caches for my  5 disk RAIDZ2 datapool (L2ARC & SLOG)
```

mafoelffen@Mikes-B460M:~$ lsblk -e7 -o name,label,size,fstype,model
NAME        LABEL      SIZE FSTYPE     MODEL
sda                    1.8T            Samsung SSD 870 EVO 2TB
&#9492;&#9472;sda1      datapool   1.8T zfs_member 
sdb                    1.8T            Samsung SSD 870 EVO 2TB
&#9492;&#9472;sdb1      datapool   1.8T zfs_member 
sdc                    1.8T            Samsung SSD 870 EVO 2TB
&#9492;&#9472;sdc1      datapool   1.8T zfs_member 
sdd                  476.9G            Crucial_CT512MX100SSD1
&#9500;&#9472;sdd1                  16M ext4       
&#9500;&#9472;sdd2               476.3G ntfs       
&#9492;&#9472;sdd3                 607M ntfs       
sde                    1.8T            Samsung SSD 870 EVO 2TB
&#9492;&#9472;sde1      datapool   1.8T zfs_member 
sdf                    1.8T            Samsung SSD 870 EVO 2TB
&#9492;&#9472;sdf1      datapool   1.8T zfs_member 
nvme3n1                1.8T            Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme3n1p1 kpool      1.8T zfs_member 
nvme4n1              931.5G            WD Blue SN570 1TB
&#9500;&#9472;nvme4n1p1            512M vfat       
&#9500;&#9472;nvme4n1p2              2G swap       
&#9500;&#9472;nvme4n1p3 bpool        2G zfs_member 
&#9492;&#9472;nvme4n1p4 rpool      927G zfs_member 
nvme6n1                1.8T            Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme6n1p1 datapool  1000G zfs_member 
nvme2n1                1.8T            Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme2n1p1 kpool      1.8T zfs_member 
nvme0n1                1.8T            Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme0n1p1 kpool      1.8T zfs_member 
nvme1n1                1.8T            Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme1n1p1 kpool      1.8T zfs_member 
nvme5n1     datapool   1.8T zfs_member Samsung SSD 970 EVO 2TB
&#9500;&#9472;nvme5n1p1            1.3T zfs_member 
&#9492;&#9472;nvme5n1p2 datapool    10G zfs_member 

```

---

### Post by thespeth on 2023-11-30
Any recommendations for brand or model, or are they basically the same?

---

### Post by MAFoElffen on 2023-11-30
I found mine on Amazon... [https://www.amazon.com/ACTIMED-Powerful-Dissipation-Compatible-Interface/dp/B09FLGR1X9?th=1](https://www.amazon.com/ACTIMED-Powerful-Dissipation-Compatible-Interface/dp/B09FLGR1X9?th=1)

It was about the middle of the price range of the ones I looked at, but had an included heat sink and had very good reviews. LOL. Looks like right now, it is less than what I paid for both of mine.

The only thing that was strange, after I installed them, is that the Ethernet port shifted it's device name... NIC's go by enp#s#, with the first Number being the PCIe bus number, Adding those 2 cards shifted that number.

---

### Post by Dennis N on 2023-11-30
> **thespeth said:**
> Any recommendations for brand or model, or are they basically the same?

What PCIe slot is available? Your new PCIe 3.0 NVMe drive can use 4 data lanes, so get an adapter that can utilize 4 data lanes. A x 4 (4 lane) adapter will fit into one of the x 16 slots on that board. Using the 3.0 x 16 slot is best. The 2.0 x 16 slot will transfer data at 1/2 the speed.

If you get a PCIe x 1 adapter, it would work, but slow down the data rate considerably.

---

### Post by MAFoElffen on 2023-11-30
As disk caches for my SSD Arrays's, their IOPS benchmark's at over 11GB/s. They are in the right spot for what they do. But 4 lanes would be better. Even Gen5 M.2 slots on motherboards only use 4 lanes for each m.2 slot, max. 

If he had 16 lanes open, he could add more M.2 4 slots... Cheaper if he has bifurcation support on his motherboard. Otherwise, the card has to have a bifurcation chip on the card. This is how I have 7 M.2's in one server and 11 M.2's in the other. In the results I posted above nvme[1-4] are on that card.

This is the sustained writes on the 4 drive RAIDZ2 array I have setup on that card:
```

Run status group 0 (all jobs):
  WRITE: bw=2377MiB/s (2492MB/s), 2377MiB/s-2377MiB/s (2492MB/s-2492MB/s), io=10.0GiB (10.7GB), run=4308-4308msec

```
That is one of my VM storage pools for that server. 

Both my servers have a PCIe Quad m.2 adapters with onboard bifurcation... This is the card I use for that (and I am very happy with): 
[M.2 Key SSD Expansion Card ANM24PE16 4-Port PCIe3.0 X16 With PLX8748 Controller]("https://www.aliexpress.us/item/3256801158360351.html?spm=a2g0o.order_list.order_list_main.11.54a0180248brsl&gatewayAdapt=glo2usa")

That is the manufacturer. I figured out that buying directly from them saved me about 75% off the retail. Their customer service is great!!! One had a cross threaded nut, I asked for a replacement and a spare. They actually sent me about 20 spares or every type it took! I am a very happy customer, I highly recommend it.

---

### Post by Dennis N on 2023-11-30
Yes, those cards that support more than one NVMe drive are certainly an option. It depends on how much storage you need. 

I have 2 x 1TB NVMe m2 drives installed (one uses the PCIe expansion card), which is way more storage than I have a need for.

---

