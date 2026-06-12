---
title: "Belkin wireless wont run"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by lorikeet88 on 2010-12-01
I've got an old Compaq nx6120, which I've converted to Maverick Meerkat after a virus ate Windows 7. Everything is going fine except for installing the wireless. I'm using a Belkin F5D8053 v6 adapter, and it wont accept the install disk. I've got Wine, and tried to install it via ndiswrapper, but the computer wouldn't accept commands into the terminal.
HELP!

---

### Post by Hippytaff on 2010-12-01
Hi and welcome :-)
Before we dig deeper what is the output of
```

rfkill

```

if there are any 'yes' to blocks, then do
```

rfkill unblock all

```

if this doesn't work can you post the output of
```

iwconfig

```
```

lshw -C network

```
```

lsmod | grep F5

```
:-D

---

### Post by lorikeet88 on 2010-12-01
When I try to install it from the disk, through wine, it insists the file is not marked as executable. is there any way around this?

---

### Post by Hippytaff on 2010-12-01
you can try changing the properties of the file, but you will have to copy it to a folder. As you know cd's are read only.
Lets say you copy it to you home folder. In a terminal do
```

chmod +x filename

```
or right click on the file and click the box to make it executable :-)

---

### Post by lorikeet88 on 2010-12-01
Got it :) Thank so much!

---

### Post by Hippytaff on 2010-12-01
No problem...glad to be of service :-)

Remember to mark the thread as solved in the thread tools near the top of the page :-)

---

