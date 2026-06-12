---
title: "/boot not large enough for update to kernel 3.5.0"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by francesco44 on 2013-04-11
The last updates for kernel 3.5 are declared impossible because the boot partition seems to be not large enough, and an automatic message ask to free 326Kb in the boot partition. This is surprising as I did some month ago a standard install with an automatic definition of the different partitions. 

I have no dual boot and the "sudo apt-get clean" do not seem to do the job. It is always difficult to tweak the boot partition...Has anybody encountered the problem and found a solution?

---

### Post by mikewhatever on 2013-04-11
Can you list the contents of the boot partition - **ls /boot**. In case there are multiple kernels, consider removeing some.
You can remove both kernels and headers as described here [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/).

---

### Post by francesco44 on 2013-04-11
OK your indications where fine....

The tutorial 

[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/) 

seems to me better than the other which wrap-up all the procedures in one command and can result in errors...

.removing the old kernels one by one seems a more secure solution

---

### Post by mikewhatever on 2013-04-11
IMHO, removing multiple files one by one can result in errors (human errors!), not to mention how tedious it is.

---

