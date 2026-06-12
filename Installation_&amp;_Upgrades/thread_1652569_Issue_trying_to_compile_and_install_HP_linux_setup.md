---
title: "Issue trying to compile and install HP linux setup"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by Yamipirogoeth on 2010-12-25
I am trying to install the drivers and setup for my HP scanner/printer using the tar.gz file I downloaded from SourceForge.

I was following the steps on this website [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) to compile and install the tar.gz file however when I get to the bottom of step 3 I can't seem to figure out what the problem is that I need to fix, this is what I'm showing in the terminal after running ./configure:

checking for jpeg_set_defaults in -ljpeg... no
configure: error: "cannot find libjpeg support"

Those are the last two lines before I get my prompt again.

I can't figure out how to get past this to get to the "make" command in order to finish the compile and then the install.

Any thoughts that could help me finish this please?

---

### Post by realzippy on 2010-12-25
...I do not know.Until somebody knows,I would suggest to try installing
libjpeg8 and libjpeg8-dev (and maybe libjpeg-progs) before compiling.
Simply type in terminal:

```
sudo apt-get install libjpeg8 libjpeg8-dev libjpeg-progs
```

And welcome to UF!


..if it does not work,you have a link to your downloaded tar.gz package?

---

### Post by Yamipirogoeth on 2010-12-25
Thanks realzippy, that actually got me past that issue with the libjpeg but then I got another error:

Again, last two lines after running ./configure
  	 	 	 	p { margin-bottom: 0.08in; }  checking for CRYPTO_free in -lcrypto... no  
 configure: error: cannot find net-snmp support (or --disable-network-build)


 This is the site where I got the tar.gz from [http://sourceforge.net/projects/hplip/files/hplip/3.10.9/](http://sourceforge.net/projects/hplip/files/hplip/3.10.9/)

---

### Post by realzippy on 2010-12-26
So you might also need this:

```
sudo apt-get install python-dev libcupsys2-dev libcupsimage2-dev xsane

```


...install the stuff and try again  ;-)

---

### Post by realzippy on 2010-12-26
...just saw that HP also offers a .run file for your driver,so you do not have to compile manually.If compiling still not works,try this:

```
sudo apt-get install python-dev libcupsys2-dev libcupsimage2-dev xsane
```
(if you have not already done)


```

mkdir hplipdriver          *#creates a directory named "hplipdriver"*
cd hplipdriver             *#goes to this directory*
wget http://sourceforge.net/projects/hplip/files/hplip/3.10.9/hplip-3.10.9.run     *#downloads the .run file to this directory*
chmod +x hplip-3.10.9.run       *#makes the downloaded file executable*
sh hplip-3.10.9.run          *# runs the .run file*
```

(line by line;use "TAB" key to autocomplete your terminal input)

---

### Post by Yamipirogoeth on 2010-12-27
...figures there's an easier way to do it and I didn't realize that.

Well, the manual compile still wasn't working so I tried all the commands for the .run file.

After running the .run file, it seems I'm missing some dependencies:

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 5 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: python-devel (Python devel - Python development files)
warning: This installer cannot install 'python-devel' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

Just so its made aware, I'm using 10.10 and I do have python v2.6 and v3.1 installed according to the software center. So I'm not sure where I need to find the python files that are missing to continue the install

---

### Post by realzippy on 2010-12-27
Have you not run
```
sudo apt-get install [COLOR="SeaGreen"]python-dev[/COLOR] libcupsys2-dev libcupsimage2-dev xsane
```
before?This command installs python-dev...?


Edit:

If you have run above command (without error output?) and .run file still not working,you could try also:

```
sudo apt-get install python2.6-dev
```


BTW,why not using the hplip version (3.10.6) from the repos?

---

### Post by Yamipirogoeth on 2010-12-28
Yeah, I installed all those dependencies but it still insisted that they were not installed. I actually went about installing each one separately to see if that would help. So far so good...granted I had to go back two steps for the cups-image dependency by installing libjpeg-dev and then libtiff4-dev first. But, after doing that I ran the .run file and so far it is still 'Running "Make" ' at the moment.

It looks like it complete the build and installed hplip 3.10.9 for me finally.

Thanks for your help realzippy.

also, I honestly have no clue how to access or find anything in the repos. Would that have made this any easier and how would I have to look through them in the future?

---

### Post by realzippy on 2010-12-28
You can browse/search programs/drivers in synaptic with the "search" option..

```
sudo apt-get install hplip
```

would have installed the 3.10.6 version of the driver you have compiled.

Great you made it finally.Hope the driver does work...;)

---

