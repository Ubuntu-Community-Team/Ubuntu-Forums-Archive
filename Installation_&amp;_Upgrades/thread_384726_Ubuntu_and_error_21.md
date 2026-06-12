---
title: "Ubuntu and error 21"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by nazg on 2007-03-14
Ok, i've installed kubuntu in my external HD that connects via USB. Everything seems ok. But when i boot the laptop, and when grub wants to start i get this error "...error 21". But if i reboot the laptop (pushing the power off button), the error message no longer appears and it boots normally. However, i have to do this everything i boot the laptop.

I think that when i boot the laptop, the external HD takes more time to start, but when i reboot the HD stays turned ON and then the error message no longer appears. 

So my question is: Should i move grub from MBR to sda1 (aka external HD)? How do i do that?

Thanks

---

### Post by silhouette on 2007-03-14
Error 21 means that the device could not be found, so you very well may be right. To manually install GRUB, you need to get to the GRUB prompt (press Escape right after you see "loading stage 1.5"), then type something like:

```
root (hd0,0)
setup (hd0)
```

Of course, most likely your drive isn't hd0,0 so you need to change those numbers so GRUB can see your drive. See the [GRUB documentation](http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html#Naming-convention) for more.

---

### Post by Kateikyoushi on 2007-03-14
Did you try to boot without the external hdd ?

---

