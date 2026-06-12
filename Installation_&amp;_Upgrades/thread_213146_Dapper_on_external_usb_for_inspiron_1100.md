---
title: "Dapper on external usb for inspiron 1100"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by skendale on 2006-07-10
So now that I am happily using Ubuntu, my girlfriend really wants to dualboot  it on her laptop too. She is using a dell inspiron 1100, and when I checked the BIOS it seems to not support booting from USB...does anybody know if there is a BIOS version for this machine that supports booting from USB? I've done the google bit but haven't had any luck.:( 
If not, does anybody have any other ideas for booting from an external USB if the BIOS does not support it?
Thanks!
-skendale..

---

### Post by kb3hkg on 2006-07-11
is there a reason it has to be done by usb?

---

### Post by skendale on 2006-07-11
Yeah so the reason it has to be on usb is that she doesn't have any more space on her internal hd...i suppose if absolutely necessary we can work on clearing up some space on that but i figured try this first...

---

### Post by kb3hkg on 2006-07-11
is there a reason not to just run it using the live cd for now? booting from usb is usually very complicated.

---

### Post by skendale on 2006-07-15
a little bios update did the trick...dapper running now!

---

### Post by Biteableniles on 2006-07-16
For those whose computers cannot support booting from USB, even after a bios upgrade, the instructions available at the following link has allowed me to boot my external drive from any computer I've tried on. It may not be perfect (I don't know if you can remove the cd after boot, I haven't tried).

[http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html]("http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html")

Here's the text, from the site (in case the site goes down):

CREATE THE BOOT CD
The boot cd works like a boot floppy, but since lots of laptops (like mine) don't use floppy anymore, we need a boot cd. To do so is easy.

If your first system is a Linux
I. Just boot. Make sure after boot you have access to the external HD (and your freshly installed system). Then install the package syslinux. In Kubuntu you can just do so with adept (just search for syslinux and install).
II. Make a directory called bootcd (in your konsole: mkdir bootcd). Copy isolinux.bin into your new folder bootcd:

    cp /usr/lib/syslinux/isolinux.bin bootcd/isolinux.bin


III.Then copy the kernel image of your new system from /Path_of_your_new_system/boot to bootcd/linux.
In our example the command would be:

    cp /media/sda1/boot/vmlinuz-2.6.15-19-386 bootcd/linux


Of course the number behind vmlinuz depends on the version of the kernel ofr your new system. Just have a look into the /boot folder of your new system an you'll see. The command above does not only copy the file, but also rename the copy to "linux".
IV. Then copy the initrd.img of your new sytem from /boot to bootcd/initrd.img. In our example:

    cp /media/sda1/boot/initrd.img-2.6.15-1 bootcd/initrd.img


Here too, replace the number with your kernel and make sure that the copied file is renamed to initrd.img.
V. Then you'll create the isolinux.cfg file. Open kwrite and paste the following line:

    DEFAULT linux initrd=initrd.img ro root=(your-root-dev)


(your-root-dev) is the partition where you installed your new system, in our example the line would look like this:

    DEFAULT linux initrd=initrd.img ro root=/dev/sda1


Save the file in the bootcd folder.
VI. Now it's time to make the iso. Cd into the directory above bootcd and type this command into your konsole (all in one line without break):

    mkisofs -o bootcd.iso -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -J -hide-rr-moved -R bootcd/ 


And - voila - your iso! Burn it to cd and restart your computer.

---

