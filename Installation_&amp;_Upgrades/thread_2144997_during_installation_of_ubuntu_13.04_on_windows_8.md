---
title: "during installation of ubuntu 13.04 on windows 8"
date: 2013-05-14
forum: Installation &amp; Upgrades
---

### Post by mounik on 2013-05-14
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {59a7630c-b8b3-11e2-b90c-d3fbf29a86ca} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.

can u tell me wat this error is about?

---

### Post by fantab on 2013-05-14
tell us what exactly you did?

---

### Post by mounik on 2013-05-14
i ran wubi thats all. i opened the iso using winrar and then i clicked on the wubi.exe

---

### Post by fantab on 2013-05-14
Wubi is not working on 13.04. Did you download 13.04 from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)? If you want WUBI then look here: [http://releases.ubuntu.com/raring/](http://releases.ubuntu.com/raring/), it should work but it was not included in the final release because it wasn't ready. Use at your own risk.

I don't know for sure, but I think you will have to turn off "Secure Boot" from BIOS to install WUBI...

As an alternative you can consider 'true' Dual-boot.

---

