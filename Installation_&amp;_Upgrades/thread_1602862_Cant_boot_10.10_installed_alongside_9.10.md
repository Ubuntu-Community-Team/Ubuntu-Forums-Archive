---
title: "Cant boot 10.10 installed alongside 9.10"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by lenubuser123 on 2010-10-22
Dear All,

I installed ubuntu 10.10 on my lenovo laptop but couldnt get into it. I was having ubuntu 9.10 and installed 10.10 alongside.  had Grub loader and all its entries still boot to my 9.10 installation. I could still see my 10.10 partition but dont know how to get 10.10 working. Any ideas?

-LenUbUser

---

### Post by sikander3786 on 2010-10-22
Did you choose not to install bootloader during installation of 10.10?

Boot into 9.10 and from terminal, run

```
sudo update-grub
```

If the output lists Ubuntu 10.10, you are good to go. If it doesn't, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap the output with proper code # tags.

---

### Post by Rubi1200 on 2010-10-22
Hi and welcome to the forums lenubuser123 :)

Follow the advice posted by sikander3786 and we will try and help you resolve this issue.

---

