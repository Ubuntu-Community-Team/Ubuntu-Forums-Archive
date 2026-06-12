---
title: "Trying to instal a program which has files .r1 ,.r2....,r51, .sfv, .nfo"
date: 2012-09-13
forum: Installation &amp; Upgrades
---

### Post by buntys006 on 2012-09-13
Hello 
im new to ubntun
i tried to instal a fille which contain  files .r1 ,.r2....,r51, .sfv, .nfo
i dont know what to do.. 
please help me

---

### Post by ajgreeny on 2012-09-13
What is the program?  More detail please as it sounds as if it needs compiling, which is seldom necessary.

Have you looked in the repositories to see if there is anything that will do the same job, but which you can install in the normal way using the software-center or **apt-get install**?

---

### Post by SlugSlug on 2012-09-13
sounds like it's a RAR archive

install rar and un-rar it 


But like above - I'd try get it via the software center first

---

### Post by Mark Phelps on 2012-09-14
Those sfv and nfo files are Window files.  The first is used to run a checksum on the assembled archive to ensure it's not corrupted.  The second is an information  file.

The .rn files are pieces of the Windows Archive file.  You can assemble them using hj-split, which you will have to hunt down and install.  There is a Java version available which you can simply copy to your machine and run.

But since this archive has WINDOWS files it in, you're most likely NOT going to be able to install the resulting app.

---

