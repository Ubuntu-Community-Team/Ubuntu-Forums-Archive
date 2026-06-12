---
title: "boot from iso image on hdd"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by JJSkoli on 2012-09-01
Hello, I am having problems installing a new OS from its iso file, and I am searching for help. 

I run Ubuntu 12.04-64 bits on a Toshiba laptop, using GRUB2; I have decided to mount on a separate partition Poseidon Linux, a Ubuntu-based specialized distro running Linux kernel 2.62. I downloaded their iso (/home/JJ/Downloads/Poseidon_Linux4_64bit.so) to my Downloads directory, then followed [https://help.ubuntu.com/community/Grub2/ISOBoot#Creating_the_GRUB_2_Menuentry]("https://help.ubuntu.com/community/Grub2/ISOBoot#Creating_the_GRUB_2_Menuentry")

To be explicit, I added these lines 
```
 
menuentry "Install Poseidon from ISO" {
set isofile="/home/JJ/Downloads/Poseidon_Linux4_64bit.iso"
loopback loop (hd0,6)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.gz
}
```
to the file /etc/grub.d/40-custom, updated grub, and failed. This is to check the file /home/JJ/Downloads/Poseidon_Linux4_64bit.iso does indeed reside in the 6th partition of my disk:
```

 sudo lsblk -f
NAME   FSTYPE LABEL MOUNTPOINT
sda                 
&#9500;&#9472;sda1 swap         [SWAP]
&#9500;&#9472;sda2              
&#9500;&#9472;sda3 ext3         
&#9500;&#9472;sda4 ext3         
&#9500;&#9472;sda5 ext4         /
&#9492;&#9472;sda6 ext4         /home
sr0                 
zram0  swap         [SWAP]

```

The fail code is:```

error: disk not found

```
and from this follow kernel not found, initrd not found. The problem is not so important per se (in the end, I used unetbootin to install via USB, successfully, and I could have installed it in my VBox just as well), but it bugs me that I may not be able to use such a convenient procedure in the future when equally convenient alternatives may not be at hand.

Can anyone point out to me my mistake? Thank you.

---

### Post by dino99 on 2012-09-01
Do your choice:

[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

[http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html](http://www.webupd8.org/2011/02/how-to-boot-iso-with-grub2-easy-way.html)

[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by oldfred on 2012-09-01
Your entry looks ok.

But even all the Ubuntu's do not work. Some put the kernel in different locations than /casper like /install. Also older one's did not work as ISO was not configured for booting. Some Other distributions also do not work with grub2's loopmount.

Another issue was with server and some older on initrd.gz was initrd.lz. 

You can mount ISO and look to see if files are in /casper and if its own boot parameters are the same or not.

---

### Post by JJSkoli on 2012-09-01
Many thanks to dino99 and oldfred for their replies. I am leaving this note for future readers, and will mark the thread as solved becauso dino99's suggestion #2 worked for me. 

Unfortunately, I had carried out all checks suggested by oldfred before asking for help. I had loop-mounted the iso, checked the location of vmlinuz and initrd, and the fact that initrd's extension is .gz, not .lz. I tried the install using /home/JJ/...
as the path to the iso, and /JJ/... since I use a separate home partition. dino99's suggestion #3 is in fact an older version than the one I had initially referred to; I was lunable to extract anything new from it. Despite all of this, I stil get the dreaded error message: disk not found, and in any case you have to mount a kernel.. 


What REALLY worked was dino99's suggestion of using unetbootin to perform this task. It worked flawlessly for me, and IMHO it is even easier to use than the community's suggested method. It does employ third-party software of course, but hey who am I to judge... 

In any case thank you guys for your awesome help; even if I don't write often, I do read you regularly. Cheers.

---

