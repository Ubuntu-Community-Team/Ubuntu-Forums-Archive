---
title: "Ubuntu 11.04 installer crashed"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by Iqbal_ on 2011-05-12
Hi,

Laptop details:

64 Bits
Dual boot with Vista and Ubuntu 9.10. Both running successfully.
Intel core 2 duo processor, nVidia cards
500 GB HDD, 4 GB RAM

I upgraded to ubuntu 11.04 from ubuntu 9.10.
I used live cd then chosen boot option (pressing F6) nomodeset. Now system was running from Live CD.
Thereafter ubuntu 11.04 was installed. The next day problem came up.


Yesterdays experience:

If I do not put live CD, then (grub rescue)  prompt comes up.
After booting from LIve CD (using boot option nomodeset), I ran the terminal and used fsck. fsck fixed a partition. Then I started installing ubuntu 11.04. In ubuntu I have 4 partitions - 1. / 2. /boot 3. /home and 4. swap. When the partitions came up I chose to format / and /boot partitions and pressed Forward button. The progress bar was showing that it is copying files. This process was taking more than usual time. During all this process a message was coming up saying "A disk is reporting health problem. Examine-Cancel-OK buttons".
Then finally installer crashed, with the following  message.

"[Errno 30] Read only file system: /target/usr/Share/gwibber/ui/themes/default. This is oftem due to a faulty disk. It may help to check whether the hard disk is old and in need of replacement or move the system to a cooler environment."

Finally installation failed.

Another message at the same time was saying that details are in /var/log/syslog and /var/log/partmanlog files.  In order to get these two log file, I put the usb drive in. The Place menu was listing the usb drive but not mounting it. I tried to copy these log file to usb drive using cp command in terminal- this command did not give any error. When I checked the drive on another computer for files, these log files were not copied to usb drive. Therefore I can not provide those log file here.

During this process, it was also saying that there was problem with ubiquity.

Now I have following problems:
1- How to solve this problem and restore this system?
2- At the time of installing ubuntu 11.04, I chose to encrypt my home folder. Now I am not able to get it. How to get my files back from this encrypted folder?
3- Windows partitions are listed in Places menu but not mounted. How to get the files from those folders?

Once I get my files back, I can fearlessly delete/format partitions.

---

