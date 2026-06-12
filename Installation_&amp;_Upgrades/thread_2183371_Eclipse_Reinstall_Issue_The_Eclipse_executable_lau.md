---
title: "Eclipse Reinstall Issue: The Eclipse executable launcher was unable to locate its..."
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by orangeman555 on 2013-10-24
This has been an absolute nightmare for me. Perhaps I have a thing or two to learn.

Eclipse has been punishing me from day one. Its plugins never work properly, and I'm often led to reinstall. 

Now when I *remove* eclipse, it seems removed, but when I attempt to install it again, it **downloads instantly** (showing that its not *really* downloading, but rather just recognizing it must be there when its not). The progress bar zips straight to finished, and becomes "installed" 

When I launch it I get this: [B]"The Eclipse executable launcher was unable to locate its 
companion shared library."[/B]

---

### Post by msdin on 2013-10-24
Are you installing from the ubuntu repos (ie. the software center)? Honestly, for eclipse you are better off downloading it from eclipse.org and installing/running it from a folder in your home directory. Just make sure you have the java sdk installed (you can use the ubuntu repo for that). It won't mess up your system since it is self contained. Normally you should try to only install software from the ubuntu repos but eclipse is an exception.

---

### Post by orangeman555 on 2013-10-25
Thanks. After the agony I've been through with it I'm not surprised to hear that! Thanks then, I will go with that.

---

