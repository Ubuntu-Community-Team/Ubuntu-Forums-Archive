---
title: "Specified backup with Clonezilla"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by mrwave2002 on 2010-11-28
Hello.
I want to ask you if i can backup with clonezilla only /home sda3 directory.
And to backup sda1 and Linux Swap with another program as Acronis and then to restore the sda1 and Linux Swap With Acronis
on a formated Hdd and restore then /home with Clonezilla.
Is this capable?

---

### Post by SecretCode on 2010-11-28
You can't backup a single directory as such, but you can backup and restore a single partition - I assume this is what you mean - your sda3 is mounted as /home.

Why do you want to do this?

There is no reason to backup the swap partition!

---

### Post by matt_symes on 2010-11-28
Hi

> **mrwave2002 said:**
> Hello.
I want to ask you if i can backup with clonezilla only /home sda3 directory.
And to backup sda1 and Linux Swap with another program as Acronis and then to restore the sda1 and Linux Swap With Acronis
on a formated Hdd and restore then /home with Clonezilla.
Is this capable?

You can use clonezilla to back up /home and /. You don't need two separate programs.
Don't bother with the swap partition.

kind regards

---

### Post by mrwave2002 on 2010-11-28
> **matt_symes said:**
> Hi



You can use clonezilla to back up /home and /. You don't need two separate programs.
Don't bother with the swap partition.

kind regards

Hello the reason i've asked you this is because i don't know if the image creation with 
Clonezilla, can support another Hardware. What happens if my Motherboard Burned,
or my Vga? Can the image with Clonezilla be opperational?
On the other hand Acronis maybe has a chance?

Ubuntu 10.04. DesKtop Pc.

---

### Post by matt_symes on 2010-11-28
Hi

> Can the image with Clonezilla be opperational?

That will depend on the OS and not the cloning software

Kind regards

---

### Post by mrwave2002 on 2010-11-28
> **matt_symes said:**
> Hi



That will depend on the OS and not the cloning software

Kind regards
What if the Os is Ubuntu 10.04?

---

### Post by mrwave2002 on 2010-11-29
I guess i will use Clonezilla after all!
The subject is closed.

---

### Post by Quackers on 2010-11-29
I have had no problems with Clonezilla, whether backing up Windows, Lucid or Maverick. It will clone discs or partitions as you choose.
If you are happy please mark the thread as solved using the Thread Tools near the top of the page (in red).

---

