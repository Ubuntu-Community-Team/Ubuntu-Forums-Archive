---
title: "Online banking"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by Didius on 2007-04-01
Hi

I've installed Ubuntu on my parents computer, they absolutly love it, but they still need windows because they want online banking.

I would like to remove windows however and i saw this:
[https://www.kbc.be/IPA/D9e01/~N/~KBC/~BZJ6N7W/-BZIQJDK/BZJE1H6/BZJ6N7G/~-BZJ6NI5](https://www.kbc.be/IPA/D9e01/~N/~KBC/~BZJ6N7W/-BZIQJDK/BZJE1H6/BZJ6N7G/~-BZJ6NI5)
The bank also offers a linux package: KBC-Online Local for Linux (9 MB)

When i downloaded it I got this error:
```
$ sh install_linux.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

rm: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
rm: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
```

After some research, i change a line of code (export LD_ASSUME_KERNEL=2.2.5 tot #export LD_ASSUME_KERNEL=2.2.5) and now I get this:
```
$ sh install_linux.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Exception in thread "main" java.lang.NoClassDefFoundError: com/zerog/lax/LAX
```

---

### Post by pradeepadapa on 2007-04-01
it seems that u havent java installd in ur ubuntu system, just check if java is present or not by typing  javac at the terminal prompt,nd if it succeds then u hav it otherwise u need to install it from synaptic manager or from other update sources like automatix or from apt-get

---

### Post by Didius on 2007-04-01
the javac commando works, and the java packages are installed.
I also installed the Java from automatix, but no change.

Any other solutions?

---

