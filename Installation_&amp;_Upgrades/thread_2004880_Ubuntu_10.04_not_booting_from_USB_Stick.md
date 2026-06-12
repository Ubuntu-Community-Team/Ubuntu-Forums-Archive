---
title: "Ubuntu 10.04 not booting from USB Stick"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by Blackbelt2011 on 2012-06-16
Hi,

I have a **Live-System Boot DVD** with Ubuntu 10.04.
There is a utility installed on the DVD to create a new boot medium.
I plugged in a new empty Kingston 4GB memory stick (the system uses 3 GB for itself), and it was found by the utility program.

I can see that there are probably all folders written on the stick: .disk, casper, desinfect, preseed, syslinux, and the files urdrive, unInstaller and casper-rw.

But when I try to boot from this stick, there is an error message **"vesamenu.c32: not a COM32R image".** I don't know what this means.
then there is a prompt: **boot:** but there is no booting.

I want to keep this special DVD from the c't magazine, because it contains 4 virus scanners. Can anybody give me a hint to boot a Laptop from that stick? With the DVD there is no problem, but on the USB stick it does not work.

Thanks
Blackbelt2011

---

### Post by N0oki3 on 2012-06-16
Hi, I have searched a bit for you and i found this 2 solutins (but i can't guarantee that they will work)

#1
> Type "Live" and enter. Linux should boot up normally

#2
> copy vesamenu.c32 from Ubuntu live USB. The USB now boots.

---

### Post by Blackbelt2011 on 2012-06-16
I entered** live** at the boot prompt, but the system does not start.
As far as I know there is the kernel **vmlinuz **must be started first?
Linux shell commands as **"ls"** do also not work at that prompt....

I do not understand the message of the **vesamenu.c32 **file, because the file is on the stick in the **folder isolinux **as well as on the original DVD in the same folder isolinux. The size 144KB is the same.

Maybe I try to write the stick again just on another machine...

---

### Post by N0oki3 on 2012-06-16
> **Blackbelt2011 said:**
> 
Maybe I try to write the stick again just on another machine...
Have you tried to copy paste the file from dvd to usb ? Might be corrupted

---

### Post by wilee-nilee on 2012-06-16
Generally a ISO loaded to a usb thumb with the correct tool should boot.

Did you extract the dvd, then use a utility like unetbootin to load the thumb?

I believe you would have to have an ISO with unetbootin, there are a number of usb flash loaders.

Do you have a link to this dvd for info?

---

