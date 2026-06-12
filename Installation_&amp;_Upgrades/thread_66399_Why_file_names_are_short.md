---
title: "Why file names are short??"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by janko on 2005-09-17
Hi all, yesterday i installed ubuntu 5.04 and i had some problems recompiling some drivers. I think the problem is because all filenames are short, something like: "eciads~1".
My question is: this problem is caused by ubuntu, or maybe it's the GNU desktop enviroment or it is more probably the file sistem i used (I've used raiser journaling fs)? What should i do? format (it wouldn't be a big problem, my pc is empty)? Or there's something else I can do?
Thanks,

Janko

---

### Post by raven on 2005-09-17
[QUOTE=janko]Hi all, yesterday i installed ubuntu 5.04 and i had some problems recompiling some drivers. I think the problem is because all filenames are short, something like: "eciads~1".
My question is: this problem is caused by ubuntu, or maybe it's the GNU desktop enviroment or it is more probably the file sistem i used (I've used raiser journaling fs)? What should i do? format (it wouldn't be a big problem, my pc is empty)? Or there's something else I can do?
Thanks,

Janko[/QUOTE]

I have reiserfs, I did not have any problem, for these files "eciads~1" I am not sure but if you opened this file with a text editor example KATE, it will save the original file with the extension "~" now the 1 in "eciads~1" as you mentioned you said "something like that" so I took it as without the 1 in the end and maybe you made a mistake, if this is the case you can delete this files, if it is not the case, as you mentioned just format, and be carefull about the steps you do, so you don't end up in the same situation........

---

### Post by janko on 2005-09-17
[QUOTE=raven]I am not sure but if you opened this file with a text editor example KATE, it will save the original file with the extension "~" now the 1 in "eciads~1" as you mentioned you said "something like that" so I took it as without the 1 in the end and maybe you made a mistake[/QUOTE]

No the 1 at the end it's not a mistake, it's like with the old dos short file names, I mean my file's real name is eciadsl-driver-0.1-beta  but the sistem it converts to eciads~1. So if i had a file called eciadsl-driver-0.1-gamma it would be converted in eciads~2. This is the reason I asked if the problem may be the filesystem or if it is normal for GNU (I'm a totally GNUwbie :) )

Janko

---

### Post by janko on 2005-09-17
I still don't know whi files do that, but i've understood that it wasn't a problem of the filesystem neither of the gnu, it was a problem of the floppy... which i used to "transport" files from windows to linux... i hope this can be usefull to someone

Janko

---

