---
title: "Setting +x attribute on non-linux partition is not possible in 10.10(but in 10.04...)"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by Vdragon on 2011-03-14
find same problem here!

[http://ubuntuforums.org/archive/index.php/t-1596666.html](http://ubuntuforums.org/archive/index.php/t-1596666.html)

I  think that something about mounting non-linux partition like FAT & NTFS has being changed from Lucid to  Maverick!

If you're a C/C++ programmer compile source file stored on a non-linux partition like FAT & NTFS.

The binary created successfully, but it will always leave a message "Permission denied" when you try to execute it.

Of course, you have write permission on that partition because you can edit any file on it.

When you tried to change the binary file's attribute (+x), it will always fail.

Something strange is this issue never happens in Lucid, but in Maverick!

Well, non-linux partition sure doesn't compatible with unix file attributes.

But it's quite nonsense to force people from converting  partition from other to Linux-based just because compiled binary can't  run a partition which does't have possibility for setting +x  attribute, isn't it?


-----------------------
Sorry for the poor language cause I'm not native speaker, though.

I spent all night install OS back to Lucid...

--------------------Update---------------------
I found that 
in lucid, ***every*** file in non-linux partition have x attribute, Including those exactly isn't executable
it's impossible to change the attribute.
However,
in Maverick, ***none*** of file have x attribute,
and it's impossible to change the attribute either...

What can I do if I want to execute files in Maverick?(And in that partition)

---------------SOLVED---------------------
unmount the partition and mount it with exec parameter

---

