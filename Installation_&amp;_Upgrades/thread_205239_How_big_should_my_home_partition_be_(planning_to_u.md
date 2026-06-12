---
title: "How big should my /home partition be? (planning to use VMware)"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by Gimbo on 2006-06-28
I know the answer to this is "it depends", but I'm just looking for a rough figure (my hard drive is 120GB).

I'm currently dual-booting with Windows XP, but now I've got my install CD in the post I'm thinking of doing a clean install.

**What I really need to know is where VMware or other virtualisation tools keep all their files. Do I need to leave space for them on the / [root] partition?**

---

### Post by mhancoc7 on 2006-06-28
Vmware creates a virtual harddisk located inside the vmware folder located in your /home/yourusername/ folder. You can preallocate the disk or you can let it expand as necessary. I choose to preallocate it because it is supposed to be faster that way. I set mine at 15GB. I have a full Windoze XP install on it with tons of extras such as VB.net, Micro$oft Office, etc. I have plenty of space left over. I can also access my /home/yourusername/ folder via Network Places from within my virtual Windoze XP. So I have access to my whole drive space. 

I hope that helps. 

Jereme

---

### Post by Gimbo on 2006-06-28
That's exactly the info I was looking for. Thanks very much.

---

### Post by mhancoc7 on 2006-06-28
No problem. If you ever have any questions just shoot me a private message.
Jereme

---

