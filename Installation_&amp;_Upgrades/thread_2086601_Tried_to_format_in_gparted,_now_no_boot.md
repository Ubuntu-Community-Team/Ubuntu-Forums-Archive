---
title: "Tried to format in gparted, now no boot"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by TheCanonKid on 2012-11-21
Hi, I recently received an old desktop from a friend so I popped in a new 500GB Seagate HDD and loaded gparted to format the drive for Ubuntu. It errored out and I repeatedly get the "No disks reserved for raid use, raid disabled." I have been through the bios and I'm fairly certain that it does not show any drives. The sata cable is new, the desktop is only about 3 years old. It's an HP Pavilion P6130Y with 8GB RAM, AMD Phenom X4, and Pegatron M2N78-LA mobo. I've been researching for several days now and I cannot find anything. Any help would be appreciated!

---

### Post by darkod on 2012-11-21
Is the SATA Port mode in RAID or AHCI or IDE?

The message mentions raid so it must have something to do with the onboard raid function of the board. Take a closer look, and disable raid if not using it. The commonly used option is AHCI unless using RAID.

If the BIOS doesn't show the disk, then no OS or tool will see it. First the BIOS has to show it.

If it has RAID enabled maybe it expects to see a configured raid array and ignores a single disk, so it might not "show" it to the OS. But in some BIOS section it has to be shown as existing disk.

---

### Post by TheCanonKid on 2012-11-21
> **darkod said:**
> Is the SATA Port mode in RAID or AHCI or IDE?

The message mentions raid so it must have something to do with the onboard raid function of the board. Take a closer look, and disable raid if not using it. The commonly used option is AHCI unless using RAID.

If the BIOS doesn't show the disk, then no OS or tool will see it. First the BIOS has to show it.

If it has RAID enabled maybe it expects to see a configured raid array and ignores a single disk, so it might not "show" it to the OS. But in some BIOS section it has to be shown as existing disk.

the SATA1 port was set to raid but I changed it to AHCI but not it says "Reboot and select proper Boot device or insert Boot Media and press a key." I put in both the Ubuntu discs and the vista disc and restarted a few times but it keeps returning that same message

---

### Post by TheCanonKid on 2012-11-21
Ok so based on that, does it sound like a failing mobo?

---

### Post by darkod on 2012-11-21
So it looks like you had it in raid earlier, you should have noticed that. The formatting it did might have been raid related.

Regardless of that, it should boot from the ubuntu cd right now, and probably you will have to wipe the disk and start all over again.

Booting from the cd doesn't work also?

---

### Post by TheCanonKid on 2012-11-21
It was initially in raid. When I boot up, I press escape for the boot menu but it goes straight into "Reboot and select proper Boot device or insert Boot Media and press a key."

---

### Post by TheCanonKid on 2012-11-21
Thank you for your help, I really appreciate it but I'm just going to junk the tower. This was probably the reason they got rid of the tower in the first place

---

