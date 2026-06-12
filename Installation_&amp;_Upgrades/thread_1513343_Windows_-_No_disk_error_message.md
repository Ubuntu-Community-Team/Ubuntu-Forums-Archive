---
title: "Windows - No disk error message"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by DrJMEvans on 2010-06-19
When trying to install ubuntu using wubi I get this error message no matter what I try:

Windows - No disk
Exception processing message c0000013.

Thanks for assistance.

Dr John Evans

---

### Post by DrJMEvans on 2010-06-20
In further research I discovered that this error is because wubi looks for all available drives, including card readers.

When I used "safely remove hardware" to remove the card readers, installation was able to proceed.

---

