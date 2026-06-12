---
title: "Boot failure after upgrade of 10.10"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by RoyT on 2011-11-03
I was running 10.10 LTS (not 11.x) and last week the software center said there was an upgrade available, which I installed. It required a reboot. I chose the "restart to finish..." so there was not even a power cycle involved. The reboot halted in grub. After typing "exit" I got the message "No bootable device found" (or something like that). 

I created a bootable USB with 10.04 to see if the disk was alive. It appears to be NORMAL! The "Disk Utility" shows "disk is healthy" for SMART, the Benchmark gives reasonable results. It says that the "boot flag" is set. The disk shows up as ext2 and I have no trouble accessing it.

It appears that the upgrade destroyed some critical information. WHAT is Wrong and how can it be fixed?

(How is it that a simple upgrade can cause such a catastrophic problem?!)

---

### Post by 0121computers on 2011-11-03
This happens when a program changes your program settings to a more up to date format which sometimes conflicts with your computer if you have your origonal instalation disc you can swich on your computer f9 for your boot settings put your disc in and boot from cd/dvd this should fix it for you if not it would be a good idea to purchase a copy of Discimge from your local pc shop this will boot your system independantly of windows

---

### Post by darkod on 2011-11-03
10.04 was LTS version, 10.10 is not. However that should not matter for failing the upgrade.

Do you know what is your root partition? If you do, you can try reinstalling grub from live mode. For example, if /dev/sda5 was your root partition, from live mode you would run:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Try rebooting from the hdd after that and see how it goes.

Otherwise, for more info about your system you could run the bootinfoscript from live mode and attach the resulting file here. Instructions and link to download: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by 0121computers on 2011-11-03
Another way is to do a system restore and restore the computer to an earlyer working state

---

### Post by darkod on 2011-11-03
> **0121computers said:**
> Another way is to do a system restore and restore the computer to an earlyer working state

System restore? Are you talking about windows? How would system restore help repair your grub and ubuntu boot? Windows can't even see the ubuntu partitions and grub by default.

---

### Post by RoyT on 2011-11-04
Thanks for the help. I have tried the commands you suggested and the the grub-install command failed as follows:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/dev/sda
install_device not specified.
...
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/dev/sda1
install_device not specified.
...
(Usage was dumped in each case.)

I don't know why I am getting this error.

I also ran boot_info_script.sh as suggested and got the attached file. It does look like the boot sector is not set up right. I do not know a lot about what it should look like but I assume sda1 should look somewhat like sdc1, which is the ubs stick I am running off of.

I have been able to copy /home off onto another usb stick so am contemplating a reinstall, but this takes a long time to complete. I am still interested in getting the patch process you suggested to work, if it will. The knowledge may come in handy in the future.

---

### Post by darkod on 2011-11-04
You are getting the error because you did not leave a space between the /mnt and /dev/sda.

sudo grub-install --root-directory=/mnt /dev/sda

The --root-directory value is /mnt and the destination device /dev/sda (your HDD MBR). That's why it says install device (destination) not specified.

---

### Post by darkod on 2011-11-04
However, the results file shows that you are missing the boot files from your root partition. Not sure if you can recover it from this easily, and is it worth it compared to a new install.

The grub files can be recreated but you seem to be missing the /etc/fstab too, and it will never mount the partitions and boot without it.

---

### Post by RoyT on 2011-11-05
Thanks for the help. I did try again with the corrected grub-install command without success. You are right that pursuing this line is much more effort than reinstalling. Since I was able to save my /home dir to a USB stick I am going to rebuild.

Thanks again.

---

