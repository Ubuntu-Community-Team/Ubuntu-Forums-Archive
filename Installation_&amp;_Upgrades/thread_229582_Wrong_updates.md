---
title: "Wrong updates"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by paparucino on 2006-08-04
Hi guys,
I downloaded a daily build of Edgy Eft and I made the bootable CD. I don't remember exactly what I made but the final result is that every time I run update-manager I'm asked for update from the files in the CD.
How can I restore the previous and coherent data?
Actually I have Dapper 6.06 updated till this morning.

---

### Post by Jagot on 2006-08-04
You may need edit your sources.list.  Type the following command in terminal:

```
sudo gedit /etc/apt/sources.list
```

You may see some lines in there that refer to your CD-Rom.  Comment them out by adding a # before them.

---

### Post by paparucino on 2006-08-04
> **Jagot said:**
> You may need edit your sources.list.  Type the following command in terminal:

```
sudo gedit /etc/apt/sources.list
```

You may see some lines in there that refer to your CD-Rom.  Comment them out by adding a # before them.

What a stupid I am!!!!!! Bafh.... I need a cup of coffee. :-)
Thank you very much.

---

