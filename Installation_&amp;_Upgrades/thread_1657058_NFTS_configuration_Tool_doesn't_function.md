---
title: "NFTS configuration Tool doesn't function"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by BKbroila on 2010-12-31
I tried installing NFTS Configuration Tool to auto-mount several partitions at startup, but the Configuration Tool isn't working.
I've entered the terminal line to update it, but it still won't even start.

What happens is when I click on NFTS Configuration Tool under System - Administration, I'll get the prompt to enter my Administrative password. I enter it and click Ok, but then it just disappears. 
If I try running the Tool again, I see a window come up at the bottom of my screen titled 'System Administrative' for about half a second then disappear. If I restart or suspend and try again, I still get the same nagging problem.

What have I done wrong?

---

### Post by ajgreeny on 2011-01-01
Try starting it in terminal with the command ```
gksu ntfs-config
```and you may get a helpful error message.

You also say "Administrative password" as if you have a different one to your user password.  Normally in the Ubuntu family the user password is used along with sudo or gksu for root permissions.

---

### Post by BKbroila on 2011-01-02
Oh, sorry for the confusion; I have the same password for everything like normal.

Well, after running your command in Terminal, I got the following: 
```

    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'

```

And I figured that the missing policy file was causing this shenanigans, so after googling it, I found the answer!

A simple install of hal did it for me. I have no idea what it does, but it works!
Thanks!

---

