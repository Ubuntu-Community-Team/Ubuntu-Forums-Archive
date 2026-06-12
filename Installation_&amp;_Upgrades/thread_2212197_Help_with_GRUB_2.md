---
title: "Help with GRUB 2"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by samlant on 2014-03-19
Evening everyone!
     I appreciate you viewing this, and I thank you for taking time out of your day to read this post!

**My Issue**: I first installed Ubuntu 13.10 with it's bootloader in the MBR (/dev/sda). I then created a **dedicated GRUB partition** to "chainload" a total of 3 OS's, including Ubuntu, WIndows 7, and another linux distro called Uberstudent.

THERE IS NOTHING WRONG WITH THE INTEGRITY OF UBUNTU'S BOOTLOADER. However, I am uncertain if there are missing files in the Dedicated GRUB Partition (such as 00_header, etc.).

I then installed GRUB 2 to the Dedicated GRUB partition (/dev/sda3), so that if I delete or change OS's, GRUB is unaffected and I can edit grub.cfg without worry. However, when I boot my system, I noticed that it uses the bootloader found in my Ubuntu's "/boot" directory and **not** the one found in my dedicated GRUB partition. How may I switch the MBR (Master Boot Record) that holds stage 1 of GRUB2 to point to my **dedicated GRUB partition** (/dev/sda3) and not my **"/boot"** folder in the "**/**" partition of Ubuntu (/dev/sda5)?

---

### Post by sudodus on 2014-03-20
Welcome to the Ubuntu Forums :-)

See this link [https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

You can probably use this method, where in your case the dedicated GRUB partition is /dev/sda3

```

sudo mkdir /mnt/boot
sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda3 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda

```

---

### Post by samlant on 2014-03-20
Thank you very much for this! It, as you suggested, was just in need of a simple reinstall of --boot-directory=/mnt/boot /dev.sda command. I appreciate your help and devotion! It's now using the bootloader on the partition in my /dev/sda3 (my dedicated GRUB partition). 

A follow-up question, because I haven't been able to find a clear answer to this: Would it be _**safe**_ to copy the files found in /etc/grub.d, such as 00_header, 05_debian_theme, and 40_custom, to the dedicated GRUB partition, leaving Ubuntu out of the main bootloading programming (as is my understanding as that would do)? Further, would it be **_wise_** and **_beneficial_** to do so? If it saves a little bit of space on my Ubuntu drive, yet doesn't sacrifice stability, I see it as a good choice. Does anyone disagree?

---

### Post by deadflowr on 2014-03-20
Moving or copying the files from /etc/grub.d won't be beneficial as they don't have anything to do with the actual booting.
The important file is the one those make, which is the grub.cfg file found in the /boot folder.
That's the file that is actually read during boot.
More important though is I think grub's design is dependent on them being in that location.(/etc/grub.d)
So unless you want to re-write a few files, keep them where they are.

---

### Post by sudodus on 2014-03-21
> **deadflowr said:**
> Moving or copying the files from /etc/grub.d won't be beneficial as they don't have anything to do with the actual booting.
The important file is the one those make, which is the grub.cfg file found in the /boot folder.
That's the file that is actually read during boot.
More important though is I think grub's design is dependent on them being in that location.(/etc/grub.d)
So unless you want to re-write a few files, keep them where they are.

+1

---

