---
title: "Installing Thunderbird from .tar.bz2 file"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by frankbr on 2010-05-15
HI ,
I was wondering how to install thunderbird 3.0 from the file I´ve downloaded
wich is in .tar.bz2 format downloaded from mozilla.com web page.

I could use Apt-get but the package available isn´t in my native language,
only in english .

is there any tutorial to acomplish this task ??

Thanks for helping me out .

---

### Post by abdulrehmanlatif on 2010-05-15
**[SIZE=2]Step  1:  Extract the tarball[/SIZE]**

[SIZE=2][FONT=times new roman]For those new to Linux, *tarball* is  a term commonly used to refer to a file which contains other files. It’s a lot like a ZIP or RAR file in Windows, except that the *tar* program, on its own, does not compress the files. Tar works with a compression program like gzip to actually compress the files, which is why you commonly see two extensions (.tar and .gz). This is sometimes abbreviated to just *.tgz*.[/FONT][/SIZE] [FONT=times new roman][SIZE=2]Fortunately,  we don’t need to run two separate programs to extract the files, we just tell tar to run the files through gzip to decompress. You can use a graphical utility to extract those files by simply double clicking the tarball from your file manager, or you can do it from the command line with:[/SIZE][/FONT]
[SIZE=2][COLOR=#C20CB9]**tar**[/COLOR] [COLOR=#660033]-zxvf[/COLOR] mytarball.tar.gz

[/SIZE][FONT=times new roman][SIZE=2]The  options we gave *tar* are as follows:[/SIZE][/FONT]
 
[LIST]
[*][SIZE=2]-z  to tell tar to run this file through gzip to decompress (use -j for  bzip files)[/SIZE]
[*][SIZE=2]-x to extract the files[/SIZE]
[*][SIZE=2]-v for “verbose”, so we can see a list of the files it’s  extracting[/SIZE]
[*][SIZE=2]-f to tell tar that we’re  working with a file[/SIZE]
[/LIST]
 [FONT=times new roman][SIZE=2]*For  easier unzipping, see the [I]Tips* section at the bottom of this  page [/I][/SIZE][/FONT]
 **[SIZE=2]Configure[/SIZE]**

 [FONT=times new roman][SIZE=2]Once  the files are extracted, open a command terminal and go to the directory where the files have been unzipped. Before we can compile, we need to run the configure script. The job of the configure script is to check your system for all the software necessary to compile the program from source code into a usable binary program. It looks for things like gcc version and other tools needed to build the software. So once you’re in the directory with all the files that were unpacked from the tarball, type in[/SIZE][/FONT]
[SIZE=2][COLOR=#FF33FF]**./configure**[/COLOR]

The most common cause of errors in this step is a missing dependency.
Look closely at any errors you may get to determine what package is
missing.

[/SIZE]**[SIZE=2]Make[/SIZE]**

 [FONT=times new roman][SIZE=2]This  is the real meat of the process – where we compile the source code into a runnable program. This is normally the easiest step, only requiring a single command. If the configure step completed without errors, simply type in[/SIZE][/FONT]
[SIZE=2][COLOR=#C20CB9][B]make

[/B][/COLOR]Technically, your program is now ready to use. Under most
circumstances, however, you’ll want to run one more step so that she
program can be fully installed into the correct locations for it to be
run from anywhere.

[/SIZE]**[SIZE=2]Make  install[/SIZE]**

 [FONT=times new roman][SIZE=2]All  this really does is copy the now-compiled program into the system directories like /usr/bin so that it can be run from any directory without having to specify a path to the files. Since it’s copying to a directory outside your home, you’ll probably need root privileges. If the make step completed without errors, simply run[/SIZE][/FONT]
[FONT=times new roman][SIZE=2][COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**make**[/COLOR] [COLOR=#C20CB9][B]install

[/B][/COLOR]to copy the files.  At this point, you’re all done!  Your new program can be used like any other.
[/SIZE]
[/FONT]
**[SIZE=2]Tips[/SIZE]**

 [FONT=times new roman][SIZE=2]Chances  are, you’ll be compiling from source more than once in your life. In fact, for those who like to use the latest and greatest software, this can be very common. To make it a little easier, open your *.bashrc* file from your home directory, and add the  following aliases to the end:[/SIZE][/FONT]
[FONT=times new roman][SIZE=2][COLOR=#7A0874]**alias**[/COLOR] [COLOR=#007800]ungz[/COLOR]=[COLOR=#FF0000]"tar -zxvf"[/COLOR]
[COLOR=#7A0874]**alias**[/COLOR] [COLOR=#007800]unbz[/COLOR]=[COLOR=#FF0000]"tar -jxvf"[/COLOR]
[COLOR=#7A0874]**alias**[/COLOR] [COLOR=#007800]cmi[/COLOR]=[COLOR=#FF0000]"./configure && make && sudo make install"[/COLOR][/SIZE]
[/FONT]

---

### Post by veli on 2010-05-15
Hi Frankbr,
the easiest way is to right click on the tar.bz2 you got from mozila, then select "extract here". The files will be extracted into a new folder "thunderbird". In this folder there is file "thunderbird". What you have to only do is to create a launcher on the desktop/menu to this file. In doing this thunderbird will be run from your home directory not installes system-wide. The updater will upgrade when new version is released.

---

