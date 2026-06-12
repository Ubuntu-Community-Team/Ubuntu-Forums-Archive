---
title: "Updated and now I get &quot;An error occurred while mounting /home&quot;"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by sagi456 on 2010-10-02
I am new to Linux and Ubuntu, I have Lucid Lynx only for about 2 weeks now, so please go easy on me ;)

Exactly as the name of the thread suggests, I have used the update  manager. Now I get an additional option (as default - 2.6.32-25) in my grub menu, I guess it is the newer kernel?

When I just let it run I get an error message: "An error occurred while mounting /home" with 2 options, "Press S to skip or M for manual recovery".

I currently simply choose the previous kernel in the grub menu every time but it's a real pain.. Does anyone know how to resolve this issue? I've searched the formus and found nothing relevant yet...

---

### Post by oldfred on 2010-10-03
I would think the error would be something from fstab, but then should occur with both kernels.

Post this, so we can see entire configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by sagi456 on 2010-10-10
Ok found the source to my problem:

Antivirus was installed (Avira) and it blocked the new kernel from accessing my home folder!

Simply uninstalled it and everything went back to normal!


Thanks for the reply anyway!

---

