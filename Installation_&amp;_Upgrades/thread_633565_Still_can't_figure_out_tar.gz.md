---
title: "Still can't figure out tar.gz"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by jennica on 2007-12-06
I am trying to install KBFX Silk [[http://www.kde-apps.org/content/show.php?content=24898]](http://www.kde-apps.org/content/show.php?content=24898])

I still don't get how to install the tar.gz files though. Is there a program that will do it for me? Last time I tried, make install and all of that did not work.

And where do I download the file into before I go into the konsole and 'install it'?

---

### Post by Pumalite on 2007-12-06
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by erickramirez on 2007-12-06
> **jennica said:**
> I still don't get how to install the tar.gz files though. Is there a program that will do it for me? Last time I tried, make install and all of that did not work.

The .gz extension refers to a file that has been compressed with gzip. TAR is short for "tape archive". In the old *nix days, files where concatenated with one another so that they could be saved to tape in one continuous stream.

If you had a file, say "myfile.tar.gz", then unzip it first, e.g. ```
$ gunzip myfile.tar.gz
```.

After that, you can "expand" the archive by running ```
$ tar xvf myfile.tar
```.

I hope I haven't misunderstood you.

Cheers,
Erick Ramirez
Melbourne, Australia

---

### Post by jennica on 2007-12-06
I am still having this problem that if I am not hovering over the window, it will not let me type. what is that?

got it figured out nevermind.

---

### Post by MQMike on 2007-12-06
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

and at the bottom, it is cross-linked to two other ubuntu articles on installing software, and the 3 go together.

---

### Post by lvleph on 2007-12-06
There is no reason to unzip it first. You can do the unzipping and untarring at the same time.

tar -xzf file.tar.gz

If you would like to tar and gzip a file you can do

tar -czf file.tar.gz file1 file2 folder1 folder2

I like to use .tgz instead of tar.gz

---

### Post by zvacet on 2007-12-07
```
sudo aptitude install rar unrar p7zip p7zip-full
```

When you have these installed just right click on file and select **unpack here**.

---

