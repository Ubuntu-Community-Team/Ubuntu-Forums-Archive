---
title: "How to Compile Programs"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by pbanjllay on 2007-04-28
I've been trying to download this Cario thing so I can have GNOME-dock.

Thing is, I don't know how to compile it. 

Can someone tell me an easy way to learn how to compile programs?

I've tried google but every technique seemed impossible to do.

---

### Post by dfreer on 2007-04-28
well, I would first start with a program that is easy to compile, that way you know what a program that is compiling correctly looks like. Generally, if a program requires a library to install (like zsnes requires libgtkglext1), it will need the corresponding -dev package to compile (so to compile zsnes, you will need to install libgtkglext1-dev).
You will need, at the very least, to install the build-essential package: 
```
sudo apt-get install build-essential
```
Generally, most of the time you will use 3 steps to compile a program:
```
./configure
make
sudo make install
```
The make command will actually compile the program, and create a binary in the directory you are currently in. sudo make install will take the binary and install it on your system.

The main thing to look for is for an error when running ./configure. If it runs correctly, it may not say anything like "configure done". It will simply end. If it runs incorrectly, it will often leave some sort of error message at the end. When it doesn't configure correctly, scroll back to the top and look for the VERY first error message. Fix that problem (often it is because you forgot to install a -dev package that is needed), and then run ./configure again.

---

### Post by pbanjllay on 2007-04-28
Everytime I type ./configure, itsays "bash: ./configure: No such file or directory"

---

### Post by pbanjllay on 2007-04-28
Do I have to do something special before doing ./configure?

How can I put this in Synaptic? Isn't there that way?

I do want to learn the terminal way.

---

### Post by fwojciec on 2007-04-28
Not all programs are compiled using the standard ./configure make make install procedure.  When you download a source tarball there is usually an "INSTALL" text file included (sometimes the relevant info is in README file) - you'll find specific instructions for compilation there.

---

### Post by hyperair on 2007-04-28
Those instructions given were very generic. Find the README file in the root directory of the archive, and follow the instructions. If you need help, post the README file as well.

---

### Post by pbanjllay on 2007-04-28
Quick-start build instructions
------------------------------
1) Configure the package:

	./configure

2) Compile it:

	make

3) Install it:

	make install

This final step may require temporary root access (eg. with sudo) if
you don't have write permission to the directory in which cairo will
be installed.

NOTE: If you are working with source from git/cvs rather than from a tar
file, then you should use ./autogen.sh in place of ./configure
anywhere it is mentioned in these instructions.

More detailed build instructions
--------------------------------

1) Configure the package

   The first step in building cairo is to configure the package by
   running the configure script. The configure script attempts to
   automatically detect as much as possible about your system. So,
   you should primarily just accept its defaults by running:

	./configure

   The configure script does accept a large number of options for
   fine-tuning its behavior. See "./configure --help" for a complete
   list. The most commonly used options are discussed here.

   --prefix=PREFIX

	This option specifies the directory under which the software
	should be installed. By default configure will choose a
	directory such as /usr/local. If you would like to install
	cairo to some other location, pass the director to configure
	with the --prefix option. For example:

		./configure --prefix=/opt/cairo

	would install cairo into the /opt/cairo directory. You could
	also choose a prefix directory within your home directory if
	you don't have write access to any system-wide directory.

	After installing into a custom prefix, you will need to set
	some environment variables to allow the software to be
	found. Assuming the /opt/cairo prefix and assuming you are
	using the bash shell, the following environment variables
	should be set:

		PKG_CONFIG_PATH=/opt/cairo/lib/pkgconfig
		LD_LIBRARY_PATH=/opt/cairo/lib
		export PKG_CONFIG_PATH LD_LIBRARY_PATH

	(NOTE: On mac OS X, at least, use DYLD_LIBRARY_PATH in place
	       of LD_LIBRARY_PATH above.)

    --enable-ps
    --enable-pdf
    --enable-quartz
    --enable-atsui
    --enable-xcb
    --enable-glitz
    --enable-beos

	Some of cairo's backends are marked as experimental and will
	not be built by default. If you would like to build and
	experiment with these backends, you will need to pass one of
	the above options to the configure script. You may need to
	have certain libraries installed first as discussed in the
	dependencies section of the README file.

    --disable-xlib
    --disable-win32
    --disable-png
    --disable-freetype

	Cairo's configure script detects the libraries needed to build
	each stable backend, and when it finds them, enables each
	backend. If you would like to override this detection and
	disable a backend, (even when it would be possible to build
	it), use one of the options above to disable the backend.

