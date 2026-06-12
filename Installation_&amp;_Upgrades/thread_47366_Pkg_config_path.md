---
title: "Pkg_config_path ?"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by karmah on 2005-07-08
```

checking for pkg-config... /usr/bin/pkg-config
checking for libwnck-1.0 >= 2.9.92... Package libwnck-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libwnck-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libwnck-1.0' found
checking for gtk+-2.0
		libwnck-1.0 >= 0.17
		libxml-2.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0
		libwnck-1.0 >= 0.17
		libxml-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```
That's what happens when I try to install Devilspie! I've located the libwnck and the libxms and set the PKG_CONFIG_PATH to their directory and exported the variable, but it still says the same thing and I can't find out why, im kindof a noob so i might need much help :D.
Thx in advance!

---

### Post by karmah on 2005-07-08
Same thing happened when i tried to install some other applications too..

---

