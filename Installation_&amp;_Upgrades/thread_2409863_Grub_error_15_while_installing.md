---
title: "Grub error 15 while installing"
date: 2019-01-07
forum: Installation &amp; Upgrades
---

### Post by anteevic on 2019-01-07
Hello,
I decided to switch from Windows 7 to Ubuntu. A friend of mine made me a bootable USB since I couldn't do so myself- my Windows has soms corrupted files and I don't really want to go through system recovery. Anyways, I got the USB and decided to boot from it(keep in mind that I still have Windows installed) and I got to the screen where I have to pick whether to install Ubuntu with ACPI or without. Regardless of what I pick, I get the error 15 grub4dos.chenall.net and don't know how to proceed. My intention was to install Ubuntu and then delete Windows. Also, if it will make any difference my PC is an old Dell Optiplex GX620.

And finally please keep in mind that I know very little about Linux based operating systems, but would like to learn more. 

Thanks in advance.

---

### Post by Autodave on 2019-01-07
Hopefully, someone with more experience than me will jump in.  But, if I were doing this and wasn't planning on keeping Win7 anyhow, I would let the installer wipe the disk and install.

Now, if you have a newer version of Win7 on that machine, you might need to disable *fast boot *in the BIOS.

Lastly, you could possibly have a bad install file.  The install medium: was it created on a Mac?  I have heard that causing problems, too.

---

### Post by anteevic on 2019-01-07
I disabled fast boot and all that, but the problem persists. Any other ideas?

---

### Post by oldfred on 2019-01-07
The standard Ubuntu installer does not use grub4dos which is based on the old grub (now grub legacy). Ubuntu has used grub2 since about 2009. Grub2 does not have error codes like grub legacy had.
What installer did you use to create Ubuntu installer?

       Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

---

