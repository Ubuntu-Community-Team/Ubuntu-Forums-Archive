---
title: "[SOLVED] Wrong Installation Place"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by je2911 on 2008-09-26
Hi, I'm new in this forum. I have problem with my hardy installation.
I was installing ubuntu beside win xp, and then uninstall for some period, until one week ago I decided to re-install the hardy. 
But I just now realized that I did a mistake, I put my installation to a small partition of my harddisk (swap partition?), the screenshot of my disk size is as the following:
[IMG]http://i34.tinypic.com/245hn37.png[/IMG]
sda1 is my windows installation. The ubuntu should be in sda3. Currently it's in sda6. When I open sda3, I also find similar file system folders, which I think it's from my older installation.
Please help how to move my installation to sda3? I don't want to lose all the settings I have now (I've changed the look of my desktop, and downloaded lot of update ~ 230 MB).

---

### Post by je2911 on 2008-09-26
Additional note: I remember because I didn't know what I do, I deleted two records of kernel/installation from sda3 in Grub. So I think there's still ubuntu system in sda3 from my old installation.

---

### Post by Elfy on 2008-09-26
The easiest way would be to resize the new install partition after removing the old one.

You'll need to use gparted on the livecd to do so. For the moment can you install gparted in your install and run it - then screenshot the gparted window.

```
sudo apt-get install gparted
gksudo gparted
```

IT will alos be some help to know what is on sda4

---

### Post by je2911 on 2008-09-26
Hi forest, this is the screenshot of gparted

[IMG]http://i38.tinypic.com/qnl7no.png[/IMG]

Btw, sda4 is ntfs, I don't know how to merge it with the windows partition, so I just fill it with mp3.

---

### Post by Elfy on 2008-09-26
Ok - should be fairly straightforward, although it might take a while. Couple of questions - How much ram do you have? Do you need to hibernate?

Basically you need to do this - delete sda3 and sda7 - resize the extended partition to include the new unallocated space - create a new swap partition and then resize sda6.

Once that's done we can deal with any mounting or swap issues that could arise from changing partitions before you reboot.

It is important that you have backups of any data you can't afford to lose - accidents happen and you are going to be working with partitions.

Sounds worse than it is - but probably likely to take longer than you think.

---

### Post by je2911 on 2008-09-26
hi Forest, good morning (here) and maybe night there. 
Ok, my ram is around 1.75 GB (2 GB less 256 MB for graphic). I don't need the computer to hibernate nor shutdown (I think the weather is good today, no thunder :p). I've checked sda3 for any data and backup. sda2 is new - no data to be backed up there.
So, now, should I go deleting sda3 and sda7? using gparted?

---

### Post by Elfy on 2008-09-27
Ok straightforward job then, but a lot of reading. Open a terminal and run this command to turn off the swap ```
sudo swapoff -a
```Boot the livecd and open partition editor from the system admin menu. There should be no key symbols on the screen once it's opened.

Delete sda3 sda5 and sda7 - apply those. Now you have to get the unallocated space inside the extended partition - right click sda2 - resize that to take up all off the free space - apply. 

Inside the extended partition - resize sda6 to useall of the free space but leaving 512Mb unallocated. Apply

In the remaining free space create a new swap partition. Apply.

The 2 resizes are likely to take a while - do not assume it has crashed, stopped or anything else. Do not turn it off.

Once that has finished we need to check and maybe change a couple of things.

Open a terminal and run ```
sudo blkid
``` this will give you a number like
/dev/sda1: UUID="[COLOR="Red"]ccf8f1c4-97d0-4544-a0ee-04088d5d67a9[/COLOR]" TYPE="ext3" - this is my / drive
/dev/sda3: TYPE="swap" UUID="[COLOR="Blue"]cbd99e21-9789-4ea0-ba9a-09d365321c1d[/COLOR]" - this is my swap

You will need your numbers for the next steps - open a new tab in the terminal with Shft+Ctrl+T so that you still have blkid in the other.

We want to mount your root so that we can access it 
```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sda6 /mnt/tmp
```

Now we can check your menu list first -
```
cat /mnt/tmp/boot/grub/menu.lst
```
Example - 
```
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=[COLOR="Red"]ccf8f1c4-97d0-4544-a0ee-04088d5d67a9[/COLOR] ro quiet splash
```
The first line of my menu list options - find yours and check that the UUID code is the same as the one you have in blkid for sda6.

If you need to change it you can do so in the terminal using nano, backup first - Ctrl+O, enter to save , Ctrl+X to exit. ```
sudo cp /mnt/tmp/boot/grub/menu.lst /mnt/tmp/boot/grub/menu.lst.2709
sudo nano /mnt/tmp/boot/grub/menu.lst
```

Now we will chnge the UUID for fstab - this will have changed, so open the file with nano ```
sudo cp /mnt/tmp/etc/fstab /mnt/tmp/etc/fstab.2709
sudo nano /mnt/tmp/etc/fstab
```

The line in my fstab for swap looks like

```
UUID=[COLOR="#0000ff"]cbd99e21-9789-4ea0-ba9a-09d365321c1d[/COLOR] none            swap    sw              0       0
```

Find the line for swap and change the UUID to the same as you have from blkid. Save the file as above and close the terminal.

You should be able to reboot now with the resized / and changed swap.

---

### Post by je2911 on 2008-09-27
Hi forest. Here's what I did. "swapoff -a" before booting from live cd is not working. When boot from livecd and running gparted, there's still key symbol beside the swaps partition. But I've managed to try this and that and found that right click on swap partition in gparted lists a menu containing "swapoff", so I chose that (after boot livecd) and all the key symbol was gone. After that, I followed your direction, delete and resize. Sda6 become sda5. I had to resize twice, first the sda2 extended, and left 512MB at the end of the harddisk, and second the sda5 (was sda6) ext3, fully resized to the end of extended partition.
Last, I create swap partition in the remaining 512 MB (509.88 exactly), became sda3.
Next step, I changed some command (like sda6 replaced by sda5). Luckily, my UUID in the grub menu was the same as the one in blkid. So I reboot to harddisk, but got error 22. I thought I miss something so I read again your direction, and found about the fstab, so I changed the fstab thing. 
In the fstab, it's still written sda6 and sda7 for linux and swap partition, so beside changing UUID for swap, I also changed the sda number to the new numbers. 
But when I reboot, I still got error 22. 
Need a little more help on this.

---

### Post by Elfy on 2008-09-27
Boot the livecd and run ```
sudo fdisk -l
``` from a terminal - post the output please.

Edit - and ```
sudo blkid
```

Error 22 - wrong partition in grub usually, you can try to reinstall grub. Use the quick start from this page to reinstall grub - it should set it up the menu list for you. When sda6 changed then the partion on which grub was changed.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by je2911 on 2008-09-27
Hi Forest, thanks for your help. I used your link to reinstall grub, after reboot, it displayed the list, but when I chose ubuntu, it said no such partition. I also cannot boot to windows. 
So I tried to press 'e' to see what's inside, and I remember in grub prompt, it's written (hd0,4) not (hd0,5). So when I saw in grub it's written (hd0,5), I just replaced 5 with 4, and it works like charm now. And my harddisk is much more tidy now :-).
After booting to linux, I edit menu.lst again, change ubuntu (hd0,5) to (hd0,4) and windows (hd0,1) to (hd0,0) [I don't know if the windows part is correct, I just guess, and will check later].
Forestpixie, thank you very much. Case closed.

---

