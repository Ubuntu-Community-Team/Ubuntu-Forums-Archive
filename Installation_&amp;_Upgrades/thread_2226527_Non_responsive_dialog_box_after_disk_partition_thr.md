---
title: "Non responsive dialog box after disk partition through &quot;Something Else&quot; option"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by gokul2 on 2014-05-27
Hi,
I have a Alienware m17xR4.  I have windows 7 already installed in it. I'm trying to install Ubuntu 14.04 LTS for dual booting. I'm using USB drive to boot the Ubuntu ISO. I tried installing ubuntu directly,but I have repeatedly faced the same problem with the installing, I loaded ubuntu demo and then tried installing ubuntu so I can print screened the following and update here. 

[IMG]http://s24.postimg.org/o9ramflrp/Screenshot_from_2014_05_27_22_17_37.png[/IMG]
Unlike most step by step guides for installing, I'm not getting the option for installing ubuntu along side. Instead, only the advanced user option is given.


[IMG]http://s24.postimg.org/9o09y6oz9/Screenshot_from_2014_05_27_22_18_09.png[/IMG]
The highlighted partition is the swap area i had previously created after going through once such guide.


[IMG]http://s24.postimg.org/5b1qfrg8l/Screenshot_from_2014_05_27_22_18_24.png[/IMG]
I deleted that partition and got it as free space. Then, I added a new partition of the 2gb free space into a swap area using create partition dialog box. 


[IMG]http://s24.postimg.org/528r3kstx/Screenshot_from_2014_05_27_22_18_44.png[/IMG][IMG]http://s24.postimg.org/xckd77awl/Screenshot_from_2014_05_27_22_19_08.png[/IMG]
Above the highlighted partition, the swap was created. Now, I deleted this 30GB partition into free space. Then using create partition, I created a ext4 file system with "/" as mounting point. 


[IMG]http://s24.postimg.org/hfllahiid/Screenshot_from_2014_05_27_22_19_53.png[/IMG]
You can see that the partition was created. I leave the Device for boot loader intallation: as /dev/sda


[IMG]http://s24.postimg.org/awo5jtgxh/Screenshot_from_2014_05_27_22_20_05.png[/IMG]
Once I click on "Install Now", after sometime of processing, this dialog box pops out. 


[IMG]http://s24.postimg.org/unkz3fg1h/Screenshot_from_2014_05_27_22_20_13.png[/IMG]
If I let the installation be without doing anything, in less than a minute the installation window changes to where are you? But even after clicking on OK or close button of the dialog box, it never closes and this is the end to my installation. I'm not able to proceed any further and only way to restart is to use "xkill" in terminal to force quit the application. 
Sorry about the big post. Am I making any mistake in the process? The ISO is the latest I have downloaded just an hour or so ago.


I'm not exactly sure if this post is a replica of something which was  posted in the past but all my search keywords failed me. If at all this  is a repeat then I apologise in advance.

---

### Post by gokul2 on 2014-05-28
Has anyone else atleast faced a problem similar to this or have seen posts similar to this?

---

### Post by gokul2 on 2014-06-03
Its been a week now. Can any moderator please help me out?

---

