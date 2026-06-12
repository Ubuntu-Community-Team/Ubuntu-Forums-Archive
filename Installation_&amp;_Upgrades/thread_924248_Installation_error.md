---
title: "Installation error"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by Javaslinger on 2008-09-19
I'm installing Ubuntu 8.04 on a Gateway FX laptop Core 2 Duo system.

The installation failed and I received the following error.

(intramfs) [96.590465] ata6.00:revalidation failed (errno=-05)
           a6: exception Emask 0x1 SAct 0x10 SErr 0x0 action 0x0 t4
           a6: irq_stat 0x40000008

I am a windows user, so I'm lost...

Edit:  I have a Serial ATA hard drive.  I understand Ubuntu has issue with them?

Thanks in advance,

javaslinger

---

### Post by Javaslinger on 2008-09-20
Some help please????

Javaslinger

---

### Post by Vivaldi Gloria on 2008-09-20
See the "installation problems" in my sig. Especially look at part 10.

---

### Post by wpshooter on 2008-09-20
> **Javaslinger said:**
> Some help please????

Javaslinger

Before attempting to install the Ubuntu O/S, did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by manishtech on 2008-09-20
> **Javaslinger said:**
> 
(intramfs) [96.590465] ata6.00:revalidation failed (errno=-05)
           a6: exception Emask 0x1 SAct 0x10 SErr 0x0 action 0x0 t4
           a6: irq_stat 0x40000008
Edit:  I have a Serial ATA hard drive.  I understand Ubuntu has issue with them?


When are you getting this error? Immediately after the installation failed or after you restarted the system before GRUB listing? Or after you selected Ubuntu from GRUB List?

Apart from this, I dont think Ubuntu has issues with SATA drives. It works properly as far as I know.

---

### Post by imacrazywoman on 2008-09-24
I also have a Gateway FX with a Centrino 2, 4gb ram, 200gb sata hdd, nvidia geforce 9800gts, and windows vista 64-bit.  I get the same error message and the installation stalls out.  I've tried burning both the 32-bit and 64-bit ISOs (with ISO Burner) and I have also bought the CD thinking that it was just bad DVDs.  Same issue with all 3 discs.  I noticed in the bios that the HDD is set up as AHCI and not IDE, could this be a problem?

---

### Post by imacrazywoman on 2008-09-25
Ok, did some forum trolling and found the fix. You need to disable the USB legacy support in the bios. Once I did that, Ubuntu loaded and is currently installing just fine.

---

### Post by zuheyr on 2008-10-28
Hello,

I have the same problems with the Ubuntu 8.0.4 on my Dell Inspiron 530S with Core 2 duo: the revalidation error.

I am glad to see in your post that you need to disable the USB Legacy in the Bios. I fail to see how can I do this, sorry I am not very good with the Linux OS. Could you please help me? 

Many thanks for reading, Regards
Zuheyr

---

### Post by AaronDev on 2008-10-28
Try adding **irqpoll** to the boot options [F6]

---

### Post by zuheyr on 2008-10-28
Thank you, but I am booting from the live CD, how can I change the boot options? 

Zuheyr

---

