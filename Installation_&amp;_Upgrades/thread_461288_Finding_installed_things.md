---
title: "Finding installed things"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by pardesi on 2007-06-01
i installed ubuntu 7.04 yesterday and updated it .in particular i downloaded python.now i am unable to find it:( also other downloaded items.please help

---

### Post by jamesjtucker on 2007-06-01
There are some search functions/programs that may work, but i like the command line for most stuff. 
do this:
sudo updatedb

then when that finishes, do a:
locate [insert file name or search string]

The first command updates the file information so you have a current index, the second looks for it. So assuming i have a file called Super_cool_ubuntuapp-4.6.0.2-awesome.sh that i need to look for, i could do a search on the whole file name, or parts like: locate Super*.sh or locate *awesome.sh or whatever you needed to find.

---

### Post by pardesi on 2007-06-01
so i should be writing sudo updatedb in the terminal. i did that but then nothing change d and after i wrote the locate command nothing happened. is ther any particular place where updated files/installed files go

---

### Post by Barticus on 2007-06-01
Try this;

"sudo find / -iname *python*"

You will likely get a bunch of hits, but you should probably see the package name in there somewhere.

B

---

### Post by pardesi on 2007-06-01
there are so many places to find after putting that command in the terminal when i found python in the bin it does not open at all on clicking.

---

