---
title: "Install software in Ubuntu without checking for dependencies"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by h66m9d on 2012-09-15
How can i install software in terminal without checking for dependencies?:?
I use Ubuntu 12.4 LTS

---

### Post by snowpine on 2012-09-15
Welcome to the forums!

What is the software you are trying to install?

The typical command would be something like:

```
sudo apt-get install firefox
```

Does that work for you?

---

### Post by h66m9d on 2012-09-15
> **snowpine said:**
> Welcome to the forums!

What is the software you are trying to install?

The typical command would be something like:

```
sudo apt-get install firefox
```

Does that work for you?

Thanks for welcome message;)
I want install many softwares (.deb) in offline mode from a folder
and I want be sure installed all my ".deb" files
some software wasn't install in offline mode because they have dependencies
I need install them and ignore their dependencies

---

### Post by snowpine on 2012-09-15
Some applications won't work without their dependencies. That is what "dependency" means.

---

### Post by Neoracu on 2012-09-15
My suggestion is to install and use APTOnCD.
This will allow you to create a disc image with the packages you have in the folder, it will auto select the dependencies(only if you have the packages).
Then you just need to burn the image to a CD, CD's or DVD(I think a rewritable one would be better).
When you insert the disc it will ask you if you want to add the CD to the sources.
After that you can install whatever is in the CD.

Best Regards

---

### Post by h66m9d on 2012-09-16
> **Neoracu said:**
> My suggestion is to install and use APTOnCD.
This will allow you to create a disc image with the packages you have in the folder, it will auto select the dependencies(only if you have the packages).
Then you just need to burn the image to a CD, CD's or DVD(I think a rewritable one would be better).
When you insert the disc it will ask you if you want to add the CD to the sources.
After that you can install whatever is in the CD.

Best Regards

Thanks a lot!
Why my ATPonCD can't load iso file in ubuntu 12.4?
"Load..." butom doesn't work.
even I was install k3b and drasero & Gdebi

---

### Post by tienlbhoc on 2012-09-16
sudo dpkg -i --force-depends *.deb (if you got deb main and dependences in a folder)

or use local repositories
[http://ubuntuofflineinstall.blogspot.com/2012/09/how-to-build-local-apt-repositories.html](http://ubuntuofflineinstall.blogspot.com/2012/09/how-to-build-local-apt-repositories.html)

---

### Post by h66m9d on 2012-09-16
> **tienlbhoc said:**
> sudo dpkg -i --force-depends *.deb (if you got deb main and dependences in a folder)

or use local repositories
[http://ubuntuofflineinstall.blogspot.com/2012/09/how-to-build-local-apt-repositories.html](http://ubuntuofflineinstall.blogspot.com/2012/09/how-to-build-local-apt-repositories.html)
Thank you.
your answer is excellent

---

### Post by Neoracu on 2012-09-16
> **tienlbhoc said:**
> sudo dpkg -i --force-depends *.deb (if you got deb main and dependences in a folder)

or use local repositories
[http://ubuntuofflineinstall.blogspot.com/2012/09/how-to-build-local-apt-repositories.html](http://ubuntuofflineinstall.blogspot.com/2012/09/how-to-build-local-apt-repositories.html)

This is a good one, If only I knew it 4 years ago...

---

