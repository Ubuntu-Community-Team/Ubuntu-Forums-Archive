---
title: "No GCC?"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by Jerryonimo on 2007-08-06
I don't believe it! Ubuntu 6.0 doesn't come with a C compiler!](*,)
I tried to install a .tar.gz file the other day, but it burped up the error message that I don't have a C compiler.  Sure enough, I looked and I didn't have gcc.  Do I just download a C compiler or do I need libraries, too?  Could I download the .tar.gz source, or would I need a C compiler to install the C compiler?:confused:

---

### Post by g2g591 on 2007-08-06
just download the package "build-essential" . if you do not know how to install that, just use "sudo apt-get install build-essential"

---

### Post by JudasReanimated on 2007-08-06
Open Terminal

sudo aptitude install build-essential

That should fix it.

---

### Post by Jerryonimo on 2007-08-06
Please keep in mind that I don't yet have Internet on my Linux system.:frown:

---

### Post by g2g591 on 2007-08-06
both of our commands do the exact same thing, just use which ever you are most comfortable with.

---

### Post by Jerryonimo on 2007-08-06
Alright.  Thanks.:)

---

### Post by g2g591 on 2007-08-06
hmm that is a problem.. try to use your install cd as a repository, just put in the cd, open synaptic, and open the repository menu, then check the box for the cd, then you will probabily get it working. If that doesnt work, try to get your internet working

---

### Post by JudasReanimated on 2007-08-06
Hmm alright, you can also download the package from here, and install it from a disk.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=names&subword=1&version=all&release=all)

---

### Post by g2g591 on 2007-08-06
thats the package you need, not sure exactly how to move files from a windows partation to a linux partation

---

### Post by JudasReanimated on 2007-08-06
He could use any number of removable storage, or a CDR would work great as well.

Then just take the file off the CD copy it to your desktop and install it.

---

### Post by g2g591 on 2007-08-06
I know, but I ment that I didn't know a Direct way.  Like somehow getting windows to dect the Ubuntu partation, and write to it.

---

### Post by JudasReanimated on 2007-08-06
XD getting Windows to do anything productive without destroying 50 other things in the process. Yeah I understand what you mean, but this way works pretty easily if he can't find it in synaptic or doesn't feel comfortable doing it.

---

### Post by Jerryonimo on 2007-08-07
Is there an actual package of build-essential?  I checked out the Debian search site, tired to download it, but all I got was an empty file.

---

### Post by psusi on 2007-08-07
build-essential is just a metapackage.  It does not contain any actual files.  It is just there to depend on all of the other packages you are likely to need to compile thing so they all get pulled in when you install it.  

You can burn the alternate cd and use that as a repository to install the packages from.

---

### Post by Jerryonimo on 2007-08-07
Oh, so then I can just install the C compiler.  Do I need the libraries as well?

---

### Post by psusi on 2007-08-08
Yes, which is why build-essential is there.

---

