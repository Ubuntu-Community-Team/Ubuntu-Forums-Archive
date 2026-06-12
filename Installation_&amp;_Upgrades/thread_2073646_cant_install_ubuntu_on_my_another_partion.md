---
title: "cant install ubuntu on my another partion"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by vibaviattigala on 2012-10-20
i have windows xp i need to get ubuntu on Drive E so i moved my E stuffs to other partion now ready to install ubuntu on e but it says no root file system is defined . selected Ext4 which is right format on ubuntu right? then there is a mount opstion like / /booot what to do?

---

### Post by 2F4U on 2012-10-20
When do you get the error message, during installation or during booting an installed system?

---

### Post by Wim Sturkenboom on 2012-10-20
> **vibaviattigala said:**
> then there is a mount opstion like / /booot what to do?Choose /, that is the root file system.

Ubuntu might also want some swap space, so it might be better to delete your 'E drive' and split it in a smallish swap partition (size depends on size of memory and type of computer (desktop/laptop) and the rest for the root partition.

3rd option can be to make three partitions; smallish one for swap, 25GB for the root partition and the rest for the home partition where you're data goes (like 'my documents' in windows). But it depends on the size of the 'E drive' what is the best option.

---

