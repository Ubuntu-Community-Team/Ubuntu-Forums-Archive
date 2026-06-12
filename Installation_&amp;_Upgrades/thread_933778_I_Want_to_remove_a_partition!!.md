---
title: "I Want to remove a partition!!"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by Spoken on 2008-09-29
so right now i have vista home basic and Ubuntu on my harddrive.  due to reasons that must remain untold.  i need to remove vista and make ubuntu in control of the entire hard drive.

can i do this with the ubuntu live cd?  how so?

any other ways without having to boot up the vista partition?

---

### Post by Partyboi2 on 2008-09-29
Yes you can, you can use gparted (System>Admin>Partition Editor) and delete the vista partition then resize ubuntu to make use of the unallocated space. You may also need to remove (or comment out) the vista entry from your grub menu.lst as well.

---

### Post by Spoken on 2008-09-29
ok ive opened up the partition editor program, however, idk how to use it.  ive deleted the vista partition, but idk how to relocate all of the unused space back to my linux partition.

any help?

---

### Post by Partyboi2 on 2008-09-29
Can you post of a screenshot of gparted?

---

