---
title: "one separation boot partition for several os"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by VlaDiSalV on 2015-06-30
Hi! I have home and working laptop. And I need very high security requirements, so i encrypted whole hard drive for two machine. For more security i installed boot partition to usb flash drive (so, i can take it with me).
But it's not comfortably have two usb flash. I thought separated my usb drive on two partitions, but now i think about crazy idea: it is really have one boot partition and boot from it two system on different machine?
Of course, i will have one version OS and linux-kernel.

---

### Post by dino99 on 2015-06-30
Some more prooved ideas  ):P

[https://www.google.fr/search?q=lubuntu+custom+shortkey&oq=lubuntu+custom+shortkey&aqs=chrome..69i57.9244j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8&gfe_rd=cr&ei=PJiSVd6zOouBoAfHk4GoBw#tbs=qdr:y&q=ubuntu+custom+paranoid+security](https://www.google.fr/search?q=lubuntu+custom+shortkey&oq=lubuntu+custom+shortkey&aqs=chrome..69i57.9244j0j8&client=ubuntu&sourceid=chrome&es_sm=93&ie=UTF-8&gfe_rd=cr&ei=PJiSVd6zOouBoAfHk4GoBw#tbs=qdr:y&q=ubuntu+custom+paranoid+security)

---

### Post by grahammechanical on 2015-06-30
Have you tried loading Ubuntu from the wrong USB stick? It does not work. Does it? That is because in Linux every partition has a Universally Unique Identifier (UUID) number. And Grub uses UUID to find the boot partition and the Linux image to load. Compare /boot/grub/grub.cfg from both machines and you will see what I am talking about.

If this idea is going to succeed you will need to create a special grub.cfg for each USB stick. In /etc/grub.d/ you will see some files. The information in these files is used to create grub.cfg. We can edit these files and when we do change those files we run

```
sudo update-grub
```

And that will create a new grub.cfg that will include our changes. I suggest that you edit /etc/grub.d/40_custom. Do this first on the home computer. And put in it the information from /boot/grub/grub.cfg of the work laptop. Copy the information under the heading

> ### BEGIN /etc/grub.d/10_linux ###

to the end of that section. Then save 40_custom and then change the permissions to set the file to allow execution as a program and then run sudo update-grub. And see if that USB stick will give you a boot menu that will let you load Ubuntu on either machine.

You can repeat the process for the other USB stick when it is plugged into the work laptop and this time you create a /etc/grub.d/40_custom with information from the /boot/grub/grub.cfg of the home computer.

In this way it might be possible to have one USB stick load Ubuntu on both machines and have another USB stick as a spare. Be aware that whenever there is an upgrade to the Linux kernel on these machines. Then /etc/grub.d/40_custom will have to be modified accordingly.

Regards.

---

### Post by oldfred on 2015-06-30
I install just grub to flash drives to boot install ISO or repair ISOs directly. But I also add boot stanzas to boot some of my installs inside my system also.
With just grub on a flash drive there is no auto updates. You just have to manually add your boot stanzas like grahammechanical suggests to 40_custom. 
But with either 40_custom or your own grub you can use the links to the most current kernel that system creates. Then you do not have to update.

       Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

      
```
 menuentry "Latest Kernel in sda1" {
insmod ext2
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
}


```

---

