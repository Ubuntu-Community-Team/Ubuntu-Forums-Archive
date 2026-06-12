---
title: "&quot;safe&quot; uninstall"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by chejose on 2008-06-26
I have a HP laptop that came with Vista installed, but since I did not want to run Vista I put Ubuntu "on top". A couple of things function in Vista that I couldn't make work in Ubuntu.

But... I want to sell this laptop. I am getting a new laptop and I want to sell this one with only the original Vista installation. The problem is that in the area where I live "linux" is still not accepted and selling it dual boot would be much more difficult.

So the question: How can I remove Ubuntu and leave only the original Vista installation?

Thanks,

José

---

### Post by Pumalite on 2008-06-26
Delete everything in the hard drive and format ntfs. Then install Windows.
Use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn to disk the iso and boot from it.

---

### Post by chejose on 2008-06-26
OK... thanks. [I] shudder a bit at formating the whole HD, but if there is no alternative.

The problem isn't formating, but handling Vista leaves me uncomfortable. So will try later and see.

Thankks,  José[/I]

---

### Post by Pumalite on 2008-06-26
Don't worry. It will work fine. Windows needs a primary partition, prefers sda1 and usually loves the whole drive. If you later want to dual boot; use the Vista partitioner to allocate space for Ubuntu. Good luck.

---

