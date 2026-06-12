---
title: "Install Plone 3.1.5.1 with Unified Installer"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by force317 on 2008-08-28
Can someone explain me how to use the Unified Installer .gz file to setup Plone CMS 3.1.5.1 on an Ubuntu 8.04.1 PC for testing.

[URL="http://plone.org/products/plone"]

I am a the moment using Plone CMS on an old MS Windows 2000 SBS server using the Microsoft file download from the same website http:/plone.org and this works fine.

But installing the Linux version seems much trickier. I'm new at Linux, so the installation documentation found on the http://plone.org website doesn't help me much.

[URL="http://plone.org/documentation/tutorial/installing-plone-3-with-the-unified-installer"]

Is there a software package that handles the installaties of a Unified Installer file for you ? One of the main problems seems to be the handling of permissions to setup the zope+plone environment.

It is possible to download Plone 3.1.2 from the backports but that gives me a setup that is not suitable for the moving of my working Plone environment from Microsoft server to Linux PC.

I would like to write off the old Microsoft server and start using Zope+Plone on an Ubuntu/Kubuntu PC.

---

### Post by Coolcool on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Partyboi2 on 2008-08-28
To install using the Unified installer, make sure you have the build-essential package installed first.
```
sudo apt-get install build-essential
```then change directory to where the downloaded file is. So if it is located on your Desktop in the terminal type
```
cd ~/Desktop
``` then extract the contents with:
```
tar zxf Plone-3.1.5.1-UnifiedInstaller.tar.gz
```Then change into the newly created directory
```
cd Plone-3.1.5.1-UnifiedInstaller
``` then
for a Zeo installation type:
```
sudo ./install.sh zeo
``` or for a standalone installation type:
```
sudo ./install.sh standalone
```

[http://plone.org/documentation/tutorial/installing-plone-3-with-the-unified-installer/running-the-unified-installer](http://plone.org/documentation/tutorial/installing-plone-3-with-the-unified-installer/running-the-unified-installer)

---

### Post by force317 on 2008-09-24
Many thanks for replying to my question. :)

Sorry for my late reply.

Are you a plone user yourself ?

---

### Post by Partyboi2 on 2008-09-24
> **force317 said:**
> Many thanks for replying to my question. :)

Sorry for my late reply.

Are you a plone user yourself ?
No, I don't use  plone.

---

### Post by heartcore on 2008-09-29
I've tried installing it using the unified installer but didn't work. Any ideas how to uninstall it?
thanks in advance

---

### Post by teraploppy on 2010-02-06
Everything looks like it's going to work.. then boom.  I get this error.

[I]Installing Plone 3.3.4 at /usr/local/Plone

Skipping zlib compile and install
Skipping libjpeg compile/install
Skipping readline compile/install
Python found at /usr/local/Plone/Python-2.4/bin/python; Skipping Python install.
Installing PIL
Traceback (most recent call last):
  File "<string>", line 1, in ?
ImportError: No module named _imaging
Python imaging support is missing; something went wrong in the PIL or python build.

Installation has failed.[/I]

i'm using 64bit 9.10 Ubuntu.

---

### Post by astoon on 2010-02-11
Hi,

> **teraploppy said:**
> Everything looks like it's going to work.. then boom.  I get this error.

[I]Installing Plone 3.3.4 at /usr/local/Plone

Skipping zlib compile and install
Skipping libjpeg compile/install
Skipping readline compile/install
Python found at /usr/local/Plone/Python-2.4/bin/python; Skipping Python install.
Installing PIL
Traceback (most recent call last):
  File "<string>", line 1, in ?
ImportError: No module named _imaging
Python imaging support is missing; something went wrong in the PIL or python build.

Installation has failed.[/I]

i'm using 64bit 9.10 Ubuntu.

do you have ~/.pydistutils.cfg file ?
If yes, what is written there?

---

### Post by astoon on 2010-02-12
> **astoon said:**
> Hi,
do you have ~/.pydistutils.cfg file ?
If yes, what is written there?

For example,
if in your ~/.pydistutils.py
```
[install]
prefix=/usr/local/egg
```then it confuses virtualenv engine which used in the Unified Installer, and PIL library will be installed into /usr/local/egg/lib/python2.4/site-packages

So, you need:
comment these lines (temporary), i.e.:
```
#[install]
#prefix=/usr/local/egg
```and then

```
$ cd /usr/local/egg/lib
$ rm -r python2.4
```Note that only PIL library installed in that directory. If there are another packages in <prefix>/lib/python2.4/site-packages then
```
$ rm -r PIL
```find file with *.pth and remove line with PIL from it.

then enjoy...

---

### Post by laboloran on 2010-02-12
Hi,

I have the same problem with the install with the UnifiedInstaller :

[URL="http://ubuntuforums.org/showthread.php?p=8782059#post8782059"]
[/URL] 				 				[I][FONT=Arial][SIZE=2][COLOR=Green]> Everything looks like it's going to  work.. then boom.  I get this error.

