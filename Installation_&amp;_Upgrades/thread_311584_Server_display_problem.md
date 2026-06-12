---
title: "Server display problem"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by garybarwick on 2006-12-03
I have just installed 6.06 server, and all went well. However, when I login I can't see the post-login prompt - it is too low down and off the screen. If I press enter a few times things come into view.

I can't see the line that I am typing, I can only see it once I press enter.

I have tried every monitor adjustment available to no avail.

Is there some way of changing the number of lines that UBUNTU thinks my monitor has.

I am new to Linux, (and not likely to get very far until I sort this one)

Thanks for any help

Gary Barwick

---

### Post by dcstar on 2006-12-04
> **garybarwick said:**
> I have just installed 6.06 server, and all went well. However, when I login I can't see the post-login prompt - it is too low down and off the screen. If I press enter a few times things come into view.

I can't see the line that I am typing, I can only see it once I press enter.

I have tried every monitor adjustment available to no avail.

Is there some way of changing the number of lines that UBUNTU thinks my monitor has.

I am new to Linux, (and not likely to get very far until I sort this one)

Thanks for any help

Gary Barwick

Your best bet may be to edit your Grub boot string for the kernel and use a "vga=xxx" modifier to set the display mode to something other than default.

You may have to do a search to find some detailed info on this.

---

