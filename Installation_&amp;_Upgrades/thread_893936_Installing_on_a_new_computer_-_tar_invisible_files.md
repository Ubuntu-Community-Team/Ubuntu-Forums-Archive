---
title: "Installing on a new computer - tar invisible files"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by confusa on 2008-08-18
Just installed the newest release on another computer and want to copy all the . files from my home directory to home on my new computer. I could not figure out the tar command to do only that. Any hints?

Also, is it safe to do this?

---

### Post by spin2cool on 2008-08-18
Yes, for the most part it's safe.  I usually stay away from the '.gnome*' folders and a few of the others that are more core OS than app-specific.  If you're unsure, make a backup of your current home directory first, so that you can restore it if something goes wrong (and then be more selective when copying config information the second time)

You can use something like this to give you a list of all the files in your home directory:

```
ls -a | perl -pe 's/\n/ /g' | less
```

Just edit the list to remove what you don't want (such as '.' and '..'), then plug the list into your tar command:

```
tar -czvf home.tar.gz <list>
```

alternately, zip everything up individually and copy them one by one:

```
ls -a | while read line;do echo tar -czvf $line.tar.gz $line;done
```

---

