---
title: "Triple boot problems"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Setarkos on 2010-01-14
Hi there

I had Win7 installed on my Laptop and wanted to set up a triple boot with Fedora 12 and Mint 8. 
So I installed Fedora 12 and it worked loading grub and offering Win7 and Fedora as choices. 
Then I installed Mint hoping for the Grub2 to recognise Fedora and set up the triple boot but it didn't and I can now only boot into Win7 or Mint. 
sudo update-grub doesn't help
How can I configure grub2 to offer me all three OSs?

Thanks in advance

---

### Post by oldfred on 2010-01-14
I do not know fedora but copied this thread. It seems that the initrd file is not in an expected location and the osprober cannot find it. I saw were some did manual entries like this in 40_custom or modified the prober to look in the correct place:

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
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

---

