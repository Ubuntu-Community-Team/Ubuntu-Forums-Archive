---
title: "Boot-repair problem"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by hagdouglas on 2012-10-07
Hello,

I use windows 7 , i have three partitions C: , D: , E: . I was reducing the space of D: and E: to allow more space for the C: when the E: partitions disappear after rebooting i've try to use partition magic and Eauseus partition tool but i wasn't be able to recover the partition .

Then i use Testdisk he found that my system partition was in confilct with the E: missing partition . I followed the instruction in the tutorial and press to write . Reboot and the MBR message appears. 

I download Ubuntu and Bootrepair , but unfortunately that won't work either . I've tried with the Windows 7 boot cd and when i was using the repair tool it was repair but don't working.

I was thinking to upgrade to an SSD and add another HDD for more space . So do you think i can repair it or at least recover the data on it ( the E: missing) because i still have the D: .

Thanks !

---

### Post by hagdouglas on 2012-10-07
The link for the report : [http://paste.ubuntu.com/1265681/](http://paste.ubuntu.com/1265681/)

---

### Post by critin on 2012-10-07
> I download Ubuntu and Bootrepair , but unfortunately that won't work  either . I've tried with the Windows 7 boot cd and when i was using the  repair tool it was repair but don't working.Did you choose to run 'Recommended Repair'?  It only ran Boot Info Report.
See at line 210 what the repair would do and where the user chose the options.

=================== Default settings
Recommended-Repair This setting would restore the [(generic mbr)] MBR in sda, and make it boot on sda2. Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot  

=========== Settings chosen by the user
Boot-Info This setting will not act on the MBR.

---

### Post by hagdouglas on 2012-10-08
Hi,

I downloaded the edtion with bootrepair included and run the "Recommended Repair"
And its still won't work :(

---

### Post by darkod on 2012-10-08
Boot-repair is not a wonder tool that can help you anytime windows messes up your system. First of all, you are not even dual booting, don't you think you can get more expert help for windows on windows forums?

What I can see right away, is that you are missing one of the boot files of win7, the /bootmgr on /dev/sda2.

I am not sure why you tried boot-repair at all, don't you have your win7 dvd? That would be the first option to try to repair your boot.

It seems you tried to do too much at once, you have to be very careful with partitioning, and don't try anything "too exotic" especially without a full backup of your system.
If you do have a full backup, simply rearrange your hdd and restore the backup, it will be much faster than trying to sort this out.

---

