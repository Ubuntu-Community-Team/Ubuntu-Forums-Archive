---
title: "untar lots of tar.gz files"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by Jason-X on 2005-04-01
Hi all,

I've downloaded a tar.gz folder full of themes for Gkrellm. I basically untarred(?) it into my /gkrellm/themes directory. The only problem is that all the themes inside the folder are also tar.gz files.

Is there a command that will untar all of the files in one hit as there is an awfull lot of tar.gz files in the directory and it will take me forever to do  them one at a time?

I hope there is!

Thanks in advance

Jason :)

---

### Post by bnutting on 2005-04-01
[QUOTE=Jason-X]Hi all,

I've downloaded a tar.gz folder full of themes for Gkrellm. I basically untarred(?) it into my /gkrellm/themes directory. The only problem is that all the themes inside the folder are also tar.gz files.

Is there a command that will untar all of the files in one hit as there is an awfull lot of tar.gz files in the directory and it will take me forever to do  them one at a time?

I hope there is!

Thanks in advance

Jason :)[/QUOTE]
If you are in the directory that contains the tar.gz files, type this:
```
for i in *; do echo working on $i; tar xvzf $i ; done
```
This should do what you want.

---

### Post by dusu on 2005-04-01
[QUOTE=bnutting]If you are in the directory that contains the tar.gz files, type this:
```
for i in *; do echo working on $i; tar xvzf $i ; done
```
This should do what you want.[/QUOTE]

Nice piece of shell code :)
I would also recommend to replace the * by *.tar.gz, ie
```
for i in *.tar.gz; do echo working on $i; tar xvzf $i ; done
```

---

### Post by Jason-X on 2005-04-01
Thanks to both of you. It did the trick and saved me loads of time.

Very nice shell code! I'll be noting this one down. :) 

Cheers Jason

---

### Post by bnutting on 2005-04-13
Glad I could help :grin:

---

### Post by jgni on 2008-07-22
> **bnutting said:**
> Glad I could help :grin:

And now, more than 3 years later, it still works.

Never happend on Winsnoews!! :lolflag:

---

