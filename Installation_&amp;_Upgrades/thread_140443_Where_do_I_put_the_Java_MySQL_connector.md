---
title: "Where do I put the Java MySQL connector?"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by Cosmic P on 2006-03-06
I need a MySQL Java Driver (or connector if you like) to work with OpenOffice.org 2. I could download the file "mysql-connector-java-5.0.0-beta.zip", but where do I save that file and install it?

---

### Post by knalle on 2006-03-06
install the **libmysql-java** package instead

```

sudo apt-get install libmysql-java

```

---

### Post by Cosmic P on 2006-03-06
That didn't work.

I get an error message on the command line:

"Package libmysql-java is not available, although it is referenced by another package. It is possible that this package is missing, outdated or only available from another source."

---

### Post by knalle on 2006-03-06
maybe its in **multiverse**, try that

---

### Post by Cosmic P on 2006-03-06
You mean from the command line? How do I do that?

Ik can't find it in Synaptic.

---

### Post by knalle on 2006-03-06
[QUOTE=Cosmic P]You mean from the command line? How do I do that?

Ik can't find it in Synaptic.[/QUOTE]

in synaptic, modify your **repositories** to say **multiverse** after **universe**, or edit the file ```
sudo emacs /etc/apt/sources.list
```.

---

### Post by Cosmic P on 2006-03-06
I already did that, but I still can't find it. Isn't there a file that contains the URLs of all the packages? I should first check if libmysql-java is listed.

---

### Post by knalle on 2006-03-06
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libmysql-java&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libmysql-java&searchon=names&subword=1&version=breezy&release=all)

---

### Post by Cosmic P on 2006-03-06
Thx

---

