---
title: "how to make .deb from source or binary??"
date: 2008-06-11
forum: Jordan Team
---

### Post by maq21 on 2008-06-11
hi all
im new here and i wnana know how to make .deb from source code or binary code

---

### Post by Jad on 2008-06-14
Hello, 
you can watch MOTU videos on Ubuntu Developer channel on Youtube [http://www.youtube.com/watch?v=VyEl3w7SFK4](http://www.youtube.com/watch?v=VyEl3w7SFK4)

and read MOTU fine documentations [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

---

### Post by emad_ramlawi on 2009-03-09
download ALIEN it can convert tar.gz and other formats to DEB

---

### Post by elitenoobboy on 2009-03-10
What do I do if the source is in .tar.bz2 format? I get an unknown package error if I try that. Does it really have to be converted?

---

### Post by wildman4god on 2009-04-14
> **elitenoobboy said:**
> What do I do if the source is in .tar.bz2 format? I get an unknown package error if I try that. Does it really have to be converted?


Just unpack it in nautilus by right-clicking it and selecting extract, much easier than command line.

---

### Post by sundar_ima on 2009-05-13
> **elitenoobboy said:**
> What do I do if the source is in .tar.bz2 format? I get an unknown package error if I try that. Does it really have to be converted? 

To make Debian package you should have build-essential and checkinstall packages installed in your system. If you dont have both then fire up synoptic package manager (system-->>administration-->>synoptic packa...) search for above packages, mark it and install(apply). i also assume that you do not have any dependency issue with the source package.

Say your source package name is "abcd"  

1. move abcd to home folder (places -->> home folder)
2. Extract abcd (right click on abcd and select option extract here)
3. Open terminal (Application -->> Accessories -->> Termial)
4. Type following commands

[B]cd abcd
./configure
make
sudo checkinstall[/B]

checkinstall is the command creates debian package for you. at the end,  terminal will show you where the .deb package is located.

Hope this will work for you...

---

### Post by YellowRatBastard on 2009-05-18
Hi there. I guess the question is: why would you? there are tens of thousands of debian -and ubuntu, packages for pretty much anything you could imagine or require. Since you are a self-professed nooby, creating .deb packages should be the least of your concerns.

Some of the reasons for making your own .deb package are architecture-specific performance optimization and memory usage optimization... are you telling me you've already covered everything there is to know and are ready to tackle the above mentioned? 

On the other hand, please consider the following... packages you create are not supported by the community, you'll have a hell of a time trying to update or upgrade those packages and removal of such packages is rarely clean. 

I suggest you try to accumulate as much knowledge as possible and please, the number one advice i always give: Use Ubuntu/Linux and nothing but ubuntu/linux everywhere. And i mean everywhere... on your home PC, laptop, server if you have one and at work. Total immersion is still the best way to learn.

Good luck

---

### Post by elitenoobboy on 2009-05-18
> **YellowRatBastard said:**
> Hi there. I guess the question is: why would you? there are tens of thousands of debian -and ubuntu, packages for pretty much anything you could imagine or require. Since you are a self-professed nooby, creating .deb packages should be the least of your concerns.

The reason I need to is that there are a large number of programs out there that I want/need and are not in a repository or in deb format, or that are not up to date and/or buggy.

> Some of the reasons for making your own .deb package are architecture-specific performance optimization and memory usage optimization... are you telling me you've already covered everything there is to know and are ready to tackle the above mentioned? 

So building a deb yourself makes it run faster on that specific system?

> On the other hand, please consider the following... packages you create are not supported by the community, you'll have a hell of a time trying to update or upgrade those packages and removal of such packages is rarely clean. 

Which is why I generally avoid it if possible. That and getting the build environment and config dependencies correct can be a bitch. As for it's removal not being clean, that is easily solved by just reinstalling the system then restoring just the users data. Upgrading to a new distro version instead of installing from scratch has proven to be quite buggy for me in the past. Systems tend to pick up cruft as time goes along anyway.

---

### Post by specialk1st on 2010-03-19
> **sundar_ima said:**
> To make Debian package you should have build-essential and checkinstall packages installed in your system. If you dont have both then fire up synoptic package manager (system-->>administration-->>synoptic packa...) search for above packages, mark it and install(apply). i also assume that you do not have any dependency issue with the source package.

Say your source package name is "abcd"  

1. move abcd to home folder (places -->> home folder)
2. Extract abcd (right click on abcd and select option extract here)
3. Open terminal (Application -->> Accessories -->> Termial)
4. Type following commands

[B]cd abcd
./configure
make
sudo checkinstall[/B]

checkinstall is the command creates debian package for you. at the end,  terminal will show you where the .deb package is located.

Hope this will work for you...

Hi, thank you very much for the step-by-step explanation.

I am having this problem...

When I type: "./configure"
I get this error: "bash: ./configure: No such file or directory"

Am I missing something?  What should I do now?

Thank you in advance for your help.

---

### Post by celldweller1591 on 2010-08-15
Type this & then run the above :
*sudo apt-get install build-essential checkinstall *

---

### Post by apandada1 on 2012-12-18
I installed build-essential & checkinstall but having the same problem after typing**  ./configure** 

I am getting this 

ubuntu@ubuntu:~/stormcloud-master$ ./configure
bash: ./configure: No such file or directory

---

### Post by rushikesh988 on 2013-01-13
> **apandada1 said:**
> I installed build-essential & checkinstall but having the same problem after typing**  ./configure** 

I am getting this 

ubuntu@ubuntu:~/stormcloud-master$ ./configure
bash: ./configure: No such file or directory
I am not the expert of ubuntu but as per my guess
there is always a configure.sh  file in source code .. if you are getting that error means you have not created that..
normally configure.sh contains some bash setting that needed for installing the software.

---

### Post by MG&amp;TL on 2013-01-13
> **rushikesh988 said:**
> 
there is always a configure.sh  file in source code .. if you are getting that error means you have not created that..
normally configure.sh contains some bash setting that needed for installing the software.

Guess is wrong, sorry. Some bits of software which use GNU autoconf (mercifully, it seems, a dying breed), have a "configure" script either supplied, or generated by "autogen.sh"

As for stormcloud, which it appears is what the OP is trying to build, is completely weird. It's not like anything I've seen before, I think it has something to do with Node.js. 

@OP: Either use checkinstall (which I believe works for some projects only), or install using the install rule of the build system (just copy files, not always a good idea), or work out how to run the program without installing it.

---

