---
title: "Install RAR Archiver"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by wlankatt on 2005-11-26
How do I do that?
I've tried typing: "sudo apt-get install rar" but it didn't work. :(

---

### Post by matthew on 2005-11-26
First, make sure you have the [extra repositories enabled]("http://www.psychocats.net/linux/sources.php") and then:

sudo apt-get install unrar-nonfree

---

### Post by wlankatt on 2005-11-26
Doesn't work. :/

---

### Post by lcg on 2005-11-26
[QUOTE=wlankatt]Doesn't work. :/[/QUOTE]
I might be going out on a limb here, but I think that people would actually be able to try and help you if you posted a little more details about how it "doesn't work". ;)

Regards,
Lars

---

### Post by Orangecrush on 2005-11-26
im getting this error. 
>     Package unrar-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package unrar-nonfree has no installation candidate
      

just tr4ying to share the wealth

---

### Post by matthew on 2005-11-26
[quote=wlankatt]Doesn't work. :/[/quote] Did you click the link and follow the directions before you tried?? Here is the link again for your convenience: [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

I'm assuming you must have had problems with the installation of the unrar-nonfree package, but you were a little vague. If you are having problems using the package please say so.

Also, consider that some rar archives require passwords. Did you try to require a password-enabled rar archive without using the password??

The more information you give the more specific our help can be. I'm just shooting in the dark here.

---

### Post by wlankatt on 2005-11-26
Yay, I get nearly the same error. I get this:
Package unrar-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source.
E: Package unrar-nonfree has no installation candidate

---

### Post by matthew on 2005-11-26
Okay, you posted your most recent response as I composed my last one.

Try the free version...I have no clue why the nonfree version didn't install for you. Works fine for me.

sudo apt-get install unrar-free

The only difference is that this one seems to be a bit more picky about the rar archive it is opening. Hopefully it will work for you.

---

### Post by matthew on 2005-11-26
Another note: unrar-free is in the universe repositories
unrar-nonfree is in the multiverse repositories

Look again at the page I linked to and see if you have all the repositories enabled or post the contents of your /etc/apt/sources.list here and I'll take a look at it.

---

### Post by wlankatt on 2005-11-26
I managed to install it, but I can't find it or use it. :???:

---

### Post by Xian on 2005-11-26
Open a terminal then issue this command:

$ rar --help

```
Usage:     rar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  a             Add files to archive
  c             Add archive comment
  cf            Add files comment
  cw            Write archive comment to file
  d             Delete files from archive
  e             Extract files to current directory
  f             Freshen files in archive
<snip>
```

---

### Post by matthew on 2005-11-26
[quote=wlankatt]I managed to install it, but I can't find it or use it. :???:[/quote]
There are two ways to use it.

Graphical:
Open Nautilus (the default file browser in Ubuntu)
Go to the directory where the rar archive is located
Click on it

Command line:
Open a terminal
Type```
unrar e <filename>.rar
```

---

### Post by maxper on 2005-11-28
[QUOTE=matthew]Okay, you posted your most recent response as I composed my last one.

Try the free version...I have no clue why the nonfree version didn't install for you. Works fine for me.

sudo apt-get install unrar-free

[/QUOTE]

sorry wrong typing

---

### Post by maxper on 2005-11-28
[QUOTE=matthew]There are two ways to use it.

Graphical:
Open Nautilus (the default file browser in Ubuntu)
Go to the directory where the rar archive is located
Click on it

Command line:
Open a terminal
Type```
unrar e <filename>.rar
```[/QUOTE]

it did not work: 
bash: unrar: command not found

why?

---

### Post by matthew on 2005-11-28
[quote=maxper]it did not work: 
bash: unrar: command not found

why?[/quote]It seems that unrar is not actually installed so the command is not being found.

What method did you use to try to install it? 
--Synaptic? Command line and apt-get?

I have to recommend reinstalling the unrar utility.

EDIT: Before you try that, I remembered the free version of unrar has a different syntax. Try ```
rar e <filename>.rar
```as recommended by Xian above

---

### Post by maxper on 2005-11-29
[QUOTE=matthew]It seems that unrar is not actually installed so the command is not being found.

What method did you use to try to install it? 
--Command line and apt-get?


EDIT: Before you try that, I remembered the free version of unrar has a different syntax. Try ```
rar e <filename>.rar
```as recommended by Xian above[/QUOTE]

command line and apt-get install
packet seems to be installed, but trying all different syntaxes, no way! :(

---

### Post by jagguars on 2005-12-15
ahj, had a similar problem with the rar files.
first thing that i got was that the non free version of unrar is needed by ark when i tried to decompress it with that program. so i installed and it worked. the clue is unrar did also not write itself anywhere but ark checked that it was installed and used it methods.
i still had problems with password protected rar files. i also installed rar but still the same problem. now i use "file-roller". nice gnome programe and decompresses every rar file with password and without, but not that nice as ark. 

so it's up to you what u need

---

### Post by psusi on 2005-12-15
Just thought I would mention that you might want to take a look at 7-zip.  Either visit [www.7-zip.org](www.7-zip.org) or there is a package you can install in the repositories.  

In some cases it is faster than rar, it can get MUCH better compression, and it is free and open source.  

For instance, I once compressed a directory tree of source and object code I was working on with winzip, winrar, and 7zip.  Winzip was the fastest, and winrar and 7zip were more or less the same speed.  Uncompressed the directory tree was around 30 MB.  Winzip got it down to 2.5 MB.  Winrar got it down to 2.1 MB ( though took a lot longer ).  7zip compressed it down to 720 KB.

---

### Post by Hootman on 2005-12-15
Worked  for me when i ran the command

---

### Post by Natsuki on 2005-12-23
Thanks this work for me ;)

---

