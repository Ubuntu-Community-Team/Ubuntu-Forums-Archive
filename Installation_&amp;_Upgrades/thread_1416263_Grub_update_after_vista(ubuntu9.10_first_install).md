---
title: "Grub update after vista(ubuntu9.10 first install)"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Frudo on 2010-02-25
Hello there guys , 
After playing around with different xsoft os'es, i am now (& will b) a proud rookie   of Linux :)

I have a little confusion , 
-dual boot ubuntu 9.10 & Vista business 
-4 partitions on HDD
-one is vista , one is ubuntu, one back up and anoher swap

I have been using linux , installed first , then i had to reinstall the crap vista again which eventually viped my Grub, now i cant boot into ubuntu. 
booted into ubuntu from a usb pendrive to get the terminal. 
Following this [http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](http://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)  i am kinda stucked . 

i know the linux is at dev/sda7 with the boot but cant get it updated. 
here is the message from the terminal ?

ubuntu@ubuntu:~$ mount | tail -1 
[COLOR=Red]/dev/sda7[/COLOR] on /[COLOR=Red]media/Linux[/COLOR] type ext4 (rw,nosuid,nodev,uhelper=devkit)
ubuntu@ubuntu:~$ ls /media/Linux/boot
abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-19-generic         System.map-2.6.31-14-generic
config-2.6.31-14-generic      System.map-2.6.31-19-generic
config-2.6.31-19-generic      vmcoreinfo-2.6.31-14-generic
[COLOR=Red]grub [/COLOR]                         vmcoreinfo-2.6.31-19-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-19-generic

ubuntu@ubuntu:~$[COLOR=Red] sudo grub-install --root-directory=/media/Linux/dev/sda7[/COLOR]
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit

any ideas ?

---

### Post by presence1960 on 2010-02-26
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Frudo on 2010-02-26
hello presence1960, 
 
i followed a couple of articles , searched the forum all over . but couldnt get it up an runnin again , therefore , risked loosin all my torrents , formatted the hdd again and started all over :(
although i managed  a fresh install of vista and ubuntu ,after a hell of a night , a 6 pack later  (now dual bootin perfectly :) ), this primary partitions thing is driving me crasy. 
from 4 partitions , i ended up with 1-vista ntfs, 2-unallocated 3-ubuntu 4- swap + 1 dell primery recovery  partitions. :( gpart or vista hd format or easeus partition didnt work to get the unallocated back to life, so i resized and added it to the primary vista partition. the options in live cd installation , i go by manual install . 
i can get around most of the stuff in computers but is there a way to change a partition already assigned as primary? or  how can u create an extended part ? by gpart ? 
cos i am going to have to resize the hdd again , i will have a primary dellbios, vista boot, backup makes 3 primary , rest will be unallocated and can get it to create an extended on that for both ubuntu and a swap ?
 
thanks for the ideas.

---

### Post by presence1960 on 2010-02-26
Given the current partition table you can not create another partition. You are maxxed out at 4 primary partitions. If you need more than four partitions you must have an extended partition. You can create as many logical partitions inside the extended that you wish, the only limit on that being how much space you allocated for the extended partition.

Please note that you can not install windows to a logical partition but you can put linux on a logical partition.

Here is a link for some reading: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Frudo on 2010-02-27
Thanks for the info , 
fully partitioning the drive , creating 1 extended  partition for ubuntu , then another 2 primary for vista & backup should work fine for me then. ? 
in that scenario , which option i can use for the gpart in live cd ? , manual or use all hdd ? (then creating other parts) ?
thanks

---

### Post by presence1960 on 2010-02-27
I would boot into windows first and create a set of recovery disk(s) whether you remove the dell recovery partition or not.

Next back up any data you don't want to lose.

I would leave the windows OS and the dell recovery partitions as is. I would delete the others and create an extended partition from all the remaining unallocated space. 

Then you can create logical partitions inside the extended partition for ubuntu, swap and anything else you may want. Remember you can create as many logical partitions inside the extended partition as you like, the only limit on that is how much space you have in the extended partition.

To do the partitioning I personally prefer the [gparted Live CD]("http://gparted.sourceforge.net/livecd.php"), but the ubuntu Live CD with gparted will suffice.

---

### Post by Frudo on 2010-02-27
Yes , 
thats what i am gonna do , but one quest though .
Is there a difference between live cd and usb stick versions in terms of gpart ?
if not i can start over now .

---

### Post by presence1960 on 2010-02-27
> **Frudo said:**
> Yes , 
thats what i am gonna do , but one quest though .
Is there a difference between live cd and usb stick versions in terms of gpart ?
if not i can start over now .

they are the same. I use gparted Live CD/USB because it is the most up to date compared to gparted on the Ubuntu Live CD

---

### Post by Frudo on 2010-02-28
presence1960, 
hi ya again.
As discussed , i wiped the hdd leaving the dell boot(sda1), (vista sda2), created another primary part (sda3)for back up then an extended part(sda4 for the rest + 1 swap in it  using ubuntu usb stick , now everything is in perfect order. sda5 for linux sda6 for swap
Thank  you for the guidance. 
Now that i have an itching feeling inside :) , i'm gonna go ahead and try to make this brilliant machine to boot on W7, located at my ext.hdd. 
I may have probs. for updating the Grub to do that but will keep posted , man . 

Frudo

---

### Post by presence1960 on 2010-02-28
> **Frudo said:**
> presence1960, 
hi ya again.
As discussed , i wiped the hdd leaving the dell boot(sda1), (vista sda2), created another primary part (sda3)for back up then an extended part(sda4 for the rest + 1 swap in it  using ubuntu usb stick , now everything is in perfect order. sda5 for linux sda6 for swap
Thank  you for the guidance. 
Now that i have an itching feeling inside :) , i'm gonna go ahead and try to make this brilliant machine to boot on W7, located at my ext.hdd. 
I may have probs. for updating the Grub to do that but will keep posted , man . 

Frudo

Good to hear. let us know how it turns out.

---

### Post by Frudo on 2010-03-06
Hi there again , 
I am really impressed so far with Ubuntu , and the massive supportive community behind it. Now back to booting W7 from external drive. There are tutorials on the net how to do it , i tried but as i am not good with some skills required i gave up on the project. 
That was for booting W7 from any external source. usb stick or hdd. Both can be done but my way was moving the partitions around a bit and installing it to internal hdd. 
Now i can triple boot  Vista Business, Windows 7 and UBUNTU , with the help of the Grub loader. :) I must say though since i started playing around with this koala,  i havent booted into any of the windows. :) I didnt give up external booting totally though , now the new one is snow leopard.But for that i must buy a new hdd or an 8 gb usb stick. once  get a hold of the drive , i will post it. 
This koala thing :) is endless and i am hungry to learn. Thanks again to the community.
Frudo.

---

