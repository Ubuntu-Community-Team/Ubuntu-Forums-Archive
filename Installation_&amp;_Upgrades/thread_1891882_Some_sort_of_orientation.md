---
title: "Some sort of orientation"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by hsaptus on 2011-12-06
Evenin',
I have a dual boot windows 7 and FC15 and i want to replace the FC15 with the new Ubuntu. However i am not so sure how to just replace the FC15 and keep up the dual boot. Any pointers on how to perform this upgrade?
Thanks in advance,
hsa :)

---

### Post by darkod on 2011-12-06
Are you happy with the sizes of the partitions you have for FC?
Do you have the standard root + swap partitions?

If the answer is yes, replacing it with ubuntu is very easy. Start the install and at the partitioning stage select Something Else (manual way).

It will show your list of partitions. Select the root and the button Change. Then just change the Use As to ext4, tick the format box and select the mount point /.
Do the same for the swap, the Use As is swap area, no pount point.

Make sure you select the correct partitions. Otherwise you might delete important data.

---

### Post by hsaptus on 2011-12-07
hummm, did that but now grub doesn't know what to load. :P :D
I think i'm in trouble.

---

### Post by darkod on 2011-12-07
The ubuntu installation installs its own grub. Unless you selected not to install it, and I think in 11.10 that option was removed.

It might be some conflict with your hardware, did you try running the live mode before installing?

---

### Post by hsaptus on 2011-12-07
yes, i did. No hardware conflict. Its just grub now doesn't load the  menu or shows what partition can be loaded.  All i have is the grub>  in a black window. If i press tab i have all the option of the grub, but  i don't know what to load. Can't believe i will actually have to format  and start all over again, installing windows 7 and then ubuntu.... hummmm :(

---

### Post by darkod on 2011-12-07
Hold on, too early to reinstall everything. Follow the link in my signature to run the boot info script. Post the result here as expleined there. It will show more details of your setup and boot.

---

### Post by hsaptus on 2011-12-07
ok, all sorted. Instead of been a lazy a@@ used google and of course, Ububtu's documentation :P
This solved my issue:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


:)

Now i can test ubuntu and unity. With the previous version of ubuntu, unity didn't work on my desktop (and i have a pretty normal ASUS quad-core, 4gb ram with  a decent asus graphic card, etc) and whit this one, it runs... so lest see why is everyone ratting unity :D

Still, many thanks Darkod, thats was very nice of you. This is why i love nix so much, there is always someone ready to share the know-how.

---

### Post by darkod on 2011-12-07
No problem, glad you sorted it out. Please mark the thread as SOLVED, you can do that in thread tools above the first post.

---

