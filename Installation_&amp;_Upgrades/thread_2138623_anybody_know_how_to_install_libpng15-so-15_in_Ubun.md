---
title: "anybody know how to install libpng15-so-15 in Ubuntu 12.04LTS?"
date: 2013-04-24
forum: Installation &amp; Upgrades
---

### Post by FenrirXIII on 2013-04-24
hello community!

i want to upgrade my libpng12 to libpng15 and neither Ubuntu Software Center nor Synaptics carry the upgrade. In the past, I found a PPA but sadly it broke my whole system and converted my ubuntu into linaro (boo!)

anyways, I found a libpng15 here:

[http://sourceforge.net/projects/libpng/files/libpng15/](http://sourceforge.net/projects/libpng/files/libpng15/)

now i just need help compiling it so that i will have libpng15

currently i follow the "INSTALL" file's instruction

and created the ./configure --prefix=/usr/local/libpng

make check (for errors)
sudo make install
then make check (for errors again)
so far it looks successful
but now im trying to install something that depends on libpng15  which still gives me a:

**error while loading shared libraries: libpng15.so.15: cannot open shared object file: No such file or directory**

my idea is that i did not install it properly. can anybody show me how to install it properly?

regards,
FenrirXIII

---

### Post by FenrirXIII on 2013-04-24
Hello Community!

I actually found a way to install it properly:

for those who wanted to install libpng15-s0-15 (or even any other libraries)

first Download library (in this case libpng15)

[http://sourceforge.net/projects/libpng/files/libpng15/](http://sourceforge.net/projects/libpng/files/libpng15/)

locate the downloaded file and _**extract**_ to Downloads folder.

now go to TERMINAL and type

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]cd Downloads/libpng-1.5.15

./configure --prefix=usr/local/libpng
make check
sudo make install
make check
[/TD]
[/TR]
[/TABLE]

Congratulations you just installed the libpng

Now we need to create a shortcut and put it in /usr/lib for any program that is depended on it to work

In TERMINAL type:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]cd                                       (only if you are not using a new terminal)
sudo updatedb                     (this could take a few seconds)
locate libpng                (locate the ".../libpng15.so.15" line and COPY)

now we will create a NEW LINK (shortcut) of that file to "/usr/lib/"

sudo ln -s /usr/local/libpng/lib/libpng15.so.15 /usr/lib/libpng15.so.15
[/TD]
[/TR]
[/TABLE]


you can now successfully execute applications that require libpng15.so.15

---

