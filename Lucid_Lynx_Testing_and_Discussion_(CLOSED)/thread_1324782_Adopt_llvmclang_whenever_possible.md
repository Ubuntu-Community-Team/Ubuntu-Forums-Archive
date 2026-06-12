---
title: "Adopt llvm/clang whenever possible"
date: 2009-11-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mojo on 2009-11-12
clang compile C program faster and output smaller binary. Why not adopt this beautiful tool? Meanwhile, C++ or other programs can keep using GCC til clang support C++ better.

---

### Post by Regenweald on 2009-11-12
So lets throw another not so mature tool into the mix ? Why not wait a bit ?

---

### Post by ssam on 2009-11-13
i'd love to see a tool that lets you do:
```
apt-recompile cc=llvm packagename
```
or
```
apt-recompile flags='-Os' packagename
```

though maybe gentoo is the distro to use if you want to experiment with compiler options.

---

### Post by gnomeuser on 2009-11-13
While I am a big fan of dumping gcc (and thus also our dependency on a poorly run FSF project that generates notoriously bad code, bad warnings and poorly performing both code and compiling), I would be worried about llvm not implementing a number of the security features that GCC/glibc have grown in the last couple of years.

---

### Post by LittleKoy on 2009-11-13
> **gnomeuser said:**
> While I am a big fan of dumping gcc (and thus also our dependency on a poorly run FSF project that generates notoriously bad code, bad warnings and poorly performing both code and compiling), I would be worried about llvm not implementing a number of the security features that GCC/glibc have grown in the last couple of years.

Uhm, let's make clear that I'm not attacking you, I'm genuinely interested in the thing. Do you have proofs about gcc producing a poorly optimized code? I saw a few benchmark but llvm quite lagged behing pure gcc, and the best compiler I know of (talking about performing code), ICC, is not so distant.

---

### Post by gnomeuser on 2009-11-13
> **LittleKoy said:**
> Uhm, let's make clear that I'm not attacking you, I'm genuinely interested in the thing. Do you have proofs about gcc producing a poorly optimized code? I saw a few benchmark but llvm quite lagged behing pure gcc, and the best compiler I know of (talking about performing code), ICC, is not so distant.

The FreeBSD people did some investigations when undertaking their llvm project, I believe you can look at phk's postings for some examples of how GCC occasionally produces odd output.

---

