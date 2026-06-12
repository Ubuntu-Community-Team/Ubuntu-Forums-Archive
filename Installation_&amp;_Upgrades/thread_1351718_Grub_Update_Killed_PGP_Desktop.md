---
title: "Grub Update Killed PGP Desktop"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by madmonkeyz on 2009-12-10
I've a dual-boot Windows 7/Ubuntu 9.10 Dell work laptop. The Windows 7 partition needs to be encrypted using PGP Desktop. My typical start-up would be PGP BootGuard would start first prompting for a password/pass-phrase, then the Grub menu list provide boot options (Ubuntu kernels and/or Windows 7). I installed Windows first then Ubuntu (as Ubuntu is much kinder :D)

After today's upgrade (I wasn't paying attention and included the Grub update) now start-up goes right to Grub menu - bypassing the BootGuard loader (I suppose the MBR got stomped); which unfortunately renders my Windows 7 partition useless.

I am wondering if there is a way to recover my original MBR (for PGP Desktop) and preserve the Grub menu list?

I am planning on trying to "recover" with a PGP boot-up recovery disk, but I am additionally concerned that Grub may also be destroyed.

I am hoping someone has encountered this issue and has a less frantic state of mind than I do right now.

---

### Post by madmonkeyz on 2009-12-10
bump

---

### Post by madmonkeyz on 2009-12-11
*bump*

---

### Post by madmonkeyz on 2009-12-11
If anyone is experiencing the same issue -> create a PGP recovery Disk. Make sure you use the EXACT same version that is installed. If you are using 9.10 use 9.10 - seriously. [https://pgp.custhelp.com/app/answers/detail/a_id/471]("https://pgp.custhelp.com/app/answers/detail/a_id/471")

Boot from the CD -> magically the BootGuard (loader -> whatever its' called) will prompt for your passphrase. GRUB menu will appear and you can select your Windows 7 partition and everything is groovy. However, this is temporary. You will only be able to boot to your Windows partition if you have the CD.

The only thing I can figure out at this point is to Decrypt the entire partition (using the PGP Desktop interface). Reboot. Ensure that GRUB and both partitions are happy. Then, RE-ENCRYPT the Windows partition to allow PGP Desktop to do whatever it does to the MBR. Then its business as usual. As there *seems* to be no way to "fix" the MBR without going through the process.

Note to self (and those within ear-shot): Be very wary of GRUB updates on a dual-boot with PGP Desktop. Hope this helps someone.

---

### Post by jcma1987 on 2011-05-23
I'm experiencing the same issue at the moment, did you find a resolution other than decrypting the HD?

---

### Post by madmonkeyz on 2011-05-23
Wow - its been so long. For that particular machine - no. The aforementioned instructions are what I had to do to recover. On subsequent updates - since (maybe...Ubuntu 10.04) Grub seems to have behaved better -> if given the option (next time); change the drop-down to "Keep existing" rather than regenerate the .cfg. Hope that helps.

---

### Post by jcma1987 on 2011-05-24
Ah, unfortunately I didn't choose that option when updating Ubuntu so the MBR was overwritten, seems you and I are the only ones to have shared our experiences of this issue with a PGP encrypted Windows partition!

Thanks for the reply anyway, I've handed the laptop over to our IT helpdesk to have an image of the Windows partition taken and restored. Lesson learned for the future! :)

---

### Post by Busterdog on 2012-03-02
I just did the same thing. How can I know what version of recovery CD to use if I cannot boot the partition and look at it?

---

### Post by jcma1987 on 2012-03-02
Hi, I'm not sure on this, unfortunately I ended up having to wipe clean the HD and restore the windows partition.

Sorry I can't be of more help! Best of luck

---

### Post by ottosykora on 2012-03-02
> **madmonkeyz said:**
> Wow - its been so long. For that particular machine - no. The aforementioned instructions are what I had to do to recover. On subsequent updates - since (maybe...Ubuntu 10.04) Grub seems to have behaved better -> if given the option (next time); change the drop-down to "Keep existing" rather than regenerate the .cfg. Hope that helps.

interesting, I would like to know what is then the end status of the operation.
Clearly, the pgp mbr is needed to start up the on the fly decryption, this is with many of similar tools that way and makes sense.

But where do you have your grub installed then?
How do you boot the ubuntu?
Is your grub in fact installed in the ubuntu partition (pbr)?

---

