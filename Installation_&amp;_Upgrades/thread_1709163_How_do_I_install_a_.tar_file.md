---
title: "How do I install a .tar file?"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by Perpetual_Bliss on 2011-03-17
I tried to look up instructions online, but it's too confusing =S Please help!

---

### Post by Perpetual_Bliss on 2011-03-17
Just adding this: I'm trying to install the AUR (abiword light) file, if that helps.

---

### Post by steveneddy on 2011-03-17
What file?

If it is an application or program are you sure that it is not in the repos? easier to install stuff that way.

Post a link to the file you DLed.

** To answer your question directly - a .tar file is like a .zip file - it is compressed.

If it is on the desktop, for example, just right click, which produces a folder on the Desktop - open the folder and look at the Read Me file - should be detailed instructions in there. **

Something like

```
./configure
make
sudo make install
sudo male clean
```

You do this in terminal - one at a time.

---

### Post by Perpetual_Bliss on 2011-03-17
> **steveneddy said:**
> What file?

If it is an application or program are you sure that it is not in the repos? easier to install stuff that way.

Post a link to the file you DLed.

** To answer your question directly - a .tar file is like a .zip file - it is compressed.

If it is on the desktop, for example, just right click, which produces a folder on the Desktop - open the folder and look at the Read Me file - should be detailed instructions in there. **

Something like

```
./configure
make
sudo make install
sudo male clean
```

You do this in terminal - one at a time.
Thanks. I extracted it and then read the installation file. It's telling me to "cd" to the directory where the file's source code is - how do I do that?

I extracted the whole thing into a folder called abiword-2.8.6 inside my downloads folder.
How do I specify the directory in the folder?

---

### Post by JC Cheloven on 2011-03-17
You should answer steven's questions before installing anything. 
In fact it seems you're trying to install abiword, a word processor which is (as steven said, again) much more safely installed from the repositoire.

---

### Post by steveneddy on 2011-03-17
> **JC Cheloven said:**
> You should answer steven's questions before installing anything. 
In fact it seems you're trying to install abiword, a word processor which is (as steven said, again) much more safely installed from the repositoire.

Agreed - go to

System --> Administration --> Synaptic Package Manager

when it opens type in the big screen that lists the applications:

**abiword**

should go magically to the application **abiword**.

just right click and select "Mark For Installation"

Then click the green "Apply" check mark on the top bar.

In mere seconds you will have installed **abiword** and you will find it in:

Applications --> Office --> Abiword

Hope that helps.

---

### Post by Perpetual_Bliss on 2011-03-17
> **steveneddy said:**
> Agreed - go to

System --> Administration --> Synaptic Package Manager

when it opens type in the big screen that lists the applications:

**abiword**

should go magically to the application **abiword**.

just right click and select "Mark For Installation"

Then click the green "Apply" check mark on the top bar.

In mere seconds you will have installed **abiword** and you will find it in:

Applications --> Office --> Abiword

Hope that helps.
No. This was AUR - apparently, a lighter version of Abiword - but I ended up installing Abiword in the end.

Thanks anyways, guys.

---

### Post by kagerato on 2011-03-18
Just in case, you do know that KDE has its own office suite?  KWord is part of it.

As to your original question, *.tar is a Tape archive.  Essentially, it's just a bunch of bundled files.  Usually if you download a tar file for a program, what you're getting is the source code (not an executable).  You can build the program from that source code, using a compiler for the right programming language.  (In this case, we're talking about C or C++, so you can use the GCC toolchain to build it.)

Compiling complicated programs (that is, most GUI applications and anything that has too many dependencies) tends to be a pain.  You often need to install particular development header packages first, and before that you have to lookup which ones those are.  Depending on the age of the program, you sometimes get into version conflicts and/or not being able to find the actual headers you need.

It's a pain, so most people tend to stick to precompiled binaries.  It could be a lot easier, but developers rarely prioritize minimizing dependencies and streamlining the build process.

---

### Post by rotave on 2011-03-18
> **Perpetual_Bliss said:**
> No. This was AUR - apparently, a lighter version of Abiword - but I ended up installing Abiword in the end.
 
Thanks anyways, guys.
 
FYI. AUR = Arch (linux) User Repository. These archives are built for Arch Linux and not Kubuntu/Ubuntu.

---

