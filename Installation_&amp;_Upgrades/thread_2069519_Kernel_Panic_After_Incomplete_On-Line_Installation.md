---
title: "Kernel Panic After Incomplete On-Line Installation of 12.04"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by evanlong on 2012-10-11
I clicked the "Upgrade to 12.04" button in the upgrade manager, and the installation stalled at about 80% (2 hours to go), right in the middle of the machine installing some MS font-related files.  The two things I noticed from this point were that I had no options to stop or retry the upgrading process, and some of the windows I was using had no text in them, only vertical rectangle characters.

Upon restarting the computer, I got this:

[B]error: no module specified.
error: no suitable mode found.
error: unknown command 'terminal'.
[    1.205753] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[    1.205809] Pid: 1, comm: swapper/0 Not tainted 3.2.0-31 generic #50-Ubuntu
[    1.205853] Call Trace:
[    1.205902]  [<c155f691>] ? printk+0x2d/0x2f
[    1.205946]  [<c155f55f>] panic+0x5c/0x161
[    1.205992]  [<c1830b59>] mount_block_root+0xb9/0x14c
[    1.206040]  [<c1140dac>] ? sys_mknod+0x2c/0x30
[    1.206083]  [<c1830d64>] mount_root+0x59/0x5f
[    1.206127]  [<c1830eb8>] prepare_namespace+0x14e/0x192
[    1.206174]  [<c1131a05>] ? sys_access+0x25/0x30
[    1.206218]  [<c18308cd>] kernel_init+0x156/0x15b
[    1.206262]  [<c1830777>] ? start_kernel+0x353/0x353
[    1.206307]  [<c157befe>] kernel_thread_helper+0x6/0x10
[/B]
That's it, and a blinking cursor.  I can boot from a live CD; is there a way I can make the system fix the installation?

---

### Post by evanlong on 2012-10-11
This fixed it:

[http://ubuntuforums.org/showpost.php?p=9528669&postcount=41]("http://ubuntuforums.org/showpost.php?p=9528669&postcount=41")

---

