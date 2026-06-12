---
title: "installing programs"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by tommytomthms5 on 2005-05-01
hi im a complete noobie i dont know how to install any thing please explain in the simplest terms possible so as to be read by a stupid person

tnx

---

### Post by XDevHald on 2005-05-01
[QUOTE=tommytomthms5]hi im a complete noobie i dont know how to install any thing please explain in the simplest terms possible so as to be read by a stupid person

tnx[/QUOTE]
 Not a problem, to make it really simple for newbies, simply goto **System > Administration > Synaptic Package Manager **and you'll be able to install the package you are looking for by using the **Search **tool. :)

Post any questions you might be having and we'll assist you further :)

---

### Post by tommytomthms5 on 2005-05-01
ok thats good for some programs but what about programs i download??

---

### Post by Professor X on 2005-05-01
It depends on the file type.  If you've downloaded source code the process is a bit more involved, but not difficult.  What is it you are trying to install?

---

### Post by 23meg on 2005-05-01
if you've downloaded a debian package, one with a .deb extension, you can install it by typing 

[PHP]sudo dpkg -i [file path][/PHP]

also check out [the ubuntu guide](http://www.ubuntuguide.org) if you haven't.

---

### Post by tommytomthms5 on 2005-05-01
what about .tar.tz

---

### Post by 23meg on 2005-05-01
that's a compressed archive file, and what you have to do with it depends on its contents. first of all you should extract it to some location using archive manager (by double clicking on it and choosing extract). if it contains source code, you'll have to compile it. if it contains a package, you can install it the way i described above. if it includes a binary executable file, you can duble click on the file after extracting it to run it.

---

### Post by tommytomthms5 on 2005-05-01
[QUOTE=23meg]that's a compressed archive file, and what you have to do with it depends on its contents. first of all you should extract it to some location using archive manager (by double clicking on it and choosing extract). if it contains source code, you'll have to compile it. if it contains a package, you can install it the way i described above. if it includes a binary executable file, you can duble click on the file after extracting it to run it.[/QUOTE]
 it contains sorce codes i think

---

### Post by Professor X on 2005-05-01
Extract the archive using the command ```
tar xzvf file.tar.gz
```.  Read the README file.  Then you shoud enter the commands ```
./configure
make
sudo make install
```

If there are no error messages, that will install the file in its default location in the sytem.

---

### Post by tommytomthms5 on 2005-05-02
god fucking dam it i cant figure this bullshit out  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by XDevHald on 2005-05-02
[QUOTE=tommytomthms5]god fucking dam it i cant figure this bullshit out  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)  ](*,)[/QUOTE]
 You might want to read the **Code of Cunduct** of UbuntuForums as cursing is not tolerated nor allowed.

[http://www.ubuntulinux.org/community/conduct]("http://www.ubuntulinux.org/community/conduct") <---- Please Read

---

### Post by tommytomthms5 on 2005-05-02
what does it mean when it says "permission denied" every time i go to install becouse i read the install file and i did exactly what it said

also how do i turn of the safy feature that wont let me run executables


oh and i sorry about cursing i was *realy* pissed off

---

### Post by Jenda on 2005-05-03
How about RPMs? Anyone?
And how exactly is it with BINs? Are those just executables?

---

### Post by karmah on 2005-05-25
'lo ppl in here!
Im very new to linux too and ive also been trying to figure out how to install programs.
But i've read the readme:s and other install texts that are included in the .tars so ive figured out what you guys said above! But i keep getting the error that i don't have the correct or none C compiler, so i downloaded intel's c compiler but i can't install it 
;P

---

