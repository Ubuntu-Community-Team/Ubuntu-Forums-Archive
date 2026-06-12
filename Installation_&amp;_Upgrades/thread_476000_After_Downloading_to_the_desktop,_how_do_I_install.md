---
title: "After Downloading to the desktop, how do I install a program?"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Adam the first on 2007-06-16
Hey,

I'm totally new to Using Ubuntu, and I'm liking it so far.

Just a few things.  I've downloaded a few desklets and one theme, but I don't know how to install them. 

Can anyone give me a step by step guide? (Or tell me where to go to get one?)

Thanks!

Adam, new guy

---

### Post by steveneddy on 2007-06-16
System --> Preferences --> Theme

Drag and drop the theme in tar.gz format, into the window and it installs itself.

As for other programs that you DL from the internet, unpack them by right clicking the file, select "Extract Here" and when the folder appears on your desktop, or where ever you DLed it to, open the folder and read the "Read Me" file and see if there is an "Install" file to read.

It should go something like this.

In a terminal, cd to the folder. Lets say that it was a folder on my desktop named pidgin-2.0.2.

```
cd ~/Desktop/pidgin-2.0.2

```

then do this in a terminal

```
 sudo ./configure 
```

Let it run, it will take a while. 

Then

```
make
```

Then

```
sudo make install
```

and when it is all done try a 

```
make clean
```

This moves the terminal to the folder where the install files live. Next it configures everything to YOUR system, then it makes the packages for you, then installs them. The make clean command cleans up all of the little snippets of trash that the install leaves behind.

Hope this helps.

-SE

You can also install things from Synaptic.

---

### Post by Adam the first on 2007-06-16
Thank you, 

I'll give that a try and let you know what happens! :)

---

### Post by steveneddy on 2007-06-17
> **Adam the first said:**
> Thank you, 

I'll give that a try and let you know what happens! :)

Good luck - we're all counting on you.

---

### Post by mptpro on 2007-11-17
How exactly does one install from Synaptic?

What if it is a DL that is directly from a web site, but not listed in the Snaptic repository?  Can that file still be installed via synatpic?

thanks

---

### Post by logos34 on 2007-11-17
> **mptpro said:**
> How exactly does one install from Synaptic?

What if it is a DL that is directly from a web site, but not listed in the Snaptic repository?  Can that file still be installed via synatpic?

thanks

[https://help.ubuntu.com/7.10/add-applications/C/advanced.html](https://help.ubuntu.com/7.10/add-applications/C/advanced.html)

If you downloaded a .deb pkg, click on it--it will use the GDebi installer.  It will show up in synaptic afterwards.

[https://help.ubuntu.com/7.10/add-applications/C/install-file.html](https://help.ubuntu.com/7.10/add-applications/C/install-file.html)

---

### Post by mptpro on 2007-11-17
thanks!

---

