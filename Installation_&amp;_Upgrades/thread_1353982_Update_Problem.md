---
title: "Update Problem"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by slotto on 2009-12-13
Hi,
I'm a new Ubuntu User. I migrated from Windows about 1 month ago.
Last week during an update, it hung up and the update couldn't complete. I got an error message, so I came here. I saw a similar problem another user was having so I followed their fix. It was to open terminal window and type something like... sodo rm * in some directory. I did that and my problem went away. Since then I couldn't get any uptates.
Today I get this message "Could not download all repository indexes" "Lists directory /var/lib/apt/lists partial is missing."

If someone could help, I would surely appreciate it.
Thanks,
Steve

---

### Post by Soul-Sing on 2009-12-13
```
sudo mkdir -p /var/lib/apt/lists/partial
```

---

### Post by slakkie on 2009-12-13
```

mkdir -p /var/cache/apt /var/cache/apt/apt-file /var/cache/apt/archives /var/cache/apt/archives/partial /var/cache/apt/partial

```

All the dirs you would need.

---

### Post by slotto on 2009-12-13
This worked. Thanks leoquant.

slakkie, I get this...
mkdir: cannot create directory `/var/cache/apt/apt-file': Permission denied
mkdir: cannot create directory `/var/cache/apt/partial': Permission denied

---

### Post by slakkie on 2009-12-13
> **slotto said:**
> This worked. Thanks leoquant.

slakkie, I get this...
mkdir: cannot create directory `/var/cache/apt/apt-file': Permission denied
mkdir: cannot create directory `/var/cache/apt/partial': Permission denied

sorry, you need to be root to do that, sudo mkdir -p <directories>

---

### Post by slotto on 2009-12-13
These directories are now created.
Thanks, Slakkie!

Steve

---

