---
title: "how to install iodine on an ubuntu server"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by diwa on 2010-11-30
hello ubuntu experts 

I've downloaded iodine-0.6.0-rc1.tar.gz and opened it in windows7 with 7-zip. the result is the folder iodine-0.6.0-rc1. now i would like to install the package on a linux server with ubuntu 6.0.6. tentatively i copied it to /usr/lib (with full rights) and executed 'apt-get install iodine', without success. moreover: aptitude didn't find iodine, and updating yielded nothing, too.

you see i'm not yet an ubuntu expert. what should i better do? i'm grateful for your help. - diwa

---

### Post by sikander3786 on 2010-11-30
Welcome to the Forums :-)

Remember I am not an expert either :-)

Did you see the extracted .tar.gz for a file named Install or Readme? It might contain the installation instructions.

apt-get won't be able to install that .tar.gz. See the link below for instructions.

[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

Or you can also use checkinstall.

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Remember, don't extract the package. Move it to your Ubuntu as it is i.e, in .tar.gz format.

---

### Post by diwa on 2010-11-30
thank you for your quick answer. - i've followed the two links given. but there are two questions left for me:

(1) i shall copy the file.tar.gz to the ubuntu-vserver, well, but into what folder (root?).

(2) i have to extract file.tar.gz. but which are the commands therefor?

when that is accomplished i will try to follow the instructions connected with your links. - best - diwa

---

### Post by sikander3786 on 2010-11-30
1. Put that in your /home directory.

2. Extract using

```
tar -zxvf iodine-0.6.0-rc1.tar.gz
```

Then cd to the extracted directory.

```
cd iodine-0.6.0-rc1
```

```
./configure
```

```
make
```

```
sudo make install
```

```
clean install
```

---

### Post by diwa on 2010-11-30
EXCELLENT! - that will be a fine job for tomorrow. - indeed, linux deserves friendly help which you accorded me. - thank you so much - diwa

---

### Post by sikander3786 on 2010-11-30
You are more than Welcome. Please let us know how that goes :P

---

### Post by diwa on 2010-12-01
i tried it now: extraction was good, also 'cd iodine-0.6.0-rc1'. but  './configure'  failed: 'no such file or directory'. in fact, there is none. what i see are folders: 'doc, man, src, tests'     and files: 'changelog, makefile, readme, readme-win32, todo'. (readme and todo don't say anything about installing the package.) 

any idea how to proceed? i hesitated to continue with 'make' etc. in order not to unclean the installation. - thank you for further help - diwa

---

### Post by diwa on 2010-12-01
./configure failed, see above - how to proceed? 

why is it SO grotesquely difficult to simply get a program installed on linux, resp. ubuntu? 

with hope for help - diwa

---

### Post by evarlast on 2011-07-04
If you are now running 11.04 ubuntu, you can apt-get install.

sudo apt-get install iodine

If you are not and you are still working with only the tarball you had before, you can skip the configure step. Just type 'make'. That will compile the source. Hopefully 'make install' will work to install the program. If not, you'll can either install it manually (which I will not attempt to cover) or you can run the program out of this source directory. (look in src for what got compiled)

Good luck.

---

