---
title: "Installing extension tar.bz2, no .deb package"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by enbaeza on 2010-03-17
Installing tar.bz2 extensions, how does one go about doing that?  
 

 I have read the earlier postings and they do not seem to be helpful at all. I am a big time newbie using Ubuntu or any other version of Linux. I have used Synaptic Package Manager (System &#8594; Administration &#8594; Synaptic Package Manager) when using .deb packages or .deb extensions. That is easy, the process is automated when using Synaptic Package Manager.
 

 How about when the software application (app) is not in a package form (.deb extension)? If we pick an app out of the air like a program, take for example Thunderbird from Mozilla.com, the file extension is tar.bz2. I have saved it on my Download folder and it has been extracted inside the Download folder with Archive Manager or with whatever but the case is that it has been extracted. We have read the useless readme.txt file, no useful information other than thanks for downloading the software and hope for happiness and don't forget to give thanks in form of a donation. It's not what it says but lets pretend that it does say that. Readme.txt file provides no useful information as to going about installing the program.
 

 The million dollar question, is whats next? How do we install this program that we have taken as an example? Thunderbird was just taken to be used as an example, it can be any program, software application (app), or whatever the case, we don't have the .deb package and the only thing we have to install is tar.bz2 file. I am fully aware that the extension tar.bz2 is a compressed file that needs to be extracted, for those that do not know that. Lets assume that the file has been extracted like mentioned above and we have the terminal open (Applications &#8594; Accessories &#8594; Terminal).

How do we go about installing a file extension with tar.bz2 that does not contain a useful readme.txt file, a configuration file, or a .deb package enclosed? Who can help us?

---

### Post by tom4everitt on 2010-03-17
Its actually easier than you might think:

First cd into the directory:

cd Thunderbird

Then launch thunderbird by typing:

./thunderbird

This will work for most programs of the type you mentioned. If you want to be able to launch it from the applications menu, you need to add a menu item for it. For that you will need the full path of the file you launched it with, in your case:
/home/<youruser>/Downloads/Thunderbird/thunderbird

Go to System->Preferences->Main menu. 
Choose the subsection you want to add it to (probably internet). 
Click 'add item' to the left.
Fill in name Thunderbird, and the full path as command. 

Before doing this you might want to move the thunderbird folder somewhere else to not fill the downloads folder with applications.



For thunderbird downloading the .bz2 is not necessary, instead open Applications->Ubuntu software center. Search for thunderbird and you will find it. (Then it will automatically add itself to the right applications menu.)

---

### Post by enbaeza on 2010-03-17
Thank you for your insightful reply, and quick response. Like I said before, Thunderbird was just taken to be used as an example, it could have been any program.

---

### Post by tom4everitt on 2010-03-17
Yeah, I sort of figured. I see a lot of people having this sort of problem, someone shot write a blog post thats number one on google when googling for 'install application/program/whatever ubuntu' :)

---

### Post by srs5694 on 2010-03-17
Although tom4everitt's reply works in some cases, it doesn't in others. The truth is that tarballs (files with .tgz, .tbz, .tar.gz, .tar.bz2, or similar extensions) can contain *anything* -- binaries (machine-understandable program files) for x86, binaries for x86-64, binaries for PowerPC, scripts, source code, documentation, fonts, music files, word processing files, etc. Since you're asking about a tarball associated with a program, chances are it's got binaries, scripts, or source files. If you happened to download binaries for your architecture (or one you can run; for instance, you can usually run x86 binaries on x86-64 systems) or a script, then you can run it directly, as tom4everitt suggests, although you may need to hunt for the executable program files. To install the program, you'll need to copy it to somewhere on your path (/usr/local/bin works, but it's technically better to create a directory under /opt and adjust your path appropriately), and you may need or want to copy libraries, documentation, or other files, too, but that will all be very specific to the package you downloaded.

Source code frequently comes in the form of tarballs. With source code, there's no one-size-fits-all solution, although there will usually be a script called "configure" that you must run. Then you type "make" to build the software, and sometimes "make install" to install it. Small packages sometimes omit the configure script and may not support "make install". Some source packages do things a bit differently; for instance, you might type "make config" or something similar to configure the software. There's usually a file called README or INSTALL that describes the details.

Overall, your best bet is to read any documentation you find in the tarball. If the documentation is missing or unclear, then take your best guess. If you can't figure it out, e-mail the package's author.

---

### Post by enbaeza on 2010-03-17
Thank you for your input, very much appreciated and taking the time to reply.

Does anyone else have constructive input to add? Remember we all learn from each other, someone adds this or that and it works for some people, and JoeBob added his two cents and it worked for MariaJuliana. Everyone's input is greatly appreciated! :popcorn:

---

### Post by enbaeza on 2010-03-18
Anyone? :KS

---

### Post by oldos2er on 2010-03-18
srs5694 said it all--tar.gz or .bz2 archives can contain anything.

---

