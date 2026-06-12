---
title: "Unable to install GRUB in /dev/sda"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by know-it-some on 2008-08-06
Hi all,

I am installing Ubuntu Server on brand new hardware, and encountering the above error on near the tail end of the install.  Here is some relevant info:

* Ubuntu is the only OS.  no other OS's will be installed at all.
* I have 4 SATA drives attached to an Adaptec RAID card, configured into a single 3TB RAID 0 config.
* I am selecting 'Guided - Use entire disk' for the partitioning, and the array is correctly detected.

One thing I think is odd is that the guided partitioning seem to want to create two partitions: one for / which is formatted into ext3, and the other for swap space.  There is no mention of creating a /boot partition, which is where I thought the GRUB bootloader would go.

Please let me know if I can provide any additional information.  Any ideas on why GRUB is not able to install on /dev/sda??  Thanks!

---

### Post by know-it-some on 2008-08-07
Update:  same error after manually partitioning.  I decided to go in and manually create the three partitions I thought should be there.  namely:

3 tb ext3 /
10 gb swap
500 mb ext3 /boot

Even when manually creating the partitions the same error occurs and the execution of grub-install /dev/sda fails.

Any suggestions would be welcome
Thanks!

---

### Post by spiderbatdad on 2008-08-07
you might go back to the guided install...a boot partition is not necessary to manually create. Let the installation complete without grub...that is skip it when you are offered the option to continue without grub installed. After the installation completes, put the live cd in again, as if you were going to re-install. There is a "fix-grub" option at some point several steps into the process...it may even be under an advanced tab in the lower right corner.
Sorry I can be more specific. I had this problem only once, and this was my only solution. There is a fix grub option, you'll just have to pay attention to find it. Good Luck.:)

---

### Post by know-it-some on 2008-08-07
Thanks for the tip!  I'll try that now and report back how it works out.

---

### Post by know-it-some on 2008-08-07
Wait...  Is the LiveCD referred to as the 'Aternate CD' on this page:
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
??

I am not sure if the server version has a livecd.

---

### Post by spiderbatdad on 2008-08-07
> **know-it-some said:**
> Wait...  Is the LiveCD referred to as the 'Aternate CD' on this page:
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
??

I am not sure if the server version has a livecd.
Pardon the mistake...I meant cd, not live cd. The server version of Intrpeid Ibex alpha2 was the first time I had to use this option. So, install without grub. Try to boot, you'll get grub error 21 or 17...then put the cd in again, and start through the installation process, several steps in, you'll encounter the option to fix grub.

---

### Post by know-it-some on 2008-08-07
Hm. I simply did not see that option anywhere at all.  I ran through the install cd a couple of times looking for it. Perhaps I am missing it but I don't think Hardy Heron includes this as an option.

---

### Post by spiderbatdad on 2008-08-07
hmm. it should have been there on the hardy cd. Did you try to boot and get the grub error message?
Perhaps this will do it:[http://maff.ailoo.net/2008/07/reinstall-grub-using-a-linux-live-cd/](http://maff.ailoo.net/2008/07/reinstall-grub-using-a-linux-live-cd/)

There many other fix grub tricks available through google, sorry I couldn't be of more help. Good luck. You'll get it fixed eventually.:)
PS I know that article may look like is doesn't pertain to your issue, but it is the install grub commands that you are interested in.
Keep in mind you are probably looking to mount sda1 not sda6...

---

### Post by know-it-some on 2008-08-11
Okay, that's a great link so thanks.  As it happens I may not pursue this since LILO installed just fine even if Grub would not. I cannot imagine why one boot loader would install just fine, while another would not unless GRUB requires some special Adaptec driver.

---

