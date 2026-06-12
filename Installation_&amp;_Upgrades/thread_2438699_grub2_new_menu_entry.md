---
title: "grub2: new menu entry"
date: 2020-03-16
forum: Installation &amp; Upgrades
---

### Post by thiemo-kellner on 2020-03-16
Hi all

I could not find helpfull information with respect to my problem. I would like to try out some distros by starting from iso files. I stared out with [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) but when I update-grub after having added

```
submenu "ISOs" {
    menuentry "Peppermint 10 ISO" {
            set isofile="/thiemo/isos/Peppermint-10-20191210-amd64.iso"
            loopback loop (hd0,4)$isofile
            linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
            initrd (loop)/casper/initrd.lz
    }
    
    menuentry "Deepin Live System 2.0 ISO" {
            set isofile="/thiemo/isos/deepin-live-system-2.0-amd64.iso"
            loopback loop (hd0,4)$isofile
            linux (loop)/live/vmlinuz boot=live iso-scan/filename=$isofile noprompt noeject
            initrd (loop)/live/initrd.img
    }
    
    menuentry "Calculate 20 ISO" {
            set isofile="/thiemo/isos/cldl-20-x86_64.iso"
            loopback loop (hd0,4)$isofile
            linux (loop)/boot/vmlinuz boot=boot iso-scan/filename=$isofile noprompt noeject
            initrd (loop)/boot/initrd
    
    }
}
```

to /etc/grub.d/40_custom, I do not get any countable results:
```
root@lubuntu-18_10:~# update-grub                                                                               
Sourcing file `/etc/default/grub'                                                                               
Generating grub configuration file ...                                                                          
Found linux image: /boot/vmlinuz-4.18.0-25-generic                                                              
Found initrd image: /boot/initrd.img-4.18.0-25-generic                                                          
Found linux image: /boot/vmlinuz-4.18.0-24-generic                                                              
Found initrd image: /boot/initrd.img-4.18.0-24-generic                                                          
Found Ubuntu 18.04.2 LTS (18.04) on /dev/sda5                                                                   
Adding boot menu entry for EFI firmware configuration                                                           
done
```

So I tested echo and exit commands in the file but it it does not seem to get called at all. After resetting 40e r file I then created file/etc/grub.d/50_isos and this file was processed however, I got the
```
Sourcing file `/etc/default/grub'                                                                               
Generating grub configuration file ...                                                                          
Found linux image: /boot/vmlinuz-4.18.0-25-generic                                                              
Found initrd image: /boot/initrd.img-4.18.0-25-generic                                                          
Found linux image: /boot/vmlinuz-4.18.0-24-generic                                                              
Found initrd image: /boot/initrd.img-4.18.0-24-generic                                                          
Found Ubuntu 18.04.2 LTS (18.04) on /dev/sda5                                                                   
Adding boot menu entry for EFI firmware configuration                                                           
/etc/grub.d/50_isos: 5: /etc/grub.d/50_isos: submenu: not found                                                 
/etc/grub.d/50_isos: 6: /etc/grub.d/50_isos: menuentry: not found                                               
/etc/grub.d/50_isos: 8: /etc/grub.d/50_isos: Syntax error: "(" unexpected                                       

```

and here I am stuck. Has anybody an idea?

Kind regards

Thiemo

---

### Post by oldfred on 2020-03-16
I found getting path and parameters correct as ongoing issues.
It looks like you have your /home in your path. 
I found it better to have a separate partition. Some mount in a folder off / (root).

I also invariable edit 40_custom and forget to update grub.
So I now just have one permanent entry in 40_custom and edit a text file in my ISO folder.

Example of my 40_custom.
[https://ubuntuforums.org/showthread.php?t=2076205&p=13764329#post13764329](https://ubuntuforums.org/showthread.php?t=2076205&p=13764329#post13764329)

```
menuentry 'Live ISOs on SSD' {
configfile (hd0,5)/livecdimage.cfg
} 

```
And then the configfile entries in livecdimage.cfg

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd0,5)/iso/livecdimage.cfg
#} 
# Add iso names to livecdimage.cfg
#for i in `ls *.iso`;do echo "# "$i>>livecdimage.cfg; done;

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
set timeout=0

menuentry "Samsung" {
    set isofile="/ISO/Samsung_SSD_970_EVO_Plus_2B2QEXM7.iso"
    loopback loop (hd0,5)$isofile

    set gfxpayload=keep
    linux    (loop)/bzImage
    initrd    (loop)/initrd
}

menuentry "Focal Live ISO" {
set isofile="/ISO/focal-desktop-amd64.iso"
loopback loop (hd0,5)$isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile toram noeject
    initrd (loop)/casper/initrd
}
```

---

### Post by thiemo-kellner on 2020-03-17
Hi. Thanks for getting at my issue so fast.

> **oldfred said:**
> 
It looks like you have your /home in your path.

I found it better to have a separate partition. Some mount in a folder off / (root).

Well, not in PATH, but yes for the time being the ISOs reside in the home partition. I am a still reluctant to repartition my hd.

> **oldfred said:**
> I also invariable edit 40_custom and forget to update grub.

Hard on me too :-)

> **oldfred said:**
> So I now just have one permanent entry in 40_custom and edit a text file in my ISO folder.

I feel it cannot fix my problem as my 40 seems to be ignored. I put lines like ```
echo "Blörtz"
``` or ```
exit 1
``` into it and it did not take any effect I could notice.

Kind regards Thiemo

---

### Post by oldfred on 2020-03-17
Try putting an ISO in a / folder. I also have seen some use a folder in /boot.

I have seen issue that since system is not running, you only have grub, the home folder does not yet exist, so cannot be easily mounted. User in Linux is 1000 and only after you boot is 1000 equal to first user by $USER name.

---

### Post by thiemo-kellner on 2020-03-19
Thanks for trying. I did not work out. I fall back to USB installation. :-)

---

### Post by yancek on 2020-03-19
I've been able to boot an iso file directly from the /home/user/Downloads directory although I've also found with some distributions that it is better to have the iso file in the / of the filesystem or on a separate partition as suggested above. I know this is not the recommended way but, if your intention was to simply boot the iso one time to install, it would be simpler to put the menuentry directly in the /boot/grub/grub.cfg file, save it and reboot.  The grub.cfg file tells you not to edit the file but the reason for that is that changes made will not be included if you run grub-mkconfig (update-grub) so don't run it.   This saves running grub-mkconfig twice. 

I have the identical Peppermint iso on a partition which boots successfully.  My entry is similar to yours except for the kernel file which is vmlinuz rather than vmlinuz.efi shown in your entry.  Did you loop mount the Peppermint iso to verify that was the correct name of the kernel file?  It's a simple thing to do and could save time.

I usually install Grub to a flash drive and then copy the iso files to the flash drive and manually edit the grub.cfg file there.

---

