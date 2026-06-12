---
title: "Grub 2 Fedora Install not seen by 40_custom"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by PeggySue on 2009-12-02
I have installed Fedora 12 on sda 7 of my my Dell AMD 64 Vostro laptop which has a single hard drive.  I chose not to let Fedora install its own boot loader as I expected it to be found by an update-grub2 in Ubuntu 9.10.  It didn't find it!

In Fedora, initramfs and vmlinux are in /boot.  I was going to make a link to these files in / but don't know how to change directory to a different partition.

I followed this link:
[http://ubuntuforums.org/showthread.php?t=1318128]("http://ubuntuforums.org/showthread.php?t=1318128") and drs305's template for grub's 40_custom.  I changed the drive to sda 7 and the file names to match those from Fedora.

My /etc/grub.d/40_custom looks like this:
```
menuentry "Fedora" {
set root=(hd0,7)
linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=/dev/sda7 ro quiet splash
initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
} 
```

Update-grub2 doesn't report seeing Fedora but this extract from /boot/grub.cfg suggests it did.

```
......
menuentry "Fedora" {
set root=(hd0,7)
linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=/dev/sda7 ro quiet splash
initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
} 
### END /etc/grub.d/40_custom ###
```

Fedora isn't shown on a reboot so there is no way to boot it.

Can anyone suggest what I am doing wrong or shall I learn how to move to a different partition in a terminal and make links in / pointing to /boot?

Thanks

---

### Post by phillw on 2009-12-02
Hi,

You may want to have a look over at [http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)  It is drs's more in depth look at Grub2. I note from the thread you pointed to, that he had some doubt to if the OP was running the Ubuntu MBR, or the Fedora one. If you are in any doubt, the above thread also covers the (re)installation of Grub2 and which files to edit (and which not to) for the update-grub command to take them into account and build it's grub.cfg file (Which you mustn't edit !!)

Regards,

Phill.

---

### Post by PeggySue on 2009-12-02
Hi Phill

Tried those notes but didn't see the answer.
Tried making symbolic and hard links in the Fedora partition - No luck.
So tried hacking grub.cfg - This gave the answer!!

Taking a template from grub.cfg 10_linux entries and putting it in 40_custom is the way forward.  I don't know if it is the /dev/sdax rather than UUID that is wrong or the other missing items but this works:

```
menuentry "Fedora 2.6.31.5 on sda7" {
	recordfail=1
	if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
	linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro 		quiet splash
	initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}
```

For anyone trying to find the UUIDs use:
```


ls -l /dev/disk/by-uuid


```

---

### Post by phillw on 2009-12-02
> **PeggySue said:**
> Hi Phill

Tried those notes but didn't see the answer.
Tried making symbolic and hard links in the Fedora partition - No luck.
So tried hacking grub.cfg - This gave the answer!!

Taking a template from grub.cfg 10_linux entries and putting it in 40_custom is the way forward.  I don't know if it is the /dev/sdax rather than UUID that is wrong or the other missing items but this works:

```
menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}
```For anyone trying to find the UUIDs use:
```


ls -l /dev/disk/by-uuid


```

okies. getting and setting the uuid is covered here --> [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I had to do that when i messed up my dual-boot Grub --> Grub2 upgrade.

Phill.

---

### Post by PeggySue on 2009-12-03
Thanks for that.  My brain was in hacking mode so I was just thrashing ideas around and didn't go back to the original documents!

Thanks for your support.  Appreciated.

---

### Post by lawaladekunle on 2009-12-04
I also Had the same problem and was unable to boot my Fedora 11 but i got it fixed by editing my grub.cfg on the line just after the 40_custom comments. 



### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora (2.6.29.6-217.2.3.fc11.i686.PAE)" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set dac2df11-8cec-4ab1-9444-2374e6ea4ab2
    linux    /vmlinuz-2.6.29.6-217.2.3.fc11.i686.PAE ro root=/dev/mapper/luks-14f13a34-a2e9-4440-af4c-ebc6018ce3c6 rhgb quiet
    initrd    /initrd-2.6.29.6-217.2.3.fc11.i686.PAE.img
}

### END /etc/grub.d/40_custom ###




1. Use the blkid command to determine the uuid

2. set root=(hd0,1)      (root device where your boot is housed)

3. search --no-floppy --fs-uuid --set dac2df11-8cec-4ab1-9444-2374e6ea4ab2  

 for the above the correct uuid for the boot partition should be inserted here after the --set .


4. linux /vmlinuz-2.6.29.6-217.2.3.fc11.i686.PAE ro root=/dev/mapper/luks-14f13a34-a2e9-4440-af4c-ebc6018ce3c6 rhgb quiet 

you can get the correct path for the root device and the uuid from your previous grub config. (Check the uuid against that in the results returned by the blkid command ) (my root partition is encrypted that is why the (**luks**) bit is there)


**N.B.** Finally after it works remember to backup your grub.cfg in case you might need it.

---

### Post by PeggySue on 2009-12-04
The rhgb option above is new to me; I will have to search for kernel options and see what other choices there are!

If the above option works, I would definetly put it into 40_custom and do a grub2-update.  grub.cfg gets overwritten with upgrades.  The link from 40_custom to grub.cfg is sound and works even if the text it is transporting isn't valid.

---

