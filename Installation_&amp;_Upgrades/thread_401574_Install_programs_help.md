---
title: "Install programs help"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by quentinludwig on 2007-04-04
Every time I go to add or remove applications and try to get anything it says I can't download or install it.  Here's the message I get.

 cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

What does this mean?  How can I fix it?

Thank you.<br /><br />
----------------------------------------<br />

----------------------------------------<br /><br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by taurus on 2007-04-04
What are you trying to install?  Try running it from a terminal to see what the error message is.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install **program_name**
```

---

