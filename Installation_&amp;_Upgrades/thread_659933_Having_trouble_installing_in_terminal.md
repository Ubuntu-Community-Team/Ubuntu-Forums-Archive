---
title: "Having trouble installing in terminal"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by Ceridan on 2008-01-06
HI
I'm trying to install mount-iso-0.9.5 to mount playstation isos.
The folder has only 3 files, Two of them are text documents. One is install.sh.
That's what happens when I try to install:
[PHP]ceridan@ceridan-desktop:~/Dummy/mount-iso-0.9.5$ ./configure
bash: ./configure: No such file or directory
ceridan@ceridan-desktop:~/Dummy/mount-iso-0.9.5$ make
make: *** No targets specified and no makefile found.  Stop.
ceridan@ceridan-desktop:~/Dummy/mount-iso-0.9.5$ sudo make install
[sudo] password for ceridan:
cat install.sh >install 
chmod a+x install[/PHP]
Now another script appears in my folder called install.
What do I do with that?
I tryed:
[PHP]ceridan@ceridan-desktop:~/Dummy/mount-iso-0.9.5$ install
install: missing file operand
Try `install --help' for more information.
ceridan@ceridan-desktop:~/Dummy/mount-iso-0.9.5$ ./install
./install: 160: function: not found

Couldn't find !
Type the full path here or press "Ctrl+C" to abort: 
ceridan@ceridan-desktop:~/Dummy/mount-iso-0.9.5$ sudo ./install
./install: 160: function: not found

Couldn't find !
Type the full path here or press "Ctrl+C" to abort:[/PHP]
I read the readme and it tells me only to type ./install.sh
[PHP]ceridan@ceridan-desktop:~/Dummy/mount-iso-0.9.5$ ./install.sh
./install.sh: 160: function: not found

Couldn't find !
Type the full path here or press "Ctrl+C" to abort: [/PHP]

I've also tryed:
[PHP]ceridan@ceridan-desktop:~/Dummy/mount-iso-0.9.5$ sudo sh ./install.sh
./install.sh: 160: function: not found
[/PHP]
And I tryed other stuff too. I've been working on this for hours but i'm new to linux so maybe its something simple.

thanks

---

### Post by forestpixie on 2008-01-06
don't know if this will help - have you tried changing into the directory before you run the commands

cd Desktop
cd *nameofdirectory*

---

### Post by taurus on 2008-01-06
You know you can mount an ISO image without installing any extra program for it.

```
sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
ls -la /media/iso
```

---

### Post by Ceridan on 2008-01-06
> don't know if this will help - have you tried changing into the directory before you run the commands

cd Desktop
cd nameofdirectory

Yes I did change my directory to the right one,

> You know you can mount an ISO image without installing any extra program for it.

Code:

sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
ls -la /media/iso



Yah I read about that but I also read that normal isos and playstation isos are diffrent. I has to do with the "iso19660" thingy. Heres a link to where I read it: 

[http://linuxreviews.org/howtos/cdrecording/#toc11](http://linuxreviews.org/howtos/cdrecording/#toc11)

They say we can burn these cds with "cdrdao", but I tryed to install that and I had the exact same problem installing it.

---

### Post by mzw! on 2008-03-23
open install.sh
```
kdesudo kate install.sh
```

And edit the first line
```
#!/bin/sh
```

write this instead:
```
#!/bin/bash
```

That solved the "function not found" error in line 160, but I am not sure this is so... correct ehehe.

---

