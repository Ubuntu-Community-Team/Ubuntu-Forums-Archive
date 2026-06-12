---
title: "Where did on xorg.conf go?..."
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by beastrace91 on 2009-10-14
Hey There,

So I have a fresh install of Karmic 32bit on my Asus Netbook and I went to view my xorg.conf file as a reference for another thread I was helping someone with and was slightly confused to discover I do not have one... At least not any where I can find - it should be located in /etc/X11/xorg.conf? Right?

I also used nautilus to search my / directory for it and it came up blank... Does Karmic use a newer version of Xorg that no longer uses the xorg.conf to control settings? And if so where do I go to view/edit settings now?

Thanks,
~Jeff

---

### Post by novafluxx on 2009-10-14
Try doing:

ls -A

---

### Post by LKjell on 2009-10-14
Karmic does not have that file. If you need to modify something you can make a new one.

---

### Post by philinux on 2009-10-14
I have one as I installed the nvidia driver so the system creates one in this case. Others like the OP may not have one.

---

### Post by beastrace91 on 2009-10-14
> **LKjell said:**
> Karmic does not have that file. If you need to modify something you can make a new one.

Ahh alrighty - just wanted to make sure it still used the file before I went ahead and did that.

~Jeff

---

### Post by tekstr1der on 2009-10-14
Try searching the forums before posting? I've gone ahead and done this for you:

[http://ubuntuforums.org/search.php?searchid=65331932](http://ubuntuforums.org/search.php?searchid=65331932)

Please note many threads of the same exact question. Your answer lies within.

---

### Post by ranch hand on 2009-10-14
Some of us had one because of a previous in stall or from doing something that caused it to be created.  Some of those who had one (me for one) had to go in frim some where else and remove the bugger wo that we could boot.

If you have an ATI card I would leave it as it is.

---

