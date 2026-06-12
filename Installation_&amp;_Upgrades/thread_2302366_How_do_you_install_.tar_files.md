---
title: "How do you install .tar files?"
date: 2015-11-09
forum: Installation &amp; Upgrades
---

### Post by John_Pawlikowski on 2015-11-09
Hello,
I can't seem to find out how to install a .tar.bz2 file or a .tar.gz file.

This is the problem:
jvpski3@LENOVO-PC:~$ cd Desktop/
jvpski3@LENOVO-PC:~/Desktop$ ls
cups-2.1.0-source.tar.bz2                 foomatic-db-20150819
Emulators & Roms                          Minecraft.jar
fglrx_15.201-0ubuntu1_amd64_UB_14.01.deb  skype.desktop
jvpski3@LENOVO-PC:~/Desktop$ tar xvfz foomatic-db-20150819
tar (child): foomatic-db-20150819: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jvpski3@LENOVO-PC:~/Desktop$ tar xvfz cups-2.1.0source.tar.bz2
tar (child): cups-2.1.0source.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jvpski3@LENOVO-PC:~/Desktop$ cups
No command 'cups' found, did you mean:
 Command 'cgps' from package 'gpsd-clients' (universe)
 Command 'cupt' from package 'cupt' (universe)
 Command 'cusp' from package 'emboss' (universe)
 Command 'cup' from package 'cup' (main)
 Command 'cupsd' from package 'cups-daemon' (main)
cups: command not found

Thank you in advance.

---

### Post by steeldriver on 2015-11-09
In the second case, it looks like a simple typo (you missed the hyphen between '2.1.0' and 'source')

You can use tab completion to avoid simple errors like that - type the first few (unique) characters of the name

```

cups-

```

and then press the TAB key to let the shell supply the rest of the name.

In the first case - it probably is a directory not an archive file. Check using

```

ls -l

```

to get a long listing including file/directory attributes.

---

### Post by John_Pawlikowski on 2015-11-09
After I had extracted the files when I downloaded it, and completed all the steps of code you told me to, this is the return problem I get:
vpski3@LENOVO-PC:~$ cd Desktop/
jvpski3@LENOVO-PC:~/Desktop$ ls
cups-2.1.0-source.tar.bz2                 foomatic-db-20150819
Emulators & Roms                          Minecraft.jar
fglrx_15.201-0ubuntu1_amd64_UB_14.01.deb  skype.desktop
jvpski3@LENOVO-PC:~/Desktop$ tar xvfz foomatic-db-20150819
tar (child): foomatic-db-20150819: Cannot read: Is a directory
tar (child): At beginning of tape, quitting now
tar (child): Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jvpski3@LENOVO-PC:~/Desktop$ tar xvfz cups-2.1.0source.tar.bz2
tar (child): cups-2.1.0source.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jvpski3@LENOVO-PC:~/Desktop$ cups
No command 'cups' found, did you mean:
 Command 'cgps' from package 'gpsd-clients' (universe)
 Command 'cupt' from package 'cupt' (universe)
 Command 'cusp' from package 'emboss' (universe)
 Command 'cup' from package 'cup' (main)
 Command 'cupsd' from package 'cups-daemon' (main)
cups: command not found

.

---

### Post by xsnake_ on 2015-11-10
The important error messages are the following:
```
[COLOR=#000000]tar (child): foomatic-db-20150819: Cannot read: Is a directory[/COLOR]
```
This means that foomatic-db-20150819 is a directory, perhaps try to "cd foomatic-db-20150819" and see what's in there.

```
[COLOR=#000000]tar (child): cups-2.1.0source.tar.bz2: Cannot open: No such file or directory[/COLOR]
```
The program tar is unable to find the file cups-2.1.0source.tar.bz2. This is because you mispelled the filename, it should be cups-2.1.0[COLOR=#ff0000]-[/COLOR]source.tar.bz2 (notice the dash). As suggested by steeldriver, you might want to use the TAB key in order to avoid these kind of mistakes.

Also, for your information, all the tar command will do is extract the files enclosed in the compressed archive. To use the software, you will most likely have to compile it, using the command "./configure" and then "make". Normally you should have plenty of errors telling you about missing packages required for compilation. Those may be install using sudo apt-get install <software name>-dev.

Best of luck!
Carl

---

### Post by oldos2er on 2015-11-10
What version of Ubuntu are you using? Cups should be installed by default on desktop versions.

---

### Post by Bucky Ball on 2015-11-10
> **oldos2er said:**
> What version of Ubuntu are you using? Cups should be installed by default on desktop versions.

Yes, it should, and strange if it's not. :-k

@John_Pawlikowski: Please use code tags for your terminal output. See the last link in my signature. Thanks.

---

