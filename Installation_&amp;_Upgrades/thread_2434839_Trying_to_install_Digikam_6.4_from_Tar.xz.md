---
title: "Trying to install Digikam 6.4 from Tar.xz"
date: 2020-01-11
forum: Installation &amp; Upgrades
---

### Post by Jorhel on 2020-01-11
Hi,
I have Digicam 5.9 installed from the depository, however a few things seem to have gone missing the export plugins for one and when I try to import from the camera I can't do it via digikam find the camera but can't communicate with it. I can live with it ,but I thought I'll try to update did via apt update and via synaptic who told me my version is up to date. Then I found out that there is a 6.4 version so I tried to install via the tar.xz . I have extracted it in the usr/share directory (where my other digikam lives) but when I try the next step
```
./configure
```
I get
 ```
bash: ./configure: No such file or directory
```
I have had a good look around on the net but the advice always seem to be 
```
[COLOR=#000000]./configure
make
sudo -s
make install 
```
I have read on multiple posts that it is better to install from the repositories, but if I want to take the risk how do I go about it?
Thanks[/COLOR]

---

### Post by SeijiSensei on 2020-01-11
The sequence beginning with ./configure is designed to install from source. I suspect you have a binary.  Try putting the .xz file in the directory /usr/local/bin then extracting the files.

Also that sequence turns out not to be what you want to do if you do want to install digikam from source.  See [https://www.digikam.org/download/git/](https://www.digikam.org/download/git/)

You'd probably need to run first "sudo apt install build-essential; sudo apt-get build-dep digikam" to install the needed compilers and source dependencies.

Did you install libkf5kipi* from the repository as well? These are valuable helper files that are shared among KDE apps.

---

### Post by CatKiller on 2020-01-11
> **Jorhel said:**
>  Then I found out that there is a 6.4 version so I tried to install via the tar.xz .  

Just... don't. 

You can install the 6.4 snap through the Software Centre, or there's an appimage if you're desperate to download some random single file off some website, or you can look for a PPA, or you can use git. Downloading a single archive of the source code that can't be easily updated is an *awful* option. 

> I have extracted it in the usr/share directory (where my other digikam lives) 

That might be where the version from the package manager is *installed* to, but that's got nothing to do with where you'd want to compile the code from. You're just making life harder for yourself by putting it anywhere but in your Home folder. 

> but when I try the next step
```
./configure
``` 

That isn't the next step, because
> ```
bash: ./configure: No such file or directory
``` 

> I have read on multiple posts that it is better to install from the repositories, but if I want to take the risk how do I go about it?

It is. 

You'd start by reading [the instructions](https://www.digikam.org/download/git/).

---

### Post by TheFu on 2020-01-11
Do not mix package installed software with software that you manually build and install.  Manually built software should end up in /usr/local/  But not until after it is built.

Either built it under your HOME somewhere or use /tmp/something/ ... completely up to you.

I haven't pulled the source code down, yet.
In the download package, there should be a README or INSTALL file which explains how to build it. Follow those instructions using your normal userid, never root, until after everything is built correctly, without errors or warnings.  There are likely to be lots of dependencies which you'll need to manually solve. The how-to install section should explain those.

BTW, the version of Ubuntu will matter for some of those dependencies, which is why using a PPA or snap/flatpak/appimage install is usually recommended for non-developers.

Let me get the source.  I suspect you really want DigiKam, not Digicam.  Yes?  Getting the wrong name will cause all sorts of problems.
[https://launchpad.net/ubuntu/+source/digikam](https://launchpad.net/ubuntu/+source/digikam) has v5.9 for 19.10.  Since only v5.6 is available for 18.04, I suspect there are core libraries which are incompatible with the newer release.  Looks like an AppImage is their new way to release  [https://download.kde.org/stable/digikam/6.4.0/](https://download.kde.org/stable/digikam/6.4.0/)

The SOURCE is 324 MB !!!  Source code should be 10MB or less.  This is not a trivial project to build.
There is a *README.DEVEL* file which says to read the *The API documentation*. This is a non-trivial project to build.  Heck, to read the documentation, you have to install 2 packages and build all the docs.  

I was a professional C++ developer for over a decade and this is too much effort for me to go farther.  Use the appimage dude.

If you aren't afraid yet, [https://www.digikam.org/api/](https://www.digikam.org/api/) will make you afraid.  This is not for casual developers with a year of C++ from school.  This is a real commitment to build. I'd guess about 3 days for me to figure out.

I really love that they have this in one of the bootstrap scripts:
```
# WARNING: Make sure you understand what this does before using it!
```

---

### Post by Jorhel on 2020-01-14
Thanks,
I have installed the snap version could have started there but I had searched specifically for 6.4 which return no file found. Searching for Digikam return 2 answers, one of them is the 6.4 snap. Good to know for future use.

---

### Post by Jorhel on 2020-01-14
> **TheFu said:**
> 

The SOURCE is 324 MB !!!  Source code should be 10MB or less.  This is not a trivial project to build.
There is a *README.DEVEL* file which says to read the *The API documentation*. This is a non-trivial project to build.  Heck, to read the documentation, you have to install 2 packages and build all the docs.  

I was a professional C++ developer for over a decade and this is too much effort for me to go farther.  Use the appimage dude.

If you aren't afraid yet, [https://www.digikam.org/api/](https://www.digikam.org/api/) will make you afraid.  This is not for casual developers with a year of C++ from school.  This is a real commitment to build. I'd guess about 3 days for me to figure out.

I really love that they have this in one of the bootstrap scripts:
```
# WARNING: Make sure you understand what this does before using it!
```
Thanks a lot this is well beyond my understanding....
Love your Warning too.

---

