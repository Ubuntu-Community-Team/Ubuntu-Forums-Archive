---
title: "LILO problem after upgrade EBDA"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by JonH on 2007-01-01
Just upgraded from 2.6.06 to 2.6.10.  went well and asked to reboot.  on reboot got the message "Loading Kernel...EBDA is big; kernel setup stack overlaps LILO second stage"

I have no idea what this is, can anybody help??  i have a multibot system using LILO as the boot loader.  4x SATA disks (tried GRUB and it doesn't work)  i think it is problems recognising the sata disks.

many thanks.

---

### Post by JonH on 2007-01-02
For those that have the same problem.  the solution was to re-boot under Xandros (the LILO) boot loader.  Select Xandros, check that /etc/lilo.conf has been updated to the correct Ubuntu version.  re-run lilo at the terminal prompt and it will re-write the correct links for the bootloader to load the new version of Ubuntu!

Good luck!!  Jon

---

### Post by satb on 2007-01-14
I'm on a Macbook, and just got this error after a kernel update... It worked fine for a couple of times, but then suddenly it hit me.

I used this solution, except for me having my ubuntu install on /dev/sda3 (I've got a basic triple-boot system):

[http://www.hantslug.org.uk/cgi-bin/wiki.pl?LinuxHints/LostLILO]("http://www.hantslug.org.uk/cgi-bin/wiki.pl?LinuxHints/LostLILO")

And I'll mark the exact steps here, as it's propably good for some Macbook people and beginners like-me:

1. Boot off the Ubuntu install CD.
2. Open up a terminal. Go to /mnt. Create a directory called for example "lin". And mount your old linux installation partition there:

```
cd /mnt
sudo mkdir /mnt/lin
sudo mount -o rw /dev/sda3 /mnt/lin

```

3. Bind-mount these directories:

```
sudo mount --bind /proc /mnt/lin/proc
sudo mount --bind /sys /mnt/lin/sys
sudo mount --bind /dev /mnt/lin/dev

```

4. Set up a chroot so that you can access everything correctly on the mounted partition:

```
sudo chroot /mnt/lin /bin/bash
```

(
Note that you **DON'T** have to do this if you are running a **Macbook with triple-boot**, but I'll include it for those who have a basic Ubuntu setup with a separate /boot partition:
5. Mount your /boot drive under /mnt (if you don't have a /boot partition, then you can safely ignore this). Note, substitute /dev/hdaX as appropriate:
```
mount /dev/hdaX /boot
```
)

6. If you for some reason need to edit your lilo.conf, you can do it with nano (Ctrl-X exits the program), but I didn't have to do anything to it:
```

nano /etc/lilo.conf

```
7. Update lilo with (-v means verbose, so that it prints all off it's output):
```

/sbin/lilo -v

```
8. Check that there are no errors (It always complains about some things on my Macbook, but it usually still works). Then you can exit chroot, and reboot the computer with:
```

exit
init 6

```

9. It *should* work now.

---

