---
title: "Gutsy - remove Compiz install Beryl"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by analyzer123 on 2007-12-03
Hello all,
        I had ubuntu Feisty on my dell E1405 (intel integrated graphics) laptop before. I was running beryl with all the effects and it ran very smooth and fast.
 
I 'upgraded' to Gutsy and find that the defualt Compiz is too slow. Is there a clean way to remove compiz and install beryl? I cant even find beryl in the repos.

Or how do i speed up compiz in my dell e1405 lappy? Somehow the 3d effects are too slow compared to beryl? some 3d acceleration problem?

Thanks,

---

### Post by Vadi on 2007-12-03
There's no going back to beryl, the project is discontinued and was merged with Compiz.

Try installing the compiz settings manager ([click]("apt:compizconfig-settings-manager")), then go to general options. In there, there should be an option to set the rendering to be 'fast'.

Also look into reducing transparencies, those are really power-hungry.

---

