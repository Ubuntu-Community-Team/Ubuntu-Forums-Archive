---
title: "Grub Problem"
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by juno_cunil on 2013-11-09
i had win 7 and ubunto 12.04 working fine. after i was using ubuntu, it updated. when i tryed to restart and boot to win 7, it wudnt appear on the grub. i ran the command sudo update-grub and this is what appeard:


alvaro@alvaro-HP-Pavilion-dm4-Notebook-PC:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-43-generic
Found initrd image: /boot/initrd.img-3.5.0-43-generic
Found linux image: /boot/vmlinuz-3.5.0-42-generic
Found initrd image: /boot/initrd.img-3.5.0-42-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
done



what should i do to get my grub back to normal?

---

### Post by juno_cunil on 2013-11-09
i guess it should show the windows os there but it doesnt

---

### Post by oldfred on 2013-11-09
Did you leave Windows hibernated?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

