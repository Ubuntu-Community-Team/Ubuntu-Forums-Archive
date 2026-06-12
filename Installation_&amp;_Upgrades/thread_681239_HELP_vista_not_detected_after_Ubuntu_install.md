---
title: "HELP vista not detected after Ubuntu install"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by egoneo on 2008-01-28
hi, first off before i installed ubuntu i had two partitions, one was for vista and the other was a recovery one. Since i didn't need the recovery one anymore, i formated it in the ubuntu installation and installed ubuntu on it. All went well until i booted the computer and now in the boot menu it only gives me options to select ubuntu and not vista. I tried going to the recovery bit in the vista installation, but it doesn't even detect any os's. I can see all my  windows files and directories in ubuntu, so i know i haven't accidently overwritten it. What should i do?

---

### Post by Partyboi2 on 2008-01-28
You could try  [supergrub]("http://supergrub.forjamari.linex.org/")

---

### Post by Shootfast on 2008-01-28
I think it has something to do with marking the active partitions. Vista likes to be installed to an active partition, so if it gets unmarked, the recovery tool doesn't see it.

If you are sure you know which hard drive it is on, you can have a go at manually adding vista to grub (the linux bootloader)

try in terminal

```
sudo gedit /boot/grub/menu.lst
```

and then scroll down to the bottom and paste in

```
title             Windows Vista
root             (hd0,0)
makeactive
chainloader +1
```

That's assuming that vista was installed on partition 1 of hard drive 1.

Hope that helps.

---

