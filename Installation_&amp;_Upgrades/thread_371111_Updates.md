---
title: "Updates"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by Orfeus on 2007-02-26
I m trying to install the latest updates but i get this

errors were encountered while processing 
sun-java6-doc
.
.
.
.
you will need to go and update one of the archives
jdk-6-doc.zip    jdk-6-doc.ja.zip

What are this stuf??

---

### Post by nyinge on 2007-02-26
Try this command in the terminal:
```
sudo apt-get -f install 
```

Any complaints?

---

### Post by Orfeus on 2007-03-01
yeah sorry... 



After unpacking 0B of additional disk space will be used.
Setting up sun-java6-doc (6-00-0ubuntu1~edgy1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by nyinge on 2007-03-01
It says that the package, sun-java6-doc, is an "integration installer," which I believe is merely a helper package that will integrate Sun's java documentation into its program.  If you've installed java and need the docs, follow the link it gives you and download the documentation, and place it in the /tmp folder.  Then reinstall the sun-java6-doc package:
```
 apt-get install --reinstall sun-java6-doc 
```

Remember that the documentation you download must have root ownership.  So, if the downloaded doc is on your desktop,
```
 sudo cp /home/USERNAME/Desktop/name_of_downloaded_doc /tmp 
```

Does it work now?

---

### Post by Orfeus on 2007-03-03
```
cp: missing destination file operand after `/home/tziny/Desktop/docs/tmp'
```

The folder was on my desktop but i still get an error

What is that??

---

### Post by nyinge on 2007-03-03
name_of_downloaded_doc /tmp

hehe.. I think you forgot about a space bewteen ...doc and /tmp.  :)

update:  What we're doing here is copying the content of name_of_downloaded_doc to the /tmp directory.

---

### Post by Orfeus on 2007-03-03
Now i get this

```
cp: omitting directory `/home/tziny/Desktop/docs'
```



:confused:

---

### Post by nyinge on 2007-03-04
I'm sorry if I have confused you.  I actually gave it a try myself.  In fact, it's just a matter of placing the file "jdk-6-doc.zip" file in the /tmp folder.

Download the file, jdk-6-doc.zip, from [this]("https://sdlc2a.sun.com/ECom/EComActionServlet;jsessionid=5FA0FB53A9677CE196CA62A595B713DE") Sun's site.  Place it inside the /tmp folder.  Then, try this:  ```
 sudo apt-get install --reinstall sun-java6-doc 
```

Here's the output:
> root@theater:/home/mahuyar# apt-get install sun-java6-doc
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  sun-java6-doc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.6kB of archives.
After unpacking 197kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-doc 6-00-2ubuntu1 [39.6kB]
Fetched 39.6kB in 0s (67.1kB/s)
Selecting previously deselected package sun-java6-doc.
(Reading database ... 146998 files and directories currently installed.)
Unpacking sun-java6-doc (from .../sun-java6-doc_6-00-2ubuntu1_all.deb) ...
Setting up sun-java6-doc (6-00-2ubuntu1) ...
/tmp/jdk-6-doc.zip has been unpacked and installed.
You can now delete it, if you wish.

---

### Post by Orfeus on 2007-03-05
i did it i hope it works...

---

