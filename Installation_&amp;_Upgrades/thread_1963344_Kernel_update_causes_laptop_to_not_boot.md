---
title: "Kernel update causes laptop to not boot"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by l0uismustdie on 2012-04-22
Hello, I am running Ubuntu 10.04 on an hp laptop. I recently did a kernel update to 2.6.32-39-generic and am now no longer able to boot the laptop. I have tried booting from the past two versions: 2.6.32-38-generic and 2.6.32-37-generic and this still doesn't work. When the machine is booting these messages are printed before it hangs indefinitely:
```

/etc/rc.local: 1: 1: not found
/etc/rc.local: 1: 2305: not found
/etc/rc.local: 1: 0c#!/bin/sh: not found

```

I'm not really sure where to start with this. Any help would be much appreciated. Thanks.

---

### Post by SeijiSensei on 2012-04-22
Looks like the file /etc/rc.local got corrupted somehow.  Boot into a "recovery mode" kernel and choose the "root shell" option when it is presented.  Then run these commands:
```
cd /etc
mv rc.local rc.local.bad
touch rc.local
chmod 755 rc.local

```
then reboot.

rc.local is the last script that runs at boot.  Usually it's a catch-all to start servers or run other commands that you require during the boot process.  If you never edited it yourself, it should look like this:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```
If you made changes to the original rc.local, examine rc.local.bad to see what went wrong.

---

### Post by l0uismustdie on 2012-04-26
Right. Thanks for the reply. I've gone through the process you described but am still having some issues. For starters I will mention that I have an external USB hard drive set up to mount automatically. So, naturally I've tried unplugging this and booting without it. If I try this the boot screen hangs on 'Checking battery state'. If I plug the drive back in i get a series of message like 
```

[ 145.360153] hub3-0:1.0: unable to enumerate USB device on port 1
[ 145.504123] usb 1-1.2: device descriptor read/64, error -32

```

And then it hangs here. Any ideas about this?

---

### Post by l0uismustdie on 2012-05-02
Just though I might give this a bump.

---

