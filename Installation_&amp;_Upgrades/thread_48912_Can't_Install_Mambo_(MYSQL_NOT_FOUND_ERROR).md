---
title: "Can't Install Mambo (MYSQL NOT FOUND ERROR)"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by racket24 on 2005-07-14
I am a relative linux noob, so please bare with me. I am trying to install mambo 4.5.2.3 on my system. I have installed Apache2 and mysql server as well as php4. When I go to localhost/mambo it gives me the following information prior to installation:

PHP Version>= 4.1.0 Yes
-zlib compression support Available
-XML support - Available

-MYSQL support UNAVAILABLE
configuration.php UNWRITEABLE



further down, all my directory and file permissions, it says unwriteable. 

How do I fix this so I can finalize mambo installation. Please tell me if you need any more information to help. Thanks!

---

### Post by alastair on 2005-07-14
You say "When I go to localhost/mambo" ...

What configuration command is this? ./configure?

For MySQL, you probably need to install a "-dev" package to get the development headers/libraries.

As for permissions - "it says unwriteable". Are they? What files and what permissions? Who are you running the configuration/install as?

---

