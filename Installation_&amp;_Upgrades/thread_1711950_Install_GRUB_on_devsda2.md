---
title: "Install GRUB on /dev/sda2"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by m.milway on 2011-03-22
A normal installation of GRUB puts it on the MBR. I would like to install it on my root partition and leave the MBR alone. I would then make the root partition the active partition.

How do I do this? I haven't seen an option during the install sequence that allows me to choose its location.

Regards,
Michael Milway
University of Wollongong

---

### Post by mikewhatever on 2011-03-22
Go with the manual partitioning option, then there is a menu down the bottom to select where grub is installed.

---

### Post by m.milway on 2011-03-28
I have just tried another installation using manual partitioning. I cannot see an option for specifying the GRUB instalation.

I am using the 10.04 LTS standard desktop install DVD. Am I just being blind or do I have to use a dfferent install disk to get the GRUB options?

Regards,
Michael Milway
University of Wollongong

---

### Post by wilee-nilee on 2011-03-28
> **m.milway said:**
> I have just tried another installation using manual partitioning. I cannot see an option for specifying the GRUB instalation.

I am using the 10.04 LTS standard desktop install DVD. Am I just being blind or do I have to use a dfferent install disk to get the GRUB options?

Regards,
Michael Milway
University of Wollongong

If you choose the custom install at the bottom of the first gui is a dropdown where grub is pointed.

---

### Post by oldfred on 2011-03-29
Herman has detailed instructions and pictures:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

See the combo box at the bottom:
[http://members.iinet.net.au/~herman546/p24/029.png]("http://members.iinet.net.au/%7Eherman546/p24/029.png")

Note that grub2 installed to the PBR has to use blocklists which are hard coded addresses on the drive for the rest of the boot files. If something gets moved it breaks grub & you have to reinstall it to the PBR. It is not considered as reliable in the PBR.

---

### Post by m.milway on 2011-03-30
Thanks for you help. I have finally worked it out.

(1) The option to install GRUB2 on /dev/sda2 is found in the advanced option on the last step, just before installation. I was looking for this option in the step where the partitions are specified.

(2) I found I could only specify GRUB2 to be installed on partitions that already existed. These were the MBR and the Windows partition, /dev/sda1 (hands up all those who think instaling GRUB on the Windows partition is a sily idea). Since the Linux partitions had not yet been created created the option to use /dev/sda2 was not available. I solved this by creating the partitions in advance and then specifying the Linux install to use them.

(3) I tested update-grub and found that it only updated the boot record of /dev/sda2, which is what I expected.

(4) I had to manually set the Linux partition as the active partition.

Regards,
Michael Milway

---

