---
title: "Simple Alternatives to ./configure?"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by Dr.FrankenStein_ on 2011-01-29
Hi, What happens when a tar.gz/tar.bz2 has no configure file after extracting?  Is there other alt. to creating a makefile?  If somebody could walk me through this it would really pay off after all the google'in i"ve done......Thank u ALL:-k

---

### Post by SaintDanBert on 2011-01-29
I'll help if I can, but it might be easier with more information.
I spent a lot of years rolling c-source into executables by hand.

Which tar-ball (tar.gz or .tgz file) are you trying to "build"?
Which programming language are you dealing with?

I recently fetched a tarball that only contained the source files (dot-C and dot-H) and Makefile.

A makefile consists of **targets** and **dependents** and **actions**. Make mostly works like this:
[list=1]
[*]read the Makefile
[*]find the first target
[*]if it is current, locate the next target
[*]if the target is older than its dependents, 
then use the actions to create the target
[/list]
This process continues until all targets are current. Since any target can be dependent on other targets (a library depends on object files that depend on source files that depend on header files) there is a lot of processing between reading the Makefile and running all of the actions.

For lots of years, we created **Makefile** by hand and there are many books and articles available that teach the details of make-file writing. It seems like arcane magic until you learn some things. The 'make' utility has been around for over 30 years and is very powerful.

There are many articles about creating your own 'configure' script, but that approximates writing a script that writes a script that writes ... that writes ... (ugh)  The role of the configure script involves scanning the workstation for libraries and utilities that are available.

---

### Post by Dr.FrankenStein_ on 2011-01-29
Ok,there is other programs that ive tried in the past from source that seem to install better than the one's in the repos   i prefer to go for the latest version if possible..... i dont see a problem w/ that. Also alot of other time that this has happened to me, sometimes there will be install.sh that u have to use  [./install.sh] to create the makefile   What if there is nothing? With the vuse tar.bz2 the README says to run Azureus- did that 5x..  Basically i would like to know for future reference

---

### Post by SaintDanBert on 2011-01-29
> **Dr.FrankenStein_ said:**
> 
...
What if there is nothing? With the vuse tar.bz2 the README says to run Azureus- did that 5x..  Basically i would like to know for future reference

Are you talking about the bit-torrent client application? I find v4.3.0.6-1 in the Ubuntu Lucid (v10.04 LTS) repository (Synaptic).
I'll grab the tar ball and see what I have.

====================
UPDATE:
    I looked at the download page for "Azureus" or "Vuze" torrent client.
The source code is "jar" files.  **Jar** files are Java language files
instead of C-language or similar.  Java applications use different conventions 
than other languages.
    Since this application is Java-based, you will need a working Java Runtime Environment (JRE) installed to your workstation. You may have one already.
If the 'azureus' script does not find the required java parts, you should see
error messages.
====================

If you have the source code files but do not have a Makefile, you must either create the Makefile by hand, or use a tool that will help you create that file. **Make** is true magic and takes some learning for real proficiency. I recommend that you locate Makefiles from some simple applications and use those as a framework.

When I create a Makefile from scratch, I usually start with the large chunks and then add details as needed.
[list]
[*]the executable program depends on header files and libraries
[*]system libraries get listed in a defined macro
[*]each of my own libraries gets its own target
[*]a library depends on the several header and object files that supply the library contents.
[*]create a target "clean" that removes anything that could be created (compiler output, &c) by the Makefile
(This does not depend on anything.)
[*]create a target "install" that moves files from the folders where they were built into places where they will live for routine use.
(This depends on a successful executable build.)
[*]create a target "verify" that runs some simple test(s) that provide the end user with an installation verification -- the installed program lives where it is supposed to and does something it is supposed to do.
(This depends on a successful install and some test data.)
[/list]

The action lines of your Makefile use the compiler and linker and librarian along with other commands and utilities to create the build artifacts. Defined macros hold compiler and linker and other command line options. Setting these options properly is a large part of what it means to do programming.

Merci,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-01-30
FOLLOW-UP:  If you really want to know about **configure** files

I found this information about "auto tools"
[http://sourceware.org/autobook/](http://sourceware.org/autobook/)

A simplistic view of "auto tools" goes something like this.
Auto tools help by scanning the workstation at hand and generating files of information. One can then use that information as input into Makefiles and other build scripts. Another feature involves scanning of the various source code files and recording all of the dependencies.

Bonne chance,
~~~ 0;-Dan

---

### Post by Dr.FrankenStein_ on 2011-02-02
Thank you for the help/info  i'll refer myself back to this thread in the future and i saved that link. And your extremely correct.. I would definatley need a working java enviroment and its all boiling down to that! i recently posted a new thread and not having very much luck :( wait till you see the output on this one...I'm lost  its like my whole /jvm dir is gone. IDK  Hope Sombody tracks the fix down or can walk me through it.     [www.linuxquestions.org/questions/linux-newbie-8/stubborn-java-installation-860143/]("http://www.linuxquestions.org/questions/linux-newbie-8/stubborn-java-installation-860143/")

---

