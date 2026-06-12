---
title: "Permission denied error, can't run sage"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by Dushyant_Sapre on 2015-05-09
Hi,

 I've been using Ubuntu for a few months. I installed sagemath after extracting the tar file . In the terminal, when I go to the directory of sage and type " ./sage " , it says permission denied. I googled about and mostly found people saying use  'sudo'  before my command. When I do that it says command not found.Have a look-

---

### Post by steeldriver on 2015-05-09
Hello and welcome to the forums

There are a number of reasons why a supposedly executable file might not execute - let's start with the following information from the terminal

```

ls -ld sage

file sage

uname -a

```

---

### Post by ubfan1 on 2015-05-09
Also lets see what's in the sage directory, with just 
ls
from within that directory.
Also, please post the output from 
mount
for that partition.  Some subtle "can't execute" problems may result from mounting with the no execution flag.

---

### Post by Dushyant_Sapre on 2015-05-10
[ATTACH=CONFIG]261875[/ATTACH]
This is what I got.

---

### Post by steeldriver on 2015-05-10
The sage script should be executable by default when you unpacked the tar archive - I suspect that your issue is that /media is a non-Unix filesystem (such as a NTFS partition) without the necessary support for Linux permissions (see ubfan1's post above)

You could try running it as

```

bash sage

```

but really a better solution would be to unpack the archive to a more suitable location (somewhere in your regular /home/dsap29 directory for example)

---

### Post by Dushyant_Sapre on 2015-05-10
I reinstalled sage in the home/dsap29 directory and it worked. Thanks a lot!

---

