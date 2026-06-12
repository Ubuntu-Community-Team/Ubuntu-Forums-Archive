---
title: "Moved Home, Advice Please"
date: 2006-04-28
forum: Installation &amp; Upgrades
---

### Post by Irony on 2006-04-28
I just performed this instruction to move my home folder from the root partition to its own partition;

[PHP]sudo cp -ax /mnt/hda3_Ubuntu/home/irony /mnt/hda7_Home/irony[/PHP]

I did this by booting into another Ubuntu I have installed on hda5.

This seems to have worked fine as I am now booted into hda3.

However if I had several users would I instead do;

[PHP]sudo cp -ax /mnt/hda3_Ubuntu/home /mnt/hda7_Home/home/[/PHP]

I'm not sure of how / is treated, in other words by putting home/ would this copy the contents of home to hda5 but not create the folder home (otherwise it would be home/home/irony)?

---

### Post by Irony on 2006-04-28
It occurred to me I could test the cp -a function by doing so on a local folder but putting after the folder name doesn't copy the contents only.

How do I copy the contents of say folder A into folder B without folder B becoming folder B with A folder inside it - what is the terminal command?

---

### Post by Irony on 2006-04-28
What I should have done is;

*sudo cp -ax /mnt/hda3_Ubuntu/home/* /mnt/hda7_Home*

As it happens I am the only user so the following command worked, but the above command would have done the same thing but also have copied any extra users;

*sudo cp -ax /mnt/hda3_Ubuntu/home/irony /mnt/hda7_Home/irony*

php command doesn't work with * hence italics.

The * copies the contents of the folder not the folder itself.

---

