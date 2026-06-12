---
title: "Disable CD/DVD Drive In Repo List via Command Line?"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by DasCrushinator on 2008-03-24
How would I go about doing this?  I am assuming 'sed' or 'awk'?  I am new to both of these commands and would appreciate any help!

---

### Post by dormant on 2008-03-24
It is easier doing it using the Synaptic Package Manager.

From the command line, you need to edit /etc/apt/sources.list.

Use your favourite editor to insert a "#" at the front of the line beginning with "deb cdrom"

---

### Post by DasCrushinator on 2008-03-24
> **dormant said:**
> It is easier doing it using the Synaptic Package Manager.

From the command line, you need to edit /etc/apt/sources.list.

Use your favourite editor to insert a "#" at the front of the line beginning with "deb cdrom"

Yes, I know this, but I am making an automated install script and would like it to do it in the script via command line.

---

### Post by DasCrushinator on 2008-03-25
Anyone?

---

### Post by c-ron on 2008-03-25
See below for the script that works.:)

---

### Post by DasCrushinator on 2008-03-25
Tried it and got ```
bash: sources.list: Permission denied
```

Edit: Just to avoid any confusion, I copied and pasted the command (did not type it out).

---

### Post by c-ron on 2008-03-25
Okay, this one works. Normally, I'm not a shell scripting kid of guy, so if anyone knows how to clean this up, please feel free.:

```

sed 's/deb cdrom/#deb cdrom/g' /etc/apt/sources.list >> ~/sources.new && sudo cp ~/sources.new /etc/apt/sources.list && rm ~/sources.new

```

Consecutive runs add hash marks '#' to the beginning of that line, so running it more than once would make it so that the CD-ROM does not show as a selectable option in other package managers like Synaptic.
Hope this helps.

---

### Post by DasCrushinator on 2008-03-26
> **c-ron said:**
> Okay, this one works. Normally, I'm not a shell scripting kid of guy, so if anyone knows how to clean this up, please feel free.:

```

sed 's/deb cdrom/#deb cdrom/g' /etc/apt/sources.list >> ~/sources.new && sudo cp ~/sources.new /etc/apt/sources.list && rm ~/sources.new

```

Consecutive runs add hash marks '#' to the beginning of that line, so running it more than once would make it so that the CD-ROM does not show as a selectable option in other package managers like Synaptic.
Hope this helps.

Thank ya kindly!

---

