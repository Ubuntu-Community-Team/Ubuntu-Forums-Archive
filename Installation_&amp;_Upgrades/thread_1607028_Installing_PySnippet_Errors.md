---
title: "Installing PySnippet Errors"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by extremelycool on 2010-10-27
Been looking for a small minimalist PySnippet manager.

I think pysnippet could do the business:

[http://sourceforge.net/projects/pysnippet/](http://sourceforge.net/projects/pysnippet/)

But getting errors on install and it didn't install to the main menu and if I try to add an application launcher linking to the .py that exectures the program it doesn't work.

Errors on installation:

error: /usr/local/bin/pysnippet.py: Operation not permitted

error: /usr/local/bin/pysnippet.py: Operation not permitted

Any ideas how to solve?

Anyone got a 64 deb?

---

### Post by ajy0852 on 2010-11-12
Hey, I just found this post. I've been using PySnippet for a month or so now and I really like it. Simple, not too many features, but it works great.

So here's what I did to make it work:
- download the package from Sourceforge
- extract it into your home folder somewhere (I have a ~/Applications directory for this kind of thing)

Now you have to run PySnippet from a folder that contains a pysnippet.xml file (one is provided for you). So in my setup:
```

cd ~/Applications/pysnippet-1.3
python pysnippet.py

```

In practice, I prefer to put my pysnippets.xml file in my Dropbox folder so it gets synced and backed up ;) . Plus, I like a more convenient way to launch PySnippet. So I have this script:
```

#!/bin/bash
cd ~/Dropbox/Resources &&
python /home/<myusername>/Applications/pysnippet-1.3/pysnippet.py

```
I have saved it as "snippets", made it executable, and put it in my path so I can launch it with that command.

Also:
- make sure you save before closing, it doesn't autosave
- I haven't bothered messing with syntax highlighting and I don't know how to add more modules for that. Not a big deal for me when I just need to copy/paste snippets
- When you open a snippet by clicking on it, it automatically copies it to the clipboard for you. I prefer it to be copied to the primary selection (so I can middle-click to paste). If you want this, open pysnippet.py and search for "SELECTION_CLIPBOARD" (match case, it only occurs once) and change it to "SELECTION_PRIMARY". It's around line 700.

---

