---
title: "Script Safe equivalent for &quot;apt list --upgradable&quot;"
date: 2024-02-25
forum: Installation &amp; Upgrades
---

### Post by qupfer2 on 2024-02-25
If I run "apt list --upgradable" inside an script, I got: ```
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
```

man apt(8) says: 

```

All features of [apt]("https://manpages.ubuntu.com/manpages/jammy/man8/apt.8.html")(8) are available in dedicated APT tools like [apt-get]("https://manpages.ubuntu.com/manpages/jammy/man8/apt-get.8.html")(8) and [apt-]("https://manpages.ubuntu.com/manpages/jammy/man8/aptcache.8.html")[cache]("https://manpages.ubuntu.com/manpages/jammy/man8/aptcache.8.html")(8) as well.  
[apt]("https://manpages.ubuntu.com/manpages/jammy/man8/apt.8.html")(8) just changes the default value of some options (see [apt.conf]("https://manpages.ubuntu.com/manpages/jammy/man5/apt.conf.5.html")(5) and specifically the Binary scope).
So you should prefer using these commands (potentially with some additional options enabled) 
in your scripts as they keep backward compatibility as much as possible.
```

But I could not find a apt-get/apt-cache/dpkg-query/apt-... conmmand, that whould give me a list of upgradable packages. 
Can someone give me a hint, please?

As a workaround, I redirect stderr to /dev/null, but it sounds not like the "correct" solution.

---

