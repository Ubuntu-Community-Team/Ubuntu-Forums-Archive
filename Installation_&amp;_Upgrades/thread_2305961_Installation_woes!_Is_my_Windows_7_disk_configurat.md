---
title: "Installation woes! Is my Windows 7 disk configuration hosing up ubuntu?"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by john496 on 2015-12-10
I want to explore Linux so I've been researching how to install Ubuntu 14.04 with my Win 7 installation. I wanted to install it on my Windows boot drive but apparently I have too many partitions there so I decided to put it on my second physical drive. But everything I found about doing that started with deleting everything that was already on the drive. (If I didn't want what was on the drive, I wouldn't even have the drive in the first place!) 

Anyway, after hours and hours of research, I decided to do my research from within Ubuntu using the live DVD. I had Firefox up for maybe 30 minutes when it crashed. I tried restarting it but it crashed again immediately. I decided to try and find another browser inside Ubuntu but nothing was working so I closed it down and when I did I saw an error message that had been "behind" the desktop. Sorry, I didn't write down what it said.

At that point I got frustrated and decided to just install Wubi instead of going the route I wanted to. After a really long installation process (Where it scared the #$%* out of me by talking about partitioning drives without showing me what it was doing!) the Windows dual boot screen came up just fine. When I chose Ubuntu I was presented with a choice of "Ubuntu" or "Ubuntu advanced options." (If I remember correctly.) I sat there wondering what to do and the whole computer just shut down.

At that point I decided to just forget the whole thing rather than risk my Windows setup. But :p today I'm interested again so... I've seen some forum posts where people talked about Ubuntu having problems with too many Windows partitions, even if it was installed on a different physical drive and I'm wondering if that could be my situation. Below is my drive setup. I was going to shrink the I: partition on the smaller drive to make room. (Note that the smaller drive is disk 0 and disk 1 is my boot drive.) 

I'd like to know how to install Ubuntu on the smaller drive without deleting the existing partitions, and also any info about my whole situation.
Thanks for any help.

[ATTACH=CONFIG]266086[/ATTACH]

---

### Post by ian-weisser on 2015-12-10
One simple way to install Ubuntu without risk is to use a VM. Several fine VM hosts are available for Windows.

WUBI is strongly discouraged. It is no longer supported, and is not compatible with newer versions of Windows.

---

### Post by grahammechanical on 2015-12-10
It looks to me that you have MBR partitioning. That means that you are allowed a maximum of 4 primary partitions. To have more than 4 partitions we use one of the allocated primary partition slots to create a special primary partition called an Extended partition and then inside the Extended partition we can create any number of Logical partitions. Your arrangement:

Disk 0 = 1 primary partition used as an extended partition & inside that 2 logical partitions (D: Languages & I: Stuff)

Disk 1 = 4 primary partitions one of which is an extended partition inside which are 2 logical partitions (Photgraphy & Data) + 236.88 GB unallocated space. Outside the extended partition is a further 254.42 GB unallocated space.

Your choices:

a) Disk 0 = shrink Languages & Stuff to create unallocated space for 2 more logical partitions and install Ubuntu into those 2 new logical partitions. One for Ubuntu & one for swap. 

b) Disk 1 = use the 236.88 GB unallocated space inside the extended partition to create 2 new logical partitions to install Ubuntu in. In addition you have the option of expanding the extended partition to take up the 254.42 GB unallocated space. You cannot create any more primary partitions on Disk 1 but you can create more logical partitions inside the Extended partition and give the logical partitions more space.

Regards.

Regards

---

### Post by SeijiSensei on 2015-12-10
I strongly recommend installing [VirtualBox]("https://www.virtualbox.org/") for Windows, then installing Ubuntu into a virtual machine using that program.  Running Linux in a virtual machine is an easy way to gain some experience with the operating system without the hassle of dealing with dual-booting.

---

### Post by oldfred on 2015-12-11
Virtual box is a good alternative.

But if you want dual boot with 2 drives you should only use something else. You have to manually create partitions / (root) & swap. But then you get to choose sizes of partitions and where to install grub2's boot loader. With two drives better to have Windows & its boot loader on one drive and Ubuntu and its grub2 boot loader on other drive. And set BIOS to boot grub2 which will let you chain load/boot to Windows.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by john496 on 2015-12-11
I appreciate all the replies. I'm considering my options.

---

