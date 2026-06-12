---
title: "Which Grub installation?"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by gseward on 2010-01-16
I have two Ubuntu installations on my computer, the first was Ubuntu 9.10, on sda6, which I have used since it was released, and I recently added 10.04 beta2 on sda8.  It is now using the Grub from the later 10.04 installation and I would like to be using the older 9.10 grub on sda6. [I may uninstall the 10.04 beta].  How can I switch back to the sda6 Grub.
p.s.  They are both Grub2 [version 1.9x].

---

### Post by kansasnoob on 2010-01-16
> **gseward said:**
> I have two Ubuntu installations on my computer, the first was Ubuntu 9.10, on sda6, which I have used since it was released, and I recently added 10.04 beta2 on sda8.  It is now using the Grub from the later 10.04 installation and I would like to be using the older 9.10 grub on sda6. [I may uninstall the 10.04 beta].  How can I switch back to the sda6 Grub.
p.s.  They are both Grub2 [version 1.9x].

If you can boot into 9.10 you should just be able to go to Terminal and run:

```
sudo grub-install /dev/sda
```

If that returns any errors:

```
sudo grub-install --recheck /dev/sda
```

Then:

```
sudo update-grub
```

Wait for it to say "done", it should find 10.04.

If for some reason you can't boot into 9.10 then you could mount and chroot 9.10 on sda6:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

Just to be sure you mounted the correct OS:

```
lsb_release -a
```

Now install Karmic's grub2 to the mbr:

```
grub-install /dev/sda
```

If that returns any errors:

```
grub-install --recheck /dev/sda
```

Then just exit chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then when you boot into Karmic the first time run:

```
sudo update-grub
```

That should find Lucid.

---

### Post by gseward on 2010-01-17
Thank you very much kansasnoob, that did the trick.  If I understand correctly, whichever version I was running when I issued the "sudo grub-install /dev/sda" command would be the one whose grub menu would then be used?

---

