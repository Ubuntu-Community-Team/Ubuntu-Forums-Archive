---
title: "System Updates Changing My Screen Display"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by gerry-acton on 2015-06-30
I am a Ubuntu 14.4.2 LTS system user. I am very pleased with this operating system, except for one very annoying thing.
I have a HANNS.G HW173A display.When I install the system it works fine, but when I apply updates, it frequently corrupts the display.
The latest update has changed the screen display to unknown, and it is now difficult to read. Does any body else have this problem, and know how to fix it.

---

### Post by ajgreeny on 2015-06-30
What graphic card do you have?

Let's see the output of terminal command ```
lspci | grep -i vga
```

---

### Post by gerry-acton on 2015-07-01
Linux System Updates – Screen Display
 

 Graphics Intel® 915G x86/MMX/SSE2
 

 

 

 Command line interface  lspci | grep -i vga
 

 VGA compatible controller : Intel Corporation 82915G/GV/910Gl Integrated Graphics Controller (rev (04)

---

### Post by gerry-acton on 2015-07-04
Linux System Updates &#8211; Screen Display
 

 Graphics Intel® 915G x86/MMX/SSE2
 

 

 

 Command line interface  lspci | grep -i vga
 

 VGA compatible controller : Intel Corporation 82915G/GV/910Gl Integrated Graphics Controller (rev (04)

---

