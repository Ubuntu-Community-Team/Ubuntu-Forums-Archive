---
title: "crossover office menu error in 11.04, Unity"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by tmillic on 2011-04-24
Hello.
At the end of installing crossover pro 9.1, I was provided the following message: 
```
cxmenu:error: unable to parse '/etc/xdg/menus/unity-place-applications.menu': Invalid string in comment field [Ln: 157, Col: 8]

```

I opened unity-place-applications.menu and looked at that line. Starting with line 155:
```
  <!-- System Tools-->
  <!-- Note: Software Center uses an OnlyUnallocated clause to generate
    --       the System section. We can't do that because we have the All Apps
    --       section. Let's cross fingers and hope we match somewhat
    -->

```
I'm guessing that the comment lines that start with just "--" are generating the error. 
Does anyone know what the section is and what it should look like for the crossover menu items, such as installing windows software?
Thanks,
-tom

---

### Post by djroot2 on 2011-06-03
I know this is over a month old but just to let others know... you can open unity-place-applications.menu and just make that comment into:
```
<!-- Note: Software Center uses an OnlyUnallocated clause to generate the System section. We can't do that because we have the All Apps section. Let's cross fingers and hope we match somewhat -->
```  *note that is just one long line.

---

