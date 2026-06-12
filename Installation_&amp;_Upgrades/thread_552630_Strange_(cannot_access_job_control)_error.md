---
title: "Strange (cannot access job control) error"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by jose_rizal on 2007-09-16
Hi,

Im new to linux and have just installed it and im now getting the dreaded (cannot access job control error).

The wierd thing though is I can boot into Linux if I select [boot from first hard drive] in the start menu. I have installed ubuntu 7.04 using both live cd and the alternate one and the same thing happens. As it goes, I am actually posting this in ubuntu right now :)

I would however like to be able to boot it normally and not like this every time. I have been searching through threads and trying things especially modifying the /etc/initramfs/modules file but I notice my hard drive is called sda1 rather than with an h prefix. I wonder if this makes a difference?

I know there&#347; a lot of threads on this but I thought my particular problem might be different as I can strangely boot into linux (albeit through boot from first hard disk). Does anybody know of any other solutions I can try?

---

### Post by Pumalite on 2007-09-16
Here is a mix of fixes. See if you can find one suitable to your particular problem:

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.
ust a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by jose_rizal on 2007-09-16
Thanks for the quick reply!

Unfortunately, that was one of the fixes I already tried :P

I'm thinking of maybe just reinstalling everything using dban and gparted, do you think this could make a difference (or maybe just screw everything up even more? :) )

---

### Post by Pumalite on 2007-09-16
I suspect you have low memory. Post your specs and I can help you better.

---

### Post by jose_rizal on 2007-09-17
My specs: P4 3.0ghz, 1GB ram, Geforce 6600 mx. My PC ran Windows XP before I reformatted and installed UBUNTU 7.04.

Its very weird how I can still boot into my system by clicking on "boot from first hard disk" yet my system will not boot by itself. Perhaps this is due to the fact that the starting scripts are not configured correctly? Can any linux expert please give me a hand? Thanks! :)

---

### Post by Pumalite on 2007-09-17
Re-install Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

