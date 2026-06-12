---
title: "[ask]install from source??"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by fourteenth on 2010-02-25
hi all.
I'm new to Linux and ubuntu here..
I was wondering how can I install a program or software form source tarball?
I used to install by apt-get and synaptic.
so, what are the differences?

If I install from source tarball?
will my installed program or software listed in synaptic?
thanks..

---

### Post by booshire on 2010-02-25
> **fourteenth said:**
> hi all.
I'm new to Linux and ubuntu here..
I was wondering how can I install a program or software form source tarball?
I used to install by apt-get and synaptic.
so, what are the differences?

If I install from source tarball?
will my installed program or software listed in synaptic?
thanks..

So...tar ball is usually source code. Also, usually includes a README or howto file after you extract it. Maybe not, oh well. It will not work like a .deb or whatever from a repository. You usually untar the thing (tar -xvf [filename.tar], it will make a directory wherever you are at with the files in it (check the man page to see how to extract it elsewhere [man tar]). Usually executing the command (inside the directory) 'make install' (or just 'make') will compile the thing, outputting (errors and) everything. A program name or more info needed if this does not work. Welcome to Linux/Unix, where you have to read instructions and not just double click all the time.

---

### Post by fourteenth on 2010-02-25
> **booshire said:**
> So...tar ball is usually source code. Also, usually includes a README or howto file after you extract it. Maybe not, oh well. It will not work like a .deb or whatever from a repository. You usually untar the thing (tar -xvf [filename.tar], it will make a directory wherever you are at with the files in it (check the man page to see how to extract it elsewhere [man tar]). Usually executing the command (inside the directory) 'make install' (or just 'make') will compile the thing, outputting (errors and) everything. A program name or more info needed if this does not work. Welcome to Linux/Unix, where you have to read instructions and not just double click all the time.

thanks for reply.
I want to know is it difficult to install from source?
I read a few article about it, it seems a difficult way to install software.
Am I must know well the terminal command, and a basic of programming language to do it?

What about the installation folder?
How can I trace which files and folders being used when I run 'make' or 'make install'?
How do I delete it?
and my very first question, Will my software listed in synaptic?

---

### Post by NefariousNobo on 2010-02-25
Would it show up in Synaptic?

Very much depends on the software, but I'd have to say probably not. On the other hand, in a distro like Gentoo, all the software is usually compiled from source, and it is listed in Portage, so I can't say for certain. If it's standard software also available through the Debian/Ubuntu repositories, it might. Else, it would probably not.

Is it difficult?

Depends on how you look at it. It's probably a little tougher than Apt-Get, but as far as difficulty goes, it's not that bad.

...Terminal Command?

You don't need to know *well* the Terminal commands. Just mainly TAR, and MAKE (INSTALL) as well as simple commands like CD.

How can I trace which files and folders being used when I run 'make' or 'make install'?

Usually, all software is installed to the same directory. Probably, you can expect the new software to go there as well. If in doubt, you could read the MAKEFILE.

How do I delete it?

If it DOES get listed in Synaptic, use it. If not, you can delete the actual program, or maybe there is a utility you could use instead.

Hope this helps...

---

### Post by nothingspecial on 2010-02-25
Have a look at [COLOR="Magenta"][checkinstall]("http://www.asic-linux.com.mx/~izto/checkinstall/")[/COLOR]

You will need to ```
sudo apt-get install build-essential
```

Always read the README file, this will contain specific instructions for installing the package.

---

### Post by fourteenth on 2010-02-25
> **NefariousNobo said:**
> Would it show up in Synaptic?

Very much depends on the software, but I'd have to say probably not. On the other hand, in a distro like Gentoo, all the software is usually compiled from source, and it is listed in Portage, so I can't say for certain. If it's standard software also available through the Debian/Ubuntu repositories, it might. Else, it would probably not.

Is it difficult?

Depends on how you look at it. It's probably a little tougher than Apt-Get, but as far as difficulty goes, it's not that bad.

...Terminal Command?

You don't need to know *well* the Terminal commands. Just mainly TAR, and MAKE (INSTALL) as well as simple commands like CD.

How can I trace which files and folders being used when I run 'make' or 'make install'?

Usually, all software is installed to the same directory. Probably, you can expect the new software to go there as well. If in doubt, you could read the MAKEFILE.

How do I delete it?

If it DOES get listed in Synaptic, use it. If not, you can delete the actual program, or maybe there is a utility you could use instead.

Hope this helps...

> **nothingspecial said:**
> Have a look at [COLOR=Magenta][checkinstall]("http://www.asic-linux.com.mx/%7Eizto/checkinstall/")[/COLOR]

You will need to ```
sudo apt-get install build-essential
```Always read the README file, this will contain specific instructions for installing the package.

Thank you for both of your reply..:D
They're very really useful information.
I understand the basic of this topic right know..

Probably, my last question about this topic, if I already have an installed software by synaptic, and I install same software but different version by compiling its source?
Is installing from source will overwrite the one from synaptic?

Maybe I should figure it by myself by install some software by trial and error, but as I said in my first post, I'm new to ubuntu and linux..
I'm afraid I will mess up and screw my ubuntu..
thanks..

---

### Post by nothingspecial on 2010-02-25
You should remove the version you have in synaptic first.

---

