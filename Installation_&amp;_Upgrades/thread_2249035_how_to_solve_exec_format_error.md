---
title: "how to solve exec format error?"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by justforfun2 on 2014-10-19
run-init:/sbin/init/:Exec format error
&#65339;   1.440167] Kernal panic-not syncing :Attempted to kill init!
&#65339;   1.440205] Pid:1,comm:run-init Not tainted 3.2.0-70-generic-ape &#65283;105-Ubuntu
&#65339;   1.440241] Call Trace:
&#65339;   1.440281] &#65339;&#12296;c1598b6e&#12297;&#65341; ? printk+0x2d/0x2f
&#65339;   1.440317] &#65339;&#12296;c1598a3c&#12297;&#65341; panic+0x5c/0x161
&#65339;   1.440354] &#65339;&#12296;c105ec64&#12297;&#65341; forget_original_parent+0x1e4/0x1f0

---

### Post by ajgreeny on 2014-10-19
When do you see this problem?
Can you boot the system at all or is this during installation?

---

### Post by SeijiSensei on 2014-10-19
```
run-init:/sbin/init/:Exec format error
```
The trailing slash indicates a directory, not the file /sbin/init.  Since a directory is not executable, you get the format error. Is this something you created yourself?  I don't recall ever seeing this problem on a vanilla Ubuntu installation.  Just remove the trailing slash from wherever /sbin/init is invoked.

---

