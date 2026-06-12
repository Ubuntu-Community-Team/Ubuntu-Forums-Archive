---
title: "kernel modules"
date: 2007-09-12
forum: Kenyan Team - Kenya
---

### Post by muithi on 2007-09-12
Hi there,

How can one make downloaded softwares said to be able to run on a linux platform to be instaledl and run on ubuntu? as in not necessarily from ubuntu....I mean something like "it can run on a linux environment." basically lyk those with a ".gz" extension 


byeeee,

Mwema

---

### Post by ddrichardson on 2007-09-13
[Here]("http://blog.lynxworks.eu/?p=23").

---

### Post by ronaldotis on 2007-09-18
Well, I may ask you to be more specific with the question. Before you build a kernel module, you have to know basically what its supposed to do,e.g. for sound purposes. Second, you have to make sure that the hardware is of the right standard, which always happens in most cases.
If you ask the question more precisely, I think I will be able to help.

NB- If you are a novice, I ask you to refrain from anything to do with the kernel unless you are absolutely sure of what you are doing. It's analogous to heart surgery

---

### Post by zsh on 2007-09-18
> **muithi said:**
> Hi there,

How can one make downloaded softwares said to be able to run on a linux platform to be instaledl and run on ubuntu? as in not necessarily from ubuntu....I mean something like "it can run on a linux environment." basically lyk those with a ".gz" extension 


byeeee,

Mwema

Hi Mwema,

Its usually a better idea to install ubuntu packages from the repos since that way if a newer version of the package is released upgrading is very simple using apt-get.

Sometimes a package for a particular software may not be available or its package is not new enough o one has to compile from source. The .gz files you are talking about are the source code of the software. Instructions for compiling them can be found here [http://www.faqs.org/docs/Linux-HOWTO/Software-Building-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Software-Building-HOWTO.html).

I STRONGLY recommend that you dont compile your own kernel unless you know what you are doing.

---

### Post by ronaldotis on 2007-09-21
Actually, what you meant was software packages/applications from the internet. They come in 3 forms; rpm, apt and source. For Ubuntu it will only be apt or source. The .gz extension you're talking about is source package that has been compressed (and in most cases archived.)
To uncompress it (and also unarchive it), you run the following command;
tar xfvz software.xx.x.xx.tar.gz

I think you will have to check the link you were given above.

---

