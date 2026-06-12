---
title: "Installing New Kernel &amp; dkms"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by jason50146 on 2009-11-20
I'm having the problem posted about at this bug report: [https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606]("https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/292606")

The final fix appears to be a change to the dkms script descibed here: 

"Patching /etc/kernel/postinst.d/dkms to redirect stdout DOES FIX the problem.  Adding "1>&2" to the invocation of /etc/init.d/dkms_autoinstaller keeps stdout clean."

I've tried putting th "1>&2" in lots of places, but can't seem to hit the right spot.  Can somebody enlighten me as to where I should put the "1>&2" to fix the problem?  Should I reboot after making the change?

My dkms file is posted below.

```
#!/bin/bash

# We're passed the version of the kernel being installed
inst_kern=$1

if [ -x /etc/init.d/dkms_autoinstaller ]; then
    if which invoke-rc.d >/dev/null 2>&1 ; then
        invoke-rc.d dkms_autoinstaller start $inst_kern
    else
        /etc/init.d/dkms_autoinstaller start $inst_kern
    fi
fi
exit 0
```

---

### Post by eliazebe on 2009-11-21
have you found the position when add 1>&2 ??

I have your same problem...

---

### Post by jason50146 on 2009-11-27
I was never able to make it work by edititing the dkms script.  

I removed nvidia-common to make it work, as was described in the bug report.  I was able to install the new kernel after that.

---

