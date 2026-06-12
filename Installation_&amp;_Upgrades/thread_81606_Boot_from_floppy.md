---
title: "Boot from floppy"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by papersith on 2005-10-24
Would like to know how to set up Ubuntu to boot from a floppy.

I currently have XP on a SATA HD and intend to install Ubuntu on an ATA HD.  I want to do this as not to mess up the windows bootloader.  

Thanks

---

### Post by taurus on 2005-10-24
Why not boot ubuntu directly from a CD!  Why would it mess up your bootloader if you just boot it from a CD.  Now, you need to install a bootloader to boot ubuntu once it's finished and grub can handle both ubuntu and your so call windows xp...

---

### Post by SilentCacophony on 2005-10-24
Hi. There is a thread on restoring GRUB that has instructions for also making a boot floppy. See the comment following the original post, [here]("http://ubuntuforums.org/showthread.php?t=76652").


There is also a method from the official GRUB FAQ: 
[http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q4](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q4)
which can be done like so:

If you're running 'Breezy' (Ubuntu 5.10), then you should already have an /etc/fstab entry for your floppy drive. I will assume that is the case.

Insert a blank floppy disk, open a terminal, and enter the following commands:

```
sudo su
```

(enter password if necessary, and you'll have root access)

```
mkfs /dev/fd0
mount /media/floppy0
mkdir -p /media/floppy0/boot/grub
cp /boot/grub/stage1 /boot/grub/stage2 /boot/grub/menu.lst /media/floppy0/boot/grub
umount /media/floppy0
/sbin/grub --batch --device-map=/dev/null <<EOF
```

(here, the prompt will change to >)

```
device (fd0) /dev/fd0
root (fd0)
setup (fd0)
quit
EOF
```

(should see '...succeeded' near the end of the output)

```
exit
```

(goes back to user access)

This will make the floppy have the same boot menu as the one you currently have on the Ubuntu partition.

---

### Post by newbie2 on 2005-11-09
grub-install /dev/fd0
[http://66.249.93.104/search?q=cache:UR2DKYTEZToJ:www.linuxquestions.org/questions/showthread.php%3Fs%3D%26goto%3Dlastpost%26threadid%3D364472+grub-install+/dev/fd0&hl=en](http://66.249.93.104/search?q=cache:UR2DKYTEZToJ:www.linuxquestions.org/questions/showthread.php%3Fs%3D%26goto%3Dlastpost%26threadid%3D364472+grub-install+/dev/fd0&hl=en)

---

