---
title: "Dual-booting Ubuntu with Win Vista"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by abbeykabir on 2011-05-03
I successfully installed Ubuntu 10.10 (not yet gotten 11.04) on my Laptop with Win Vista installed already on it but I have an issues. Everytime I start my Win Vista OS, it'll boot to a certain point and then restarts. think in 5 attempts, it will restart 4 times and until i do a System repair it will then bootup. I actually partitioned my hard drive to install the Ubuntu and created a Swap(40GB and 3GB Swap). I HONESTLY DON'T KNOW WHERE THE PROBLEM LIES. I like the OS but I still want to use Windows. Any Suggestion or Help? 

I used Ext4 for the partition. and is it normal for me to still be able to access the windows files/folder bcos i could still browse to that part of the hard disk. And also this is the iso i downloaded "ubuntu-10.10.2-desktop-i386.iso.torrent"

Pls. help?

---

### Post by wilee-nilee on 2011-05-03
So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a what is where and more to work with, which is a good thing.;)

---

### Post by YesWeCan on 2011-05-03
Another way to do this is to use EasyBCD to add Ubuntu to your Windows bootloader. So you end up booting Ubuntu from Windows rather than the other way around. I would recommend this, especially when using Vista, because Vista does not like having a foreign master boot record. EasyBCD is free and I found it easy to use.
Repair Vista boot and then download EasyBCD and run it and follow the instructions.
I assume you are putting Vista and Ubuntu on the same disk?

---

### Post by abbeykabir on 2011-05-04
> **wilee-nilee said:**
> So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

This will give us a what is where and more to work with, which is a good thing.;)

If I understand u very well, I think this is what u r requesting for

```


menuentry "Try Ubuntu without installing" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    linux    /casper/vmlinuz  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Test memory" {
    linux16    /install/mt86plus
}



```
Thanks...

---

### Post by wilee-nilee on 2011-05-04
> **abbeykabir said:**
> If I understand u very well, I think this is what u r requesting for

```


menuentry "Try Ubuntu without installing" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    linux    /casper/vmlinuz  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Test memory" {
    linux16    /install/mt86plus
}



```
Thanks...

Not quite, lol don't worry it happens, so go to this site and download the script.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Drag it to your desktop, and run this command in the terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

You will see a very large text file appear, open it copy all of the text, and paste them into to the reply in the code tags as you have done in your response.

It is also normal for you to be able to mount the Windows partitions from Ubuntu, it is read and write so be aware of that.

---

### Post by abbeykabir on 2011-05-04
> **YesWeCan said:**
> Another way to do this is to use EasyBCD to add Ubuntu to your Windows bootloader. So you end up booting Ubuntu from Windows rather than the other way around. I would recommend this, especially when using Vista, because Vista does not like having a foreign master boot record. EasyBCD is free and I found it easy to use.
Repair Vista boot and then download EasyBCD and run it and follow the instructions.
I assume you are putting Vista and Ubuntu on the same disk?


i'll give it a trial. thanks

---

### Post by abbeykabir on 2011-05-06
> **wilee-nilee said:**
> Not quite, lol don't worry it happens, so go to this site and download the script.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Drag it to your desktop, and run this command in the terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```You will see a very large text file appear, open it copy all of the text, and paste them into to the reply in the code tags as you have done in your response.

It is also normal for you to be able to mount the Windows partitions from Ubuntu, it is read and write so be aware of that.

I'll do that. but i'd like to ask u another question. Is there a way or is it possible for me to re-package Ubuntu after i have installed all the application I use and my dirvers online? So that if I perform a fresh installation, I will have all my divers and apps. intact? How? if it possible

---

### Post by Quackers on 2011-05-06
Did you resize your Windows partition before you installed Ubuntu? If so, what program did you use for that?

---

