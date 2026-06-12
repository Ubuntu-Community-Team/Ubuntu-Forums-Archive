---
title: "ubuntu studio 16.04 Broken Count&gt;0"
date: 2017-04-08
forum: Installation &amp; Upgrades
---

### Post by beriko on 2017-04-08
Who can help me?

Application manager doesn't work. I can't upgrade my OS. 

sudo apt get install f

what is mean?

Thank you

---

### Post by ubfan1 on 2017-04-08
The command appears to be missing two "-"s.  It should be
sudo apt-get install -f

---

### Post by RobGoss on 2017-04-08
If you're trying to upgrade your system are you using the correct command line?

Try this

```
 sudo apt-get update
```

---

### Post by Frogs Hair on 2017-04-11
> [COLOR=#000000]sudo apt get install f[/COLOR]

[COLOR=#000000]what is mean?[/COLOR]

This is a fix installation command and the complete command follows.

```
sudo apt-get install -f
```

Are you being prompted to run this command?

---

