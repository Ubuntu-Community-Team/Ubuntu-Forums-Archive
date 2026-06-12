---
title: "Wheres the Kernel located?"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by Brando569 on 2005-09-21
im trying to figure out how to use bootsplash with ubuntu, i think after alot of searching/reading i might actually have the info i need. im REALLY confused on how to actually install bootsplash support, then how to install the actual bootsplash. right now im using the default grub loader, but ill change over to lilo if i need to. so far this is what i understand: (im trying to follow all the stuff on bootsplash.org as close as possible)

1.patch and compile kernel. this part seemed easy enough, it said check to see if you kernel is  /usr/src/linux i went there and the only thing in the /usr/src folder is a folder called RPM. i would of linked the kernel to that location, but theres one slight problem, i dont know where it is!  :-? 

2. i just read the other stuff and im pretty much lost. this stuff is really confusing to me, ive been using linux on and off for about 2 or so years. now im thinking of making ubuntu my main os, and only using windows when i have to. 

i just found this site( [http://wiki.sourcemage.org/index.php?page=HOWTO-Bootsplash](http://wiki.sourcemage.org/index.php?page=HOWTO-Bootsplash) ) while searching and it sounded pretty easy as opposed to the directions listed on bootsplash.org but theres one problem, i dont have the program "cast" and it isnt in any of the repositories. 

id like to get one of these working but dont know how:

[http://www.kde-look.org/content/show.php?content=15539](http://www.kde-look.org/content/show.php?content=15539) 

[http://www.kde-look.org/content/show.php?content=28828](http://www.kde-look.org/content/show.php?content=28828)

[http://www.kde-look.org/content/show.php?content=27889](http://www.kde-look.org/content/show.php?content=27889)

does anyone know of any other sites that have alot of bootsplash themes? as you can tell im a complete noob at this. any help will be greatly appriciated
thanks
brando

---

### Post by bsussman on 2005-09-21
the kernel(s) live(s) in  /boot, usually.

Be careful in there.  alterations to /boot are a superb way to render your system senseless.  I have been there... :)


Clearly I made it back but...

---

### Post by mlomker on 2005-09-21
Compiling a kernel isn't quite as trivial as it sounds, then.  Here are the [instructions](http://ubuntuforums.org/showpost.php?p=361253&postcount=10) for downloading the kernel source.

---

### Post by Brando569 on 2005-09-21
im not able to patch the kernel, the command patch -p1 <patch location> doesnt do anything (yes i did replace  <patch location> with the location of the patch) i just type it in the terminal as root and it just sat there and didnt do anything. any1 have any idea whats wrong?

---

### Post by Xian on 2005-09-21
It might help if you post the actual output of the commands.
It is difficult to tell from just your description where the problem resides.

$ cd /usr/src/linux
$ sudo patch -p1 <path_to_patch>

---

### Post by Brando569 on 2005-09-21
thats the thing there is no output! i wouldnt be a problem that linux is a link to /usr/src/linux-source-2.6.10 right? also i upgraded the defualt kernel from i386 to i686

---

### Post by mlomker on 2005-09-22
[QUOTE=Brando569]im not able to patch the kernel, the command patch -p1 <patch location> doesnt do anything (yes i did replace  <patch location> with the location of the patch) i just type it in the terminal as root and it just sat there and didnt do anything. any1 have any idea whats wrong?[/QUOTE]

Patches are designed to be applied to a very specific version of the source code and it is possible that it cannot be applied to Ubuntu's kernel source.  Ubuntu already applies a lot of its own patches.

---

### Post by Brando569 on 2005-09-22
hmm ok, so would it be better update my kernel to 2.6.13 and then try to install the patch or should i just try and find out if ubuntu already implemented the patch? also performance wise would it be better to stick with the ubuntu optimized kernel 2.6.10 or try out the new vanilla source 2.6.13, probably would be better to stick with 2.6.10 right?

---

### Post by mlomker on 2005-09-22
[QUOTE=Brando569]hmm ok, so would it be better update my kernel to 2.6.13 and then try to install the patch or should i just try and find out if ubuntu already implemented the patch? also performance wise would it be better to stick with the ubuntu optimized kernel 2.6.10 or try out the new vanilla source 2.6.13, probably would be better to stick with 2.6.10 right?[/QUOTE]

I'm not sure how you'd discover what patches are applied.  I have the *if it isn't broke then don't fix it mentality*.  

I could never get a custom 2.6.10 kernel to boot on my laptop.  I got a 2.6.13 to compile but I ran into other problems installing software, etc, because the kernel was too new.  I'm back to using the stock kernel...it's good enough for most people.

---

### Post by Brando569 on 2005-09-22
to clarify what i meant by "...find out if ubuntu already implemented it" was do everything else in the walkthrough except for the patch and see if it works

---

