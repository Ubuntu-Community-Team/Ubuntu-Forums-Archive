---
title: "kernel panic!!"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by IGNIZ on 2006-12-25
hi all, i tried to install the edgy eft distro but i got a bad kernel panic problem.

so i tried to upgrade my dapper using aptitude, and when i use the old kernel all runs smoothly, but when i use the new one it gives me this kernel panic:

not syncing: attempted to kill init!


i'm a bit desperate... because i uninstalled the old kernel and now i've got a big useless pc full of panic ](*,)...

---

### Post by brt on 2006-12-25
you can try to add the option "noapic" to your kernel boot options.

if you are at your grub menu at bootup, select the kernel you want to boot, 
but instead of <return> press "e"  to see the boot options of this kernel.

select the line which starts with the word "kernel":
eg.
   kernel		/vmlinuz-2.6.17-10-generic root=/dev/hda ro quiet splash

again press "e" to edit this line and at the end of the line add the word:  noapic

the line should now look similiar to this:

   kernel		/vmlinuz-2.6.17-10-generic root=/dev/hda ro quiet splash **noapic**

press <return>

and press "b" to boot this configuration.

if this does not help you can also add: noapic nolapic 

if it helped you have to edit your grub menufile to make the change persitant:

sudo gedit  /boot/grub/menu.lst

look for the line
# defoptions=quiet splash

and add your options, save and close the file and execute:
sudo update-grub

good luck!

---

### Post by IGNIZ on 2006-12-25
thanks for the help but it still gives me the same error ](*,)

i wonder what to do :confused:

---

### Post by brt on 2006-12-26
hmm sounds bad :(

you could try to install a working kernel from a live CD. 

 - boot from your Live CD 

 - mount your root partition, e.g.:
```
sudo mount /dev/hda1 /mnt
```

instead of /dev/hda1 you must use the correct value for your root partition.

then copy the needed files to your /boot folder on your harddisk:

```
sudo cp /boot/vmlinuz* /mnt/boot
sudo cp /boot/System.map* /mnt/boot
sudo cp /boot/initrd.img* /mnt/boot
```

chroot too your root on the harddisk using:

```
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc/ /mnt/proc/
sudo mount -o bind /sys /mnt/sys
sudo chroot /mnt
```

tell grub to rebuild your kernel list:

```
update-grub
```

now reboot and you should have a new kernel available in the grub-menu.

once again, good luck (fingerX)

---

### Post by IGNIZ on 2006-12-26
thx! but i've reinstalled dapper and upgraded it. still the new kernel doesn't work, but i can use the old one... i should try to recompile the new one?

---

### Post by brt on 2006-12-26
recompile?

if everything works with the old one you should be fine...

if you have compiled the new kernel yourself and are unable to boot, 
maybe you have not created an initrd.img ? 

```
sudo update-initramfs -c -k 2.6.17.1
```

then you will have to run:

```
sudo update-grub
```

---

### Post by IGNIZ on 2006-12-26
i'm not sure the old kernel is good... when i boot i can only see the progress bar and nothing else

---

