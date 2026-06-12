---
title: "Iommu.."
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Lexicon101 on 2008-09-06
Ok, I installed the testing beta of Intrepid, and immediately upon boot-up, it tells me my motherboard isn't leaving an aperture hole or something, and that I should enable the "IOMMU" setting on my mobo.. Well, I did a *little* reading on this, and found that IOMMU refers to remapping the ram.. (I might be wrong on that count, I didn't fully understand it.) It seems to me that this is about full 4gb ram support.. Well, my question is, what exactly is this, and has anyone else encountered it? From what I understand, it can break a select few programs like VMs and stuff.. Well, I basically want to know if it's a good idea, and what the pros and cons are..

---

### Post by Rocket2DMn on 2008-09-06
Moved to Intrepid Ibex Testing and Discussion, good luck with your problem, hopefully somebody here can help.

---

### Post by thaumielx72 on 2008-09-06
> **Lexicon101 said:**
> Ok, I installed the testing beta of Intrepid, and immediately upon boot-up, it tells me my motherboard isn't leaving an aperture hole or something, and that I should enable the "IOMMU" setting on my mobo..  Well, I basically want to know if it's a good idea, and what the pros and cons are..

I also recieved this message on my laptop every time I booted it up.  (AMD64 Athlon X2, 4 GB RAM) I went to the boot options screen as it suggested and there was no mention of IOMMU.  Is there another way to test this feature?:confused:

---

### Post by Hershey on 2008-09-06
If you are seeing something like this and you are not using an AGP video card:

```

[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 20000000 size 32 MB
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Please enable the IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000

```

Adding "iommu=noaperture" to the kernal parameters will get the error to disappear. (/boot/grub/menu.lst)

Here's mine for reference:

kernel		/boot/vmlinuz-2.6.27-2-generic root=UUID=8116c71f-703c-45f2-b7cd-e4e395578ee8 ro quiet splash iommu=noaperture

---

### Post by Nullack on 2008-09-06
Are you running amd64 with 4gb of ram?

---

### Post by Hershey on 2008-09-08
> **Nullack said:**
> Are you running amd64 with 4gb of ram?

Yup.  My motherboard is a ASUS M2N-E.

---

### Post by bpl07 on 2008-09-08
I also have been adding the iommu=noaperture entry since gutsy and it has fixed my problems.  Check your bios to make sure there isn't a setting for iommu in there first though.  My bios didn't have a setting so I had to use this fix, but ideally the bios setting would fix it.

---

### Post by TheSky on 2008-10-20
Hi! I'm a new member from Italian community.

I have the same problem. This is my hardware:

CPU AMD Phenom x4 9550;
MB Sapphire AM2RX780 with AMD 700 chipset;
RAM 4096 DDR2 PC6400.

When I try to start up installation, I get this message on screen:

[I]Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup
This costs you 64 MB of RAM


Kernel alive
Kernel really alive[/I]

If I try *iommu=noaperture* option, i get only [I]Kernel alive
Kernel really alive[/I]

I think it could be a bug.

Thank you :)

---