2) Compile the package:

   This step is very simple. Just:

	make

   The Makefiles included with cairo are designed to work on as many
   different systems as possible.

   When cairo is compiled, you can also run some automated tests of
   cairo with:

	make check

   NOTE: Some versions of X servers will cause the -xlib tests to
   report failures in make check even when cairo is working just
   fine. If you see failures in nothing but -xlib tests, please
   examine the corresponding -xlib-out.png images and compare them to
   the -ref.png reference images (the -xlib-diff.png images might also
   be useful). If the results seem "close enough" please do not report
   a bug against cairo as the "failures" you are seeing are just due
   to subtle variations in X server implementations.

3) Install the package:

   The final step is to install the package with:

	make install

   If you are installing to a system-wide location you may need to
   temporarily acquite root access in order to perform this
   operation. A good way to do this is to use the sudo program:

	sudo make install


Here that's the whole thing.

---

### Post by fwojciec on 2007-04-28
Are you sure that you are in the correct directory when you type ./configure?

---

### Post by pbanjllay on 2007-04-28
How do I know if I'm in the correct directory? How do I get in the correct one?

---

### Post by fwojciec on 2007-04-28
When you open the terminal you are usually located in your home directory.  You have to navigate to the directory where you ununtared the tarball using the cd (change directory) command.  For example, if you saved the tarball to the Desktop and did the "Extract here" command then you'd have to type something like 

cd Desktop
cd [the name of the directory where the untared files are]
and then run the ./compile and so on...

Not to discourage you, but if you need help with changing directories compiling Cairo might be rather difficult for you to do, since I imagine the script is going to complain about missing dependencies - but I might be wrong. 

The only way to learn is to try to do it ;)

---

### Post by pbanjllay on 2007-04-28
Then where can I learn? Can you give me some easy stuff to do?



I want to have Beryl, Wine, Gnome-Dock, and a bunch of other programs on my Linux computer.

---

