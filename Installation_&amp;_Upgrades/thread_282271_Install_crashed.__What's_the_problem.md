---
title: "Install crashed.  What's the problem?"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by Jimmyqwy on 2006-10-22
When I install ubuntu 6.06, there happens a problem during the installation.  Install crashed! :( 

The error is:

Traceback (most recent call last):
file "/usr/bin/ubiquity",line 130,in ?
install(sys.argv[1])
file "/usr/bin/ubiquity",line 55 install
ret = wizard.run()
file"/usr/lib/python2.4/site=packages/ubiquity/frontend/gtkui.py",line 264,in \
run
self.progress_loop()
file"/usr/lib/python2.4/site=packages/ubiquity/frontend/gtkui.py".line 538,in \
progress_loop
raise RuntimeError,("install failed with exit code %s;see")
RuntimeError:install failed with exit code 1;see/var/log/installer/syslog and \
/var/log/syslog

Can anyone help me ? Many thanks!

---

### Post by Jimmyqwy on 2006-10-22
Could anyone help me?:confused: 
](*,)

---

### Post by unisol on 2006-10-23
check the cds integrity for errors if there are no errors try safe-graphics mode and do a text-mode install. what are your system specs?

---

