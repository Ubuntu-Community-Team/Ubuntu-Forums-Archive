---
title: "Not able to download file packages."
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by xWoodie on 2011-01-26
I put Ubuntu on my computer about a week ago, and have not been able to download many new programs or updates.  For expmple, I'll go over to Update Manager and try to install something, but it will stop usually halfway through or near the end and show me an error message.  usually, the message looks like this:
----------------------------------------------------------------------------------------------------------------------------
FAILED TO DOWNLOAD FILE PACKAGES
Check your Internet connection

Details:
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.12.1-0ubuntu10.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.12.1-0ubuntu10.2_i386.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.12.1-0ubuntu10.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.12.1-0ubuntu10.2_i386.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.32.1-0ubuntu1.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.32.1-0ubuntu1.1_i386.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/libevolution_2.30.3-1ubuntu7.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/libevolution_2.30.3-1ubuntu7.3_i386.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.98+20100804-5ubuntu3.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.98+20100804-5ubuntu3.1_i386.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98+20100804-5ubuntu3.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98+20100804-5ubuntu3.1_i386.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.10.6-1ubuntu10.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.10.6-1ubuntu10.2_all.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.38.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.38.3_all.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-25_2.6.35-25.44_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-25_2.6.35-25.44_all.deb) Hash Sum mismatch
--------------------------------------------------------------------------------------------------------------------------
I'm aware that I can go to Software Sources and change the sever I get the downloads from, and I've tried tons of them.  I've even connected to a wireless Internet connection to see if that would fix it.

I'm still new to Ubuntu an am still exploring the world of Linux, so easy-to-follow instructions would be greatly appreciated! :P

I'll go to bed early because of testing tomorrow, but I'll t check this thread again tomorrow and bring it back up then if my problem hasn't been fixed.

---

### Post by gordintoronto on 2011-01-26
Do you use a USB Ethernet adapter? Data is being lost somewhere between your modem and your CPU, perhaps in your router, perhaps in your Ethernet adapter, or even a slightly loose cable?

---

### Post by xWoodie on 2011-01-27
I'll check that right now and change the topic to "Fixed" if it worked.

*EDIT*- Still did not work right.  I have less "mismatches" though.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.12.1-0ubuntu10.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.12.1-0ubuntu10.2_i386.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.10.6-1ubuntu10.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.10.6-1ubuntu10.2_all.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.38.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.38.3_all.deb) Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-25_2.6.35-25.44_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-25_2.6.35-25.44_all.deb) Hash Sum mismatch

---

### Post by xWoodie on 2011-01-27
I figured this would be a simple fix.  No one has any ideas?

And no, I don't use a USB Internet adapter or wireless connection.  Just a normal ethernet cable running straight to the router downstairs in the basement.

---

### Post by gordintoronto on 2011-01-27
If it were me, I would put the computer next to the router and try a short Ethernet cable. It probably wouldn't make any difference, but it eliminates a couple of possibilities.

---

