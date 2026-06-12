---
title: "Download during installation aborted"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Michi86 on 2010-10-11
Hello!
 
I installed Ubuntu 10.10 32bit on my Vaio VGN-NS21Z. It is working fine but I have a question concerning the insallation process.
 
I chose the option "Download updates while installing" and "Install this third-party software" at the beginning of the installation.
 
The installation was without problems but unfortunately the server providing the updates was very slow so I pressed the button "Skip" during the download of a large package in the installation process.
 
 
After the installation I changed the server for software updates and searched. It found 2 minor updates.
 
Now I have the feeling that there is a package missing because of the abort in the installation process.
 
Can you help me?

---

### Post by Michi86 on 2010-10-11
?

---

### Post by Michi86 on 2010-10-11
Is the third-party software downloaded or on the Ubuntu CD?

---

### Post by Michi86 on 2010-10-11
:-(

---

### Post by sikander3786 on 2010-10-11
I am sure the third party software you skipped should be the Ubuntu Restricted Extas that contain audio/video codecs, flash, java, fonts etc. You can install them by typing

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

from the terminal or by searching Ubuntu Restricted Extras in Software Center.

You can install the skipped updates by (which you've already done I think),

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by Michi86 on 2010-10-11
It is called Fluendo MP3 plugin.
 
Why is there anyway this option at the beginning of the installation process?
Is this software so important?

---

### Post by sikander3786 on 2010-10-11
> **Michi86 said:**
> It is called Fluendo MP3 plugin.
 
Why is there anyway this option at the beginning of the installation process?
Is this software so important?
It was not present in the pre Maverick installers. They just added it up for the new comers so that "Everything works out of the box".

---

