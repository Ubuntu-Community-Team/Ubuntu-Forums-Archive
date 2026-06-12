---
title: "Solarized color name not defined"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by dzy on 2013-06-02
Hi! 

I recently installed the Solarized theme for gnome-terminal in Ubuntu 12.04, but now, every time I used vim, I receive the warning "Warning: Color name "S_base03" is not defined". This warning is printed whether or not I am using the solarized colorscheme for vim. Otherwise, everything else seems normal. Any clue why I might be getting this error?


Thanks!

(I previously posted this question on AskUbuntu as well, but there were no replies. Hope re-posting here is not a problem?)

---

### Post by zealotds on 2014-03-22
Same problem, no idea. Although I have removed all the solorized color definitions in my XTerm / .Xdefaults...

---

### Post by vasa1 on 2014-03-22
> **dzy said:**
> ... the Solarized theme for gnome-terminal in Ubuntu 12.04, but now, every time I used vim, I receive the warning "Warning: Color name "S_base03" is not defined". ...
Could you post a part of the theme with a little before and after so that we can see where "S_base03" occurs and the context?

I'm using a Solarized theme as well, but for Geany, FWIW, and that doesn't have "S_base03", just "base03":```

[theme_info]
name=Solarized (dark)
description=Dark Solarized theme for Geany
version=1.22.0
author=Ethan Schoonover
url=http://ethanschoonover.com/solarized

[named_colors]
# See: http://ethanschoonover.com/solarized#the-values
base03=#002b36
base02=#073642
base01=#586e75
base00=#657b83
base0=#839496
base1=#93a1a1
base2=#eee8d5
base3=#fdf6e3
yellow=#b58900
orange=#cb4b16
red=#dc322f
magenta=#d33682
violet=#6c71c4
blue=#268bd2
cyan=#2aa198
green=#859900

[named_styles]
...
```

---

