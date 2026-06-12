---
title: "VMWare tools fix for Feisty"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by wrycatcher on 2007-04-24
from [http://www.vmware.com/community/thread.jspa?threadID=62836&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=62836&tstart=0):

```
- unpack vmtools into tmp. 
- mkidr /tmp/vmxnet 
- cd /tmp/vmxnet 
- tar xf /tmp/vmware-tools-distrib/lib/modules/source/vmxnet.tar 
- fix vmxnet.c 
- tar cf vmxnet.tar vmxnet-only 
- cp vmxnet.tar /tmp/vmware-tools/distrib/lib/modules/source/vmxnet.tar 
rerun the installation.
```

**NOTE**: When it says "fix vmxnet.c" that means go to line 1058 (in my version, anyway) and remove the last argument altogether, and save.  In my version, this line was causing a compiliation error.  In case your version shows it on a different line, here's the code (pre-update):  ```
vmxnet_interrupt(int irq, void *dev_id, NULL)
```

This worked for me perfectly for me for several "unsupported" Linux distro versions, including Feisty beta.  You should be able to accept all the default options, and then at the end of the install it will kick off the vmware-tools-config.pl.  This ends by spelling out a few commands you need to issue regarding networking.  **Make sure to do those otherwise your network devices won't work.**  

I also heard of another unrelated issue regarding the install script failing to create a directory upon installation and then aborting.  Something in /etc/init.d...This is either due to needing to run with 'sudo' prepended to the install script -OR- the script isn't getting invoked from the proper location.  It is important to navigate to the directory that contains the vmware-install.pl script and run it from there for the best results.  I managed to dodge an annoying bug in the install script by doing that.

---

### Post by stephenk on 2007-04-26
I tried this but "fix vmxnet.c" doesn't work - the fix command isn't found. How do I install this?

---

### Post by gvkwok on 2007-07-11
> **stephenk said:**
> I tried this but "fix vmxnet.c" doesn't work - the fix command isn't found. How do I install this?

Stephen, you are correct there's no "fix" command. What wrycatcher refer to the "fix" is that you have to edit the vmxnet.c file, browse to line 1058 and remove the last ", NULL" from the line. and repack the tar file and rerun the installation.

Original quote as below:

/*
NOTE: When it says "fix vmxnet.c" that means go to line 1058 (in my version, anyway) and remove the last argument altogether, and save. In my version, this line was causing a compiliation error. In case your version shows it on a different line, here's the code (pre-update):

vmxnet_interrupt(int irq, void *dev_id, NULL)

This worked for me perfectly for me for several "unsupported" Linux distro versions, including Feisty beta. You should be able to accept all the default options, and then at the end of the install it will kick off the vmware-tools-config.pl. This ends by spelling out a few commands you need to issue regarding networking. Make sure to do those otherwise your network devices won't work. 
*/

The above line would become 

vmxnet_interrupt(int irq, void *dev_id) 

BTW, wrycatcher, thanks for the fix... :guitar:

---

### Post by gvkwok on 2007-07-11
Stephen, leave a reply if you still can't get it work...

---

### Post by Mach1US on 2007-09-15
any idea how to reinstall or remove vmware tools running 7.04 on xp ?

---

### Post by Mach1US on 2007-10-02
Does anybody know how to enable drag and drop between host and guest ?
Is there any way to improve frame rates in vmware running feisty on Xp  ?
I have vmware tools running but it does not help , any ideas , at all ?

---

