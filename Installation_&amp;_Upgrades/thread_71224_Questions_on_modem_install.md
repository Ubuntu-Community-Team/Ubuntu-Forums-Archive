---
title: "Questions on modem install"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by eagleseye on 2005-10-02
I have a modem with the Conexant HCF chipset so I downloaded the driver available at luxincant and the install instructions.  I don't understand the first line.  Extract with "tar -xzf riptide(version).tar.gz."  What does version refer to?  I tired various things for version to no avail, also, get an error message concerning riptide.  I believe it was something like a bad command or  unavailable.

I can do most anything with the floppy except see it in terminal.  Anything typed with floppy0 in the line results in an error to the affect, floppy0 not found.  I found instructions on another post regarding making a directory with floppy0 in it.  Do I need to do so?

If this is to vague, I'll boot back into Unbuntu and get the exact error messages. Ubuntu seems like a good OS if I can learn a new language, Unix.

---

### Post by mlomker on 2005-10-02
> Extract with "tar -xzf riptide(version).tar.gz."  

Just use the name of the file: **tar zxvf filename.tar.gz**

> 
I can do most anything with the floppy except see it in terminal.  Anything typed with floppy0 in the line results in an error to the affect, floppy0 not found.  I found instructions on another post regarding making a directory with floppy0 in it.  Do I need to do so?


If you can see if from the desktop then you should also be able to go into the /media/floppy0 folder or wherever it is mounting it.  If it isn't mounting then you can do this:

```

sudo mkdir /media/floppy0
sudo nano /etc/fstab

```

Add this:

```

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 2

```

Ctrl-W, Y, Enter to save.  Afterward you should be able to type:

```

sudo mount /dev/fd0

```

---

### Post by eagleseye on 2005-10-02
Thanks for your quick reply, I tried using the filename, hcfpci~1.deb.  The floppy is seen in the media folder along with the CDrom, just not when using terminal.  It was your instructions I copied from another post about making the directory.  I'll try that next, maybe that is the problem.

---

### Post by mlomker on 2005-10-02
> hcfpci~1.deb.

Debian files (.deb) are not installed that way.

Try:

```

sudo dpkg -i hcfpci~1.deb

```

---

