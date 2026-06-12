---
title: "Installing GnuPG"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by halodweller on 2008-06-17
Hello all.  Right up front let me stress I am noob at this.  

Currently I am running Ubuntu 8.04LT and I am trying to install GnuPG, but I am running into some difficulty.

I downloaded the BZ2 file and extracted the contents.  I went into Terminal and navigated to the now extracted gnupg directory and ran ./configure, but I am receiving an error.  Below are the last few lines from Terminal:

checking whether build environment is sane... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


I have attached the log file.  Can anyone help in getting this squared away.  Thank you to all those who read and/or reply.

-Halodweller

---

### Post by meindian523 on 2008-06-17
1]Please don't attach Word files.
2]You don't need to compile and install,GnuPG is available in Synaptic.
3]If you still want to compile and install,you need to install the tools for building,```
sudo apt-get install build-essential
```

---

### Post by halodweller on 2008-06-17
I apologize for the DOC file, but it was a supported extension and log is not.

The code you provided me did work and allowed me to properly run ./configure

Thank you for your response.

-Halodweller

---

### Post by meindian523 on 2008-06-17
.txt is allowed,IIRC.I believe you didn't read the 2nd point,eh?

---

### Post by halodweller on 2008-06-17
In regards to Point 2, I have no idea what synaptic is.

-HD

---

### Post by meindian523 on 2008-06-17
System>>Administration>>Synaptic Package Manager.Rather System>>Help and Support>>Adding and removing software in the left pane.You don't need to always compile software in Linux.This is 2008,not 1988.

---

### Post by halodweller on 2008-06-17
Appreciated.

-HD

---

