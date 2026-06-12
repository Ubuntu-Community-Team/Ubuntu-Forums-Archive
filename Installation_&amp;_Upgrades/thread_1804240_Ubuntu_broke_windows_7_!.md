---
title: "Ubuntu broke windows 7 !?"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by shftn2gear97 on 2011-07-14
I just installed ubuntu to dual boot with my windows 7 machine (compaq) succesfully!

Played around with ubuntu and everything works fine...

Found out i need to use internet explorer for training purposes (work)

but.. when i boot up windows 7 its pretty much a boot loop and never gets to the log on screen...wtf...

Please help/much appreciated 

Mike

---

### Post by Quackers on 2011-07-14
Welcome to UF :-)
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mark Phelps on 2011-07-15
> **shftn2gear97 said:**
> but.. when i boot up windows 7 its pretty much a boot loop and never gets to the log on screen...wtf...

Did you allow the Ubuntu installer to SHRINK the Win7 partition to make room for Ubuntu? Or did you install INSIDE Win7 using Wubi?

If you did the first, you've encountered the problem where GParted corrupts Win7 OS partitions, leaving them unbootable.  Unless you have a Win7 Install DVD, or had the foresight to make a Win7 Repair CD BEFORE you did the dual-boot setup, you're pretty-much hosed in Win7.

---

