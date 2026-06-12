---
title: "windows wont boot"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by arch_angle07 on 2007-10-06
im typing this form the ubuntu live cd, I tried to partion my hd from gnome partition editor, their was an error when I tried to resize the ntfs partition, I closed that restarted my computer and tried to boot into windows. it gave me an error message, but I know my files are still on the computer because now on my live cd desktop I have a new folder titled hp_pavilion that contains what used to be my windows c:\ drive, does anyone know why windows will not work, and is their anyway to get both ubuntu and windows working from this point.

---

### Post by Pumalite on 2007-10-06
If there is still Windows, you can use your CD Installation>hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by arch_angle07 on 2007-10-06
ok i will try that

---

### Post by arch_angle07 on 2007-10-06
:sorry for double post:

my windows cd wont work for some reason, but I can get into the command prompt, is their anyway to restore from their.

---

### Post by Pumalite on 2007-10-06
Can you boot from your CD and if so what do you encounter?

---

### Post by arch_angle07 on 2007-10-06
I fixed it, i'd tell you what I did but I really dont know what I did. I will tell you what I think I did

I went into the partitioner in linux, and their was an 8gb partition that was unused,in front of my ntfs partition. I made the unused partition into an ex3 partition, what I think was happening was when windows went to boot it saw the unused space and found no files so it didn't boot, since it's now an ex3 it skips over that and moves on to the windows files. at least thats what I think it's doing

but i dont care windows is working again, and ill try getting ubuntu installed later.

---

### Post by Pumalite on 2007-10-06
Good for you.

---

