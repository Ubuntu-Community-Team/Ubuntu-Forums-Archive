---
title: "Is there any way I can continue or repair a partly failed ubuntu install ?"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by re1n0ut on 2010-01-21
Hello, I've a fairly simple problem but I don't seem to find an answer anywhere.

I have a sony vaio vgn-AR71s with dual boot Vista and Ubuntu, no problems there.

Since, over time, I messed up my previous Ubuntu setup while trying to get my wifi working, I decided to reinstall the whole thing and give it a fresh start. (as after two Kernel updates my wifi card drivers should be supported)

I Reïnstalled Vista and drivers after which I downloaded the latest Ubuntu 9.10 LiveCD, burned to a disc and rebooted.
When the Ubuntu installation was almost finished I got an error, the disc I was using got overheated (bad quality CD) and there was a problem copying certain files. However my hard disk was successfully partitioned and divided in half (1st partition Vista -NTFS and second Ubuntu -Ext4). But my laptop still boots directly into Vista ignoring the partly failed Ubuntu install, no boot option at startup.
When I reboot using the LiveCD I can only install Ubuntu on a newly created third partition.

Is there any way I can continue or repair the previous ubuntu install ?
I searched this forum and the internet for options and hints yet don't seem to find an answer.

The good thing is my wifi card is finally working (when I booted from the LiveCD it immediately detected wireless networks :D yeay)

Thanks in advance,
r

---

### Post by howefield on 2010-01-21
Boot to the desktop with the Live CD, then load up System > Administration > GParted.

Format the existing Ubuntu partition and then install into it.

---

### Post by presence1960 on 2010-01-21
Since it is a new install it is probably better to do what howefield suggests...unless you want to spend some time troubleshooting and trying to find out what packages are missing, etc and installing them.

---

### Post by re1n0ut on 2010-01-22
Thanks for the fast replies, heres what I did : 

As suggested I formatted the Ubuntu partition but still got the same issue as setup wanted to create an additional partition for the new Ubuntu install.
[I]I should note that the Live CD did take a suspiciously long time to start up, after I tried to reboot I got a load of squashfs errors. So I reburned the Live CD on a new disc and continued :
[/I]I 'de-swapped' the swap partition and deleted it, after which I deleted the Ubuntu partition and created a new one filling the empty space which I formatted in Ext4.
Restarted the installation and all went smooth from there.

Just one more thing though, I couldn't get Ubuntu to use the entire partition leaving me with a total of 4 partitions : 1. Vista 2. dev/sda5 3. dev/sda6 Ubuntu 4. Swap
The number 2 partition is a little gap between the Vista and Ubuntu partition, is that because I used the slider to define Ubuntu's partition size instead of doing that manually ? Or is there a better way to install Ubuntu to an existing partition ?
It doesn't bother me that much as I'm sure that in a few months from now I'll have to do this all over again.

---

### Post by mocoloco on 2010-01-22
Yes, the better way is to pick "manually select partitions" or whatever the option is called.  Then you select your ext4 partition, set / as the mount point, and make sure it's marked to format it.  You may also have to select the swap partition to be used as swap.  No need to remove and re-add partitions, just tell it to format them and use them.

---

### Post by re1n0ut on 2010-01-22
Thanks, should've checked that option earlier ! I'll keep that in mind for future installations. Now that my wifi is working I'm moving on to the next peripheral : webcam.
Gradually I will get the hang of this.

grtz.r

---

