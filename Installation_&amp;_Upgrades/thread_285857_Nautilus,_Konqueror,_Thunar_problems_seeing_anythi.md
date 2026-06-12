---
title: "Nautilus, Konqueror, Thunar problems seeing anything beyond my home dir"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by DigitalDuality on 2006-10-27
let me add another really odd problem.

Nautilus, Konqueror, Thunar, it doesn't matter.  Each file browser can ONLY see my home directory.. and a dictory right above it "/"  but it's not the root directory.  All the directory displays is my home folder and a media folder to access my usb disk, cd-roms, etc.   this is both as root (gksudo) and as a normal user.  I can't see /etc /var /usr, nothing.

in the command line i can access everything.  ?

---

### Post by noripcord7 on 2006-10-27
View:Show Hidden Files works in Konqueror, but I agree that files and folders with which I have "read" permissions should appear by default in my file browser.

I guess the argument could be made that things are less confusing for new users this way, but I think it's more confusing for new and experienced users alike to ignore useful information by default and require a command line approach for simple, visiual tasks.

---

### Post by noripcord7 on 2006-10-27
What's more amusing, I think, is that files and folders within the root directory's folders are not hidden, only the top level directories themselves. I take back what I said, I disagree with any argument that states that this is a good policy (until someone smarter than me proves me wrong).

---

### Post by jneno on 2006-10-28
This is just plain dumb. I will not be upgrading beyond 6.06 as long as this is the case. Frankly I'm considering moving to another distro for the first time in over a year. 

Assuming there is an argument for these broad restrictions on GUI browsing of the file system (in my opionion there is not), it should at least be a configurable option. Can you imagine the uproar if Microsoft restricted directory browsing in explorer to 'My Documents' and similar folders?

There is a line between making a system more less intimidating and crippling it. Ubuntu just took a flying leap over that line.

---

### Post by AlterEgo on 2006-10-28
No worries :D 
Look for a file named .hidden in / and delete it.

---

### Post by noripcord7 on 2006-10-28
Ah, there it is. Thanks AlterEgo.

---

### Post by SirPecanGum on 2006-11-02
Nice 1! Thank you.

---

