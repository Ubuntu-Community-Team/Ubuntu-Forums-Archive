---
title: "C++ Compiller"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by dJnEvS on 2005-09-28
```
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
```

does someone know a good c++ compiller that can compile executable files?

---

### Post by darkmatter on 2005-09-28
[QUOTE=dJnEvS]```
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
```

does someone know a good c++ compiller that can compile executable files?[/QUOTE]

```
sudo apt-get install build-essentials
``` for your general compiling needs.

---

### Post by dJnEvS on 2005-09-28
```
E: Couldn't find package build-essentials
```

hmm:?

---

### Post by darkmatter on 2005-09-28
[QUOTE=dJnEvS]```
E: Couldn't find package build-essentials
```

hmm:?[/QUOTE]

Oops...Been up most the night, eyes are blurry. Make that
```
sudo apt-get install build-essential
```

Sorry.

---

### Post by whiterabbit on 2005-09-28
darkmatter!!!!!! Thank you!

---

### Post by darkmatter on 2005-09-28
[QUOTE=whiterabbit]darkmatter!!!!!! Thank you![/QUOTE]

You're welcome.:)

---

### Post by dJnEvS on 2005-09-28
```
build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed
```

libc6-dev needs libc6, it says it is already newest version, so i cant install it :?

---

### Post by YourSurrogateGod on 2005-09-28
[QUOTE=dJnEvS]```
build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed
```

libc6-dev needs libc6, it says it is already newest version, so i cant install it :?[/QUOTE]
Why don't you go into synap, search for "g++" and install the C++ compiler from there? It should be something called g++ -3.3...

---

### Post by YourSurrogateGod on 2005-09-28
You can always try openc++ in synap (search for 'openc++' in synap.) That's a C++ compiler.

---

