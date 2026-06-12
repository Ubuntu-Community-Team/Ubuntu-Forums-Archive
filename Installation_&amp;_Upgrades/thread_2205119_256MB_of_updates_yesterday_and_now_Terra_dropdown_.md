---
title: "256MB of updates yesterday and now Terra dropdown terminal stop working"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2014-02-12
any suggestions   [always worked like a dream so i think it must be related to updates from software updater but i could be wrong here]
[http://ubuntuhandbook.org/index.php/tag/terra-terminal-emulator/](http://ubuntuhandbook.org/index.php/tag/terra-terminal-emulator/)

```
 terraFontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 14: out of memory
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 23: out of memory
Fontconfig error: "/etc/fonts/conf.d/65-khmer.conf", line 32: out of memory
Traceback (most recent call last):
  File "/usr/bin/terra", line 27, in <module>
    terminal.main()
  File "/usr/lib/python2.7/dist-packages/terra/terminal.py", line 499, in main
    app = TerminalWin()
  File "/usr/lib/python2.7/dist-packages/terra/terminal.py", line 52, in __init__
    self.init_ui()
  File "/usr/lib/python2.7/dist-packages/terra/terminal.py", line 111, in init_ui
    self.add_page(page_name=tab_name)
  File "/usr/lib/python2.7/dist-packages/terra/terminal.py", line 178, in add_page
    self.notebook.append_page(VteObjectContainer(), None)
  File "/usr/lib/python2.7/dist-packages/terra/VteObject.py", line 51, in __init__
    self.active_terminal = VteObject()
  File "/usr/lib/python2.7/dist-packages/terra/VteObject.py", line 100, in __init__
    self.update_ui()
  File "/usr/lib/python2.7/dist-packages/terra/VteObject.py", line 152, in update_ui
    self.vte.set_background_saturation(ConfigManager.get_conf('transparency') / 100.0)
AttributeError: 'Terminal' object has no attribute 'set_background_saturation'



```

---

### Post by Wako on 2014-03-24
Yes this is a bug in the code but there are no solution yet.

You can checkout the response from the developer here: 

[https://bugs.launchpad.net/terra/+bug/1229762](https://bugs.launchpad.net/terra/+bug/1229762)

---

