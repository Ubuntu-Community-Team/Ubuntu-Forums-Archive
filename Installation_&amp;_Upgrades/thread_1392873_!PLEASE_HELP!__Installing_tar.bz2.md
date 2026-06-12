---
title: "!PLEASE HELP!  Installing tar.bz2?"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by jdgregson on 2010-01-28
Okay, so I'm new to Linux. So far I kind of like it, but I'm very frustrated about trying to install tar.bz2 files. I've found tutorial after tutorial on the web, which all say to do it a little different, but they all have one thing in common, it never works. The problem usually comes when I get to the "make" command. So far what I've learned to do is this, tar -xjvf example-0.0.3.tar.bz2 > ./configure > make > make install. The problem seems to be when I type "make" it says "make: *** no targets specified and no makefile found. stop." I've tried it several different ways and they all come to the same/similar result. Can someone give me a complete, detailed, from the time I get the tar.bz2 to the time it's finished installing and ready do use, step by step, key stroke by key stroke, click by click tutorial on how to install a tar.bz2 in Ubuntu? This is important for me to learn, because almost everything for Linux comes like this.

---

### Post by snowpine on 2010-01-28
tar.bz2 is simply a type of archive (like .zip in Windows). Literally anything could be inside that archive.

Can you be more specific about which application you're trying to install? Most apps you could possibly need are easy to install using the Ubuntu Software Center.

---

### Post by r_s on 2010-01-28
well, tar.bz2 is just a method of compressing a folder , you can extract its content easily , and then the installation would depend on the files that are present in this folder and it's just not tar.bz2 that is followed there are plenty of these formats.. you need to give a little more detail.

---

### Post by darkod on 2010-01-28
I don't know what are you trying to install but tar.bz2 is compressed archive like zip. I would suggest splitting the process. Ubuntu has Archive Manager by default. Just right clcik any tar.bz2 file and you should see option Open with Archive Manager.
When it opens it, there is Extract button whch will also ask you for destination where to unpack.
I'm not sure but I think both tar and bz2 are different archives so you might need to extract once, then again (extract the extracted file).
If you end up with .deb you can install that too with right click and select Install with Package Manager (or similar, don't remember the exact text).
If it's a bunch of files you would usually have to go into the folder where they were finally extracted, and run:
sudo make (or what ever the instructions said)

Also, did you install build-essential so you can compile? Before doing make you need to install that package (it will install connected packages automatically):
sudo apt-get install build-essential

---

### Post by jdgregson on 2010-01-28
Well I want to use the Ubuntu center, but I installed Ubuntu on an old laptop (2000's era), which uses a 10/100 PC card. But unfortunately, I don't have the dongle for it, so I can't connect to the internet. :( So I have to use a thumb drive to move files over. 

Okay, right now I'm trying to install audacity

I open terminal and change to the proper directory, 

type "tar -xjvf a*.bz2" and hit enter

change to the newly created directory and type "ls" to see whats there,

the current files are as follows: 

audacity.dox, configure, images, LICENSE.txt, Makefile.in, src, config.guess, configure.in, Info.plist.h, locale, nyquist, win, config.log, dox2-src, install-sh, m4, plug-ins, config.sub, help, lib-src, mac, README.txt

To install this particular file, how should I proceed?

---

### Post by r_s on 2010-01-28
well there is a README which suggests, you read it properly , however I guess , that install.sh might be the bash script you are looking for.

---

### Post by darkod on 2010-01-28
> **r_s said:**
> well there is a README which suggests, you read it properly , however I guess , that install.sh might be the bash script you are looking for.

If that's true, and asuming they already made the file executable, all you need is to run:
./install.sh

Yes, that is correct, just type ./ in front of the file name.

---

### Post by jdgregson on 2010-01-28
> **darkod said:**
> If that's true, and asuming they already made the file executable, all you need is to run:
./install.sh

Yes, that is correct, just type ./ in front of the file name.

"install: no input file specified"

---

### Post by darkod on 2010-01-28
> **jdgregson said:**
> "install: no input file specified"

OK then, you have to depend on what the readme.txt says. We are just guessing here otherwise. :)

---

### Post by jdgregson on 2010-01-28
> **darkod said:**
> OK then, you have to depend on what the readme.txt says. We are just guessing here otherwise. :)

Well that stinks because the readme says to get other pieces of software that i need to get straight from the Ubuntu computer, which can't go on the internet. Half the stuff won't even work on my ancient laptop because it has a architecture that I can't find any .deb's for, i686 I think. Dose anyone know where to find stuff for that architecture? All I can find is i383.

---

### Post by snowpine on 2010-01-28
I think you'll have a much easier time installing software if you get your networking fixed first. I'd suggest starting a new thread on your networking problems, good luck! :)

---

### Post by mhgsys on 2010-01-28
If I remember correctly ;

You're suppose to run ./configure first to install audacity from tar.bz2

(edit: Nevermind my first comment, I see I did not read your first post very well)

Anyway this should help you 

[http://wiki.audacityteam.org/index.php?title=CompilingAudacityForBeginners](http://wiki.audacityteam.org/index.php?title=CompilingAudacityForBeginners)

And I agree with snowpine; The easiest way to install Audacity would require some internet connection > 
You can just apt-get it.

```
sudo apt-get install audacity
```

---

