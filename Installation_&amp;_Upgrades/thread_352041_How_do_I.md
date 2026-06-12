---
title: "How do I?"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by bobbilob on 2007-02-02
How do I download and install Adobe Reader?

---

### Post by neverett on 2007-02-02
[http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html)

Here you are going to select the .tar.gz download the file and save it to the desktop.

You can follow these directions then:

To install adobe Reader 7.0.8 using a tarball installer

1. Open a terminal window.

2. Change directory (using the cd command) to the directory that contains the tarball archive.

3. Run one of the following commands.

    * On Linux:

tar -zxvf AdobeReader_enu-7.0.8-1.i386.tar.gz

If the -z command-line option for the tar command does not work on your operating system, then run the gunzip command on the .gz file and then run the tar -xvf command on the resulting .tar file.

By default, on Linux, Adobe Reader is installed in /usr/local/Adobe/Acrobat 7.0. You can however, specify a different location by using the following command-line option: --install_path= <adobe_install_dir>

4. In the newly created AdobeReader directory, run the INSTALL script.

5. Add <adobe_install_dir> /bin to the PATH environment variable to allow browsers to launch Adobe Reader, where <adobe_install_dir> is the installation directory of Adobe Reader 7.0.8.

Let me know if that works for you!

---

### Post by Paerez on 2007-02-02
Open up Synaptic Package manager and install "acroread" or run:
sudo aptitude install acroread
from a terminal.

---

### Post by neverett on 2007-02-02
> **Paerez said:**
> Open up Synaptic Package manager and install "acroread" or run:
sudo aptitude install acroread
from a terminal.

I would try this before my method.  If all else fails, then try mine.

---

### Post by Paerez on 2007-02-02
also if you want adobe reader inside firefox, install "mozilla-acroread"

---

### Post by bobbilob on 2007-02-03
Thanks guys:

Got it working inside firefox, but not inside Explorer. Any help?

---

### Post by meng on 2007-02-03
Internet Explorer? Or do you mean Nautilus (the file manager, we don't call it Explorer because that's not its name). If you mean that it is not the default application to open pdf in Nautilus, then do this: right-click on a pdf and go to Properties > Open With, and choose Acrobat as the default opening application.

---

### Post by bobbilob on 2007-02-04
I have adobe reader and microsoft internet explorer working but explorer can't yet open a .pdf file. Any help?

---

### Post by bobbilob on 2007-02-04
I downloaded IES4Linux and installed IE6, Thing load OK, but I can't print or opwn .pdf documents from within IE6.:confused:

---

### Post by Paerez on 2007-02-04
try installing the windows adobe plugin through IE6. You will have to download adobe for windows and install it under linux using wine.

---

### Post by meng on 2007-02-04
You would probably have to install Adobe Reader within wine. I can't quite fathom why you need to open pdfs within IE6, though ...

---

### Post by Paerez on 2007-02-04
The mozilla-acroread plugin is pretty much the identical program to adobe inside IE6, except that the mozilla-acroread plugin will integrate with ubuntu better (so it will be easier to print, etc).

---

### Post by bobbilob on 2007-02-04
> **meng said:**
> You would probably have to install Adobe Reader within wine. I can't quite fathom why you need to open pdfs within IE6, though ...

I'd really like to not need to. Real Estate forms in Canada can be filled in online but the process involves typing into an open .pdf file... go figure!!

How do I install Adobe Reader and some printer drivers from within wine??

---

### Post by meng on 2007-02-04
Install the acroread plugins, they will enable you to fill out forms in the native Linux version of Acrobat Reader. Ask the right question, you'll get the appropriate answer.

---

