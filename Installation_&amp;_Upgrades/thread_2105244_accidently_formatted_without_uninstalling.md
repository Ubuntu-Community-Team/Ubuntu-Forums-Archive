---
title: "accidently formatted without uninstalling"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by Coolguy137 on 2013-01-15
hi,
i accidently formatted the disk i had with ubuntu and now in the boot i have ubuntu but i need to delete it 
what can i do?

---

### Post by Laiquendi on 2013-01-15
What do you want to do - recover the Ubuntu partition or delete it from the GRUB?

---

### Post by darkod on 2013-01-15
Did you have ubuntu or you had wubi inside windows? You have to be precise. Many people think wubi is exactly the same as ubuntu and don't mention it's wubi.

If you are using grub2 from ubuntu to boot and you deleted the ubuntu partition, it wouldn't work at all. So, since you say you can see an option for ubuntu in your boot menu I assume it's the windows bootloader and you had wubi installed.

Or some kind of custom setup with the bootloader. Which bootloader are you using?

---

