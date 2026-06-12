---
title: "Installing Ubuntu on laptop with Windows already installed"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by Josh784 on 2006-09-12
When I installed Windows on my laptop, I divided the hard drive into 3 partitions.  One I used for the Windows partition, and the other two I left unformatted.  The larger of the two I want to use for the Ubuntu install, and the other as a means to swap files between Windows and Linux.

How should I go about setting this configuration up?  Is it possible to do without erasing my Windows partition, which is what the Ubuntu installer leads me to believe.  I get as far as the prepare mount points screen, at which point I am clueless.

I have been unable to find any articles on the web dealing with this, surprisingly, so any help would be appreciated.

Thanks

---

### Post by Josh784 on 2006-09-13
I really can't seem to find any information on this.

Even an explanation of what /, /home, /boot, /usr, /vsr, /media/sda1 etc means, would be helpful.  The Ubuntu installer is horrid when it tries to explain the options on this screen.

I would think that this would be a fairly typical install scenario?  I'm really surprised that I can't find any helpful information.  I must be looking in the wrong places.

---

### Post by Josh784 on 2006-09-13
I'm also trying to add a new partition as a swap partition for linux, but it doesn't show up on the prepare mount points screen, rather a few new partitions of size less than 1mb do instead.

---

### Post by Josh784 on 2006-09-13
Alright, I've managed to create a / partition and /swap partition, and am installing now...I couldn't find any information on /what to use for the shared partition, so I axed it and will use my external hard drive for that purpose.

---

### Post by confused57 on 2006-09-13
See this guide:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Check out the sections on plan partitions and installing Ubuntu...if something isn't clear, just ask.

---

### Post by plexi50 on 2006-09-13
I found the partition/installer on the Ubuntu disc difficult. I recommend GParted, a live CD/partioner. It makes it really easy to resize, delete, and add partitions. Look at distrowatch.com to find the download. You have your 3 partitions. 1 is windows, Other large one will be Ubuntu. Make it a primary partion, type would be ext3. Your swap partion only needs to be twice the size of your installed memory, so if you have 512mb, just setup a 1024mb, type=linux swap. You should be good to go. I never did the multiple partions for home, root, etc. There is a limit to how many primary partitions you can have, I think it is 5? Not really sure. Be sure to install Grub in the mbr of the same partition you install Ubuntu, it should find Windows and add an entry for it.

---

