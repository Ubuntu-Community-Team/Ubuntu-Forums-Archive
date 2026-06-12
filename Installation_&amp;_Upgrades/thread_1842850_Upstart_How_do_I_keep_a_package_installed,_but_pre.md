---
title: "Upstart: How do I keep a package installed, but prevent it from running via Upstart?"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by IndieRockSteve on 2011-09-12
I have some programs installed but I wish to prevent them from running at system boot via Upstart AND to not revert back to this state after each upgrade.

I know how to accomplish the first part by editing the Upstart conf for that program, but when I upgrade that file gets overwritten. Is there a file somewhere I can edit that will accomplish the same "blacklisting" of a program without having to edit the original conf file?

thanks!

---

### Post by sisco311 on 2011-09-12
In Natty you can use an .override file: [http://upstart.ubuntu.com/cookbook/#override-files](http://upstart.ubuntu.com/cookbook/#override-files)

```
echo 'manual' | sudo tee /etc/init/job-name.override
```

Unfortunately this doesn't work in earlier releases.

---

