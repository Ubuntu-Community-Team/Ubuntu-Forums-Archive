---
title: "[SOLVED] Java SDK and libstdc++.so.5 question"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by animefan82 on 2008-05-24
ran chmod +x java_ee....
---
$ ./java_ee_sdk-5_05-linux.bin 
./java_ee_sdk-5_05-linux.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
---
gcc has been installed, but still no go.

And on a side note, I ran chmod both with and without sudo. Doesn't work.
Oh, and the jre was installed from add/remove applications (GNOME)

I think that's about it. Now.
What do I do to access libstdc++? Step by step, please.

---

### Post by animefan82 on 2008-05-24
Psh, wrong place. I'll repost in another area. Although if you can answer, much apreciated.

---

### Post by animefan82 on 2008-05-31
Guess what I had to do:

- Open synaptic (or preferred package manager)
- search for "libstdc++"
- mark "libstdc++" for installation
- Apply
- retry JavaEE installation

And it worked... how simple was that?

---

### Post by UnifiedHokie on 2009-02-17
This worked perfectly!!  I was trying to install this bin file so I could play with the Sun Java Access Manager and couldn't get past this error.  Thanks so much posting this

---

