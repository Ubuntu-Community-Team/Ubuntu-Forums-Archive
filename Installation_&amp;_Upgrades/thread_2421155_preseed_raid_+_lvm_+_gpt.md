---
title: "preseed raid + lvm + gpt"
date: 2019-06-17
forum: Installation &amp; Upgrades
---

### Post by paulobruck1 on 2019-06-17
Hi guys

I have a pressed that  I modified to use with Ubuntu 18.04 with cubic to made an iso image, but at partitions I receive this error:

md-devices: mdadm: No array found in this file or automatically
partman: No mathiching phisical volumes found
partman Reading all phisical volumes. This way take a while...
apt-install: Queueing package mdadm for later installation
partman-auto-raid: Select spare cont: 0
partman-auto-raid: Spare device count: 0
partman-auto-raid: mdadm: Note: this array has metadata at the start and
partman-auto-raid:     ,may not be suitable as a boot device. If you plan to
partman-auto-raid:      store '/boot/  on this device please ensure that
partman-auto-raid:      your boot loader understands md/v1.x metadata, or use
partman-auto-raid:      --metadada=0.90
partman-auto-raid:   mdadm: Defaulting to version 1.2 metadata
partman-auto-raid:  mdadm: array /dev/md0 started
kernel:  ... md/raid1:md0: active whith 1 out of 2 mirrors
kernel:..... md0: deteced capacity change from 0 to 20933771264


preseed file:

# LVM
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-auto-lvm/new_vg_name string zeus
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-auto-lvm/guided_size string 20% 
#d-i partman-auto-lvm/guided_size string max


#RAID
d-i partman-auto/method string raid
d-i partman-md/device_remove_md boolean true
d-i partman-md/confirm boolean true
d-i partman-md/confirm_nooverwrite boolean true


# other
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true


#GPT
d-i partman-basicfilesystems/choose_label string gpt 
d-i partman-basicfilesystems/default_label string gpt 
d-i partman-partitioning/choose_label string gpt 
d-i partman-partitioning/default_label string gpt 
d-i partman/choose_label string gpt 
d-i partman/default_label string gpt 
partman-partitioning partman-partitioning/choose_label select gpt 

d-i partman-auto-raid/recipe string         \
    1 2 0 lvm - raidid=1 .                  \
    /dev/sda3#missing                       \
    .


d-i partman-auto/choose_recipe select expert_recipe
d-i partman-auto/expert_recipe string       \
    multiraid ::                            \
        10 10 10 free \
            $gptonly{ } $primary{ } $lvmignore{ } $bios_boot{ } method{ biosgrub } . \
        512 512 512 fat32 \
            $gptonly{ } $primary{ } $lvmignore{ } method{ efi } format{ } . \
        20000 5000 -1 raid \
            $primary{ } $lvmignore{ } \
            method{ raid } raidid{ 1 } . \
        512 512 512 ext4 \
            $defaultignore{ } $lvmok{ } lv_name{ boot } label{ /boot } mountpoint{ /boot } \
            method{ format } format{ } use_filesystem{ } filesystem{ ext4 } \
            options/defaults{ defaults } . \
        1000 1000 1000 ext4 \
            $defaultignore{ } $lvmok{ } lv_name{ barra } label{ / } mountpoint{ / } \
            method{ format } format{ } use_filesystem{ } filesystem{ ext4 } \
            options/defaults{ defaults } . \
        1000 1000 1000 linux-swap \
            $defaultignore{ } $lvmok{ } lv_name{ swap } \
            method{ swap } format{ } . \
        4000 4000 4000 ext4 \
            $defaultignore{ } $lvmok{ } lv_name{ usr } label{ /usr } \
            mountpoint{ /usr } method{ format } format{ } \
            use_filesystem{ } filesystem{ ext4 } options/defaults{ defaults } . \
.....
        100 100 100 ext4 \
            $defaultignore{ } $lvmok{ } lv_name{ varlogquarantine } label{ /var/log/quarantine } \
            mountpoint{ /var/log/quarantine } method{ format } format{ } \
            use_filesystem{ } filesystem{ ext4 }  options/defaults{ defaults } .





[FONT=Verdana]Any help would be very appreciated

thanks in advanced[/FONT]

---