[I]> Installing Plone 3.3.4 at /usr/local/Plone

> Skipping zlib compile and install
> Skipping libjpeg compile/install
> Skipping readline compile/install
> Python found at /usr/local/Plone/Python-2.4/bin/python; Skipping Python  install.
> Installing PIL
> Traceback (most recent call last):
  > File "<string>", line 1, in ?
> ImportError: No module named _imaging
> Python imaging support is missing; something went wrong in the PIL or  python build.

> Installation has failed.[/I]

> i'm using 64bit 9.10 Ubuntu.
[I][COLOR=Black]
[/COLOR][/I][/COLOR][/SIZE][/FONT][LEFT][FONT=Arial][SIZE=2][COLOR=Green][COLOR=Black]I 've tried to install Zope and Plone in standalone and Root-less Install[/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=Green][/COLOR][/SIZE][/FONT][/LEFT]
   [/I]

I don't find the file ".pydistutils.cfg" i think that it isn't on my server...

So what can i do ?
Thank you for your help :)

---

### Post by astoon on 2010-02-12
> **laboloran said:**
> Hi,

I have the same problem with the install with the UnifiedInstaller :

[URL="http://ubuntuforums.org/showthread.php?p=8782059#post8782059"]
[/URL] 				 				[I][FONT=Arial][SIZE=2][COLOR=Green]> Everything looks like it's going to  work.. then boom.  I get this error.

[I]> Installing Plone 3.3.4 at /usr/local/Plone

> Skipping zlib compile and install
> Skipping libjpeg compile/install
> Skipping readline compile/install
> Python found at /usr/local/Plone/Python-2.4/bin/python; Skipping Python  install.
> Installing PIL
> Traceback (most recent call last):
  > File "<string>", line 1, in ?
> ImportError: No module named _imaging
> Python imaging support is missing; something went wrong in the PIL or  python build.

> Installation has failed.[/I]

> i'm using 64bit 9.10 Ubuntu.
[I][COLOR=Black]
[/COLOR][/I][/COLOR][/SIZE][/FONT][LEFT][FONT=Arial][SIZE=2][COLOR=Green][COLOR=Black]I 've tried to install Zope and Plone in standalone and Root-less Install[/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=Green][/COLOR][/SIZE][/FONT][/LEFT]
   [/I]

I don't find the file ".pydistutils.cfg" i think that it isn't on my server...

So what can i do ?
Thank you for your help :)
show the output of
```
$ grep "copying build" install.log
```

---

### Post by laboloran on 2010-02-13
Hi Astoon,

Thank you for your help :D !!

/////////////////////////////////////////////////////////////////////////////////////////////


//////////////////////////////////////////////////////////////////////////////////////////

Merci...

---

### Post by astoon on 2010-02-13
Hi Laboloran,
are you sure that you don't have installed system-wide PIL for python2.4 anywhere?
and, for example, system-wide python2.4 as whole?

---

### Post by laboloran on 2010-02-15
>          Hi Laboloran,
are you sure that you don't have installed system-wide PIL for python2.4  anywhere?
and, for example, system-wide python2.4 as whole?     
Hello,

After launching  UnifiedInstaller, I found a directory "python-2.4" in this directory (/  home/user_folder/Plone/Python-2.4) with sub-directories bin,  include, lib, man, and share).
Otherwise on my server, I  find 3 directories in "etc / lib /" which are "python-2.5, python-2.6,  python-3.0. I suppose these 3 versions of python are already installed on my serveur...

Should I install  python-2.4 on my server (in root mode) before running UnifiedInstaller in no root mode with my user login ?

Thank you for your help.

---

### Post by astoon on 2010-02-15
> **laboloran said:**
> After launching  UnifiedInstaller, I found a directory "python-2.4" in this directory (/home/tecendo-riquezas/Plone/Python-2.4) with sub-directories bin,  include, lib, man, and share).
Yes, this is how it should be.> **laboloran said:**
> Shuld I install  python-2.4 on my server (in root mode) before running UnifiedInstaller in no root mode with my user login ?Not, not.

---

### Post by danzilio on 2010-02-15
```
sudo apt-get install libjpeg-dev libfreetype6-dev libfreetype6
```

then

```
sudo ./install.sh [standalone|zeo] 
```

rejoice

---

### Post by laboloran on 2010-02-16
> **danzilio said:**
> ```
sudo apt-get install libjpeg-dev libfreetype6-dev libfreetype6
```then

> I id it in root mode and it was ok...

> **danzilio said:**
> 
```
sudo ./install.sh [standalone|zeo] 
```rejoice


But this mean that i have to run the install UnifiedInstaller in root mode, with my root login and pass ?

And i don't want to install Zope and Plone in root mode...

I don't understand what is the problem.

Thanks for your help...

---

### Post by laboloran on 2010-02-20
Hi, 

I want to install Plone and Zope in root-less mode with my user account.
And i don't understand why it doesn't work.


That is what i 've from Putty :



Thank for help

---

