---
title: "2 Disks ea w Ubuntu on BTRFS - grub os-prober fails to find OS on 2nd Disk"
date: 2017-11-27
forum: Installation &amp; Upgrades
---

### Post by bmullan2 on 2017-11-27
I have a*** server*** with four 2 TB drives on it.
  
I have installed Ubuntu on Drive A and Drive B.

The BIOS is set to Boot from Drive A and it does that ok.

If I connect a monitor & keyboard to the Server ***I can use the BIOS to boot from Drive B okay also.***

I rebooted to ubuntu on Drive A okay and then ran **update-grub** but the ***Grub2 os-prober only seems to search & find ubuntu on Drive A*** ... it doesn't seem to look at Drive B.

  Is this due to both Drive A and B having Ubuntu installed on **btrfs**  and the Grub2 os-prober unable to search Drive B for other Ubuntu installs?

 Is the editing & modification of /etc/grub.d/40_custom the only way to accomplish this when you have multiple BTRFS disks each with their own OS installed ?
 
I had understood Grub2 supported multiple disks each with their own OS installed and would on boot present a menu allowing selection of which OS (and thus which disk) to boot from ?

Thanks for any ideas.

---