### Post by fwojciec on 2007-04-28
First thing - Google is your friend, learn to search for solutions to problems, most problems repeat themselves and solutions/guides/howtos are already available on the web.  There is also a Feisty guide webpage which has a good collection of solutions to common problems ([link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty"))    And, of course, keep asking questions here, you will always find someone here willing to help you out ;)

For Beryl - you need to know what card you have, and then try googling for "[name/model of your card], feisty, howto" or something to that effect.  A good place to go to first when it comes to Beryl is beryl-project.org wiki ([link]("http://wiki.beryl-project.org/wiki/Main_Page")) - they have all kinds of guides for different linux distributions/video cards.  You can also try searching these forums for the same info.

Wine is easy: type "sudo aptitude install wine" (without quotation marks naturally) - this is actually taken directly from the Feisty Guide linked above.  Once it is installed you use "wine /[path to the exe file]/[file.exe"]

I don't use Gnome Dock so I can't help you with this, but I'm sure someone else can.

One final thing - when you're following guides and howtos don't just copy/paste but try to think what different commands actually do, and why they are used in this particular way - that way you will very quickly familiarize yourself with how Linux works, and everything will become much easier, trust me. 

I'd help you some more, but I need to go to sleep ;)  Good luck!

---

### Post by hyperair on 2007-04-28
There are plenty of Beryl installation guides around this forum. Why don't you try searching?

---

### Post by Astrodan on 2007-04-30
> **pbanjllay said:**
> Then where can I learn? Can you give me some easy stuff to do?



I want to have Beryl, Wine, Gnome-Dock, and a bunch of other programs on my Linux computer.

As you can see from my meager postings, I'm certainly no expert, but I wouldn't want another beginner to have a hard time compiling.   That said, I think you should check the beginners section some.  Particularly the advice on Beryl.... [http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)
As for  help others have provided on compiling your code, it looks good.

Dan

---

### Post by loathsome on 2007-05-19
*wrong*

---

### Post by loathsome on 2007-05-19
Setting up Beryl on Feisty is incredibly easy. Just run ```
sudo apt-get update && sudo apt-get install beryl beryl-manager
```

Then type [FONT="Impact"]beryl-manager[/FONT] in bash to start.

There's lots, LOTS of pre-compiled programs in the package manager. You can search for specific programs either through synaptic or by running ```
apt-cache search beryl
``` for example.

If you can't find any deb-packages, you can try an rpm-package. You will need to convert it using Alien (available through synaptic). Just run ```
sudo alien package.rpm
``` and Alien will create a perfectly fine deb-package. If you can not find either a deb-package OR an rpm-package, you'll need to compile the source (usually .tar.gz) yourself. This is a bit harder. I recommend using **checkinstall** for this, which is available through synaptic. Checkinstall creates a deb-package from your source, but you will need the required libraries to do this.

Good luck.

---

### Post by hyperair on 2007-05-20
I found checkinstall to be buggy in some cases. Pidgin for example cannot be compiled using checkinstall, as it will conflict with another package. I think it tried to replace the file /usr/bin/ld or something of that sort.

Alien has been fine for me all the while, and I still use it from time to time. Very handy application, I should think. 

As for Beryl, don't forget to install emerald and emerald-themes as well. They provide the window decorations for Beryl.

---

### Post by dfreer on 2007-05-20
> **hyperair said:**
> I found checkinstall to be buggy in some cases. Pidgin for example cannot be compiled using checkinstall, as it will conflict with another package. I think it tried to replace the file /usr/bin/ld or something of that sort.

That is because you are using checkinstall wrong :p You probably just need to change to package name or version number, OR make sure it isn't including files that overwrite another packages files.

checkinstall doens't help with compliing a program, just installing it. You should always use either checkisntall or build the .deb package yourself instead of using make install, because you will have no way of removing the program you install short of finding the files and manually deleting them.

Checkinstall is ok to start with, it serves it's purpose well. But you won't really learn anything with it :)

EDIT: I realize I earlier said use sudo make install, I wasn't thinking correctly evidently :oops:

---

### Post by hyperair on 2007-05-21
Of course I knew that. It's just that the proper way to install a program using checkinstall is:
```

./configure
make
sudo checkinstall

```
Am I right? I'd like to see how you get Pidgin installing fine with checkinstall. You'd have to practically rip the DEB apart yourself afterwards and remove the unnecessary files.

---

### Post by yman on 2007-05-22
instructions for checkinstall are mentioned [here]("http://ubuntuforums.org/showthread.php?t=445651&highlight=checkinstall") as well.

---

### Post by dfreer on 2007-05-22
> **hyperair said:**
> Of course I knew that. It's just that the proper way to install a program using checkinstall is:
```

./configure
make
sudo checkinstall

```
Am I right? I'd like to see how you get Pidgin installing fine with checkinstall. You'd have to practically rip the DEB apart yourself afterwards and remove the unnecessary files.

Yeah, for some reason using the standard checkinstall procedure with pidgin it likes to include those files (I got a list of the ones it complained about on my system at the end of my post), you would either need to modify the config files for pidgin to use checkinstall correctly, checkinstall anyways and afterwards tear apart the .deb like you suggested, or build the package yourself. 
For some reason when I read your earlier post I thought you meant it was replacing another package on the system (e.g. gaim or another pidgin install), in which case it was because you were supplying the wrong values to checkinstall, my mistake. 

but anyways yeah at least now I have pidgin, hmmm. doesn't seem much different from Gaim.

Conflicting files:
/usr/bin/ld
/usr/bin/nm
/usr/bin/strip
/usr/lib/gcc/i486-linux-gnu/4.1.2/crtbeginS.o
/usr/lib/gcc/i486-linux-gnu/4.1.2/collect2
/usr/lib/gcc/i486-linux-gnu/4.1.2/crtendS.o
/usr/lib/libgconf2-4/2/libgconfbackend-xml.so
/usr/bin/gcc

---

