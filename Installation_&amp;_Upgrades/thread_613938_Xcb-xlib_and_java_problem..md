---
title: "Xcb-xlib and java problem."
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by warnec on 2007-11-15
Hello. I wanted to use op2m on my ubuntu. java is of course installed.
```

maciek@maciek-ubuntu:~$ javaws http://www.opem.xpg.com.br/OpenP2M.jnlp
maciek@maciek-ubuntu:~$ java: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.

```\

I known it is a known problem:
```

https://bugzilla.novell.com/show_bug.cgi?id=252510

```

```

http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6532373

```

But do not know how to get rid of it. Can you help, please?

---

### Post by DaveRM on 2007-11-15
I had this problem.

I had to remove libx11-xcb1 and downgrade libx11-6.

Java then worked.

Good Luck.

---

### Post by warnec on 2007-11-15
I am not sure if i am allowed to do that. I've installed git version of Compiz Fusion with a script and it asked me whether i want to compile xlib with xlib support and that it is required if i want to have CF from git. So i suppose removing it will cause problems.

---

### Post by DaveRM on 2007-11-15
That was exactly my problem also.

See my earlier post on a similar thread on how I solved the problem.

[http://ubuntuforums.org/showpost.php?p=3732020&postcount=5]("http://ubuntuforums.org/showpost.php?p=3732020&postcount=5")

DaveRM

---

### Post by warnec on 2007-11-16
Ok, thank you. I'll try this as soon as i switch on ubuntu. Now I'm using Win XP, because currently OP2M works only on it, and i want to download Need For Speed: Pro Street from Gmail today :D 
I'm using CF_Installer-Updater_v.3 and i really love it. And can i do this (remove and downgrade these packages) if i already have CF installed, or do i need to reinstall it first?

Another thing: Why did you mention this website?

[http://gitweb.compiz-fusion.org/?p=users/3v1n0/compiz-patches;a=summary](http://gitweb.compiz-fusion.org/?p=users/3v1n0/compiz-patches;a=summary)

I see:
```

2007-08-22
Treviño - ...
Added disable-libx11-xcb-support.patch

```

I understand it is needed for CF to run without xcb-xlib, but i've got no idea how to  run it. I just make 

```

git-clone git://anongit.compiz-fusion.org/users/3v1n0/compiz-patches

```

and i should just compile everything i downloaded?
 Please provide details of how did you EXACTLY made it to work, please.

---

### Post by DaveRM on 2007-11-17
warnec-

I used the script available at the Italian page.
Here is a google translate of the page.

[http://www.google.com/translate?u=http%3A%2F%2Ftelperion.wordpress.com%2F2007%2F10%2F27%2Ffusion-nuovo-script-per-compilazione%2F&langpair=it%7Cen&hl=en&ie=UTF8]("http://www.google.com/translate?u=http%3A%2F%2Ftelperion.wordpress.com%2F2007%2F10%2F27%2Ffusion-nuovo-script-per-compilazione%2F&langpair=it%7Cen&hl=en&ie=UTF8")

This script is NOT interactive.
You MUST fill in the options inside the script using a text editor.

I am on gutsy/gnome.
I made an export of my current CF profile from csm but was not needed.

These are the options I am using.
Many were already set as default.

DISTRO="ubuntu-gutsy"
COMPIZ_MANAGER_DEFAULT_DECORATOR="emerald"
PACKAGES="fusion ccs-gconf"
COMPIZREMOVE="kde fuse kconfig"
CCPLUGINS="atlantis 3d"
PREFIX="/usr/local"
BUILD_FUSION_ICON="YES"
COMPIZ_VERSION="master-noxcb"

Save the script file.
Make a folder in your home directory. I called it cf8.
Move the script to the cf8 folder.
Open a terminal and cd cf8.

Now run the script.
First time.
Check the dependencies:
./makefusion8 packages
Uninstall current installed version.
./makefusion8 uninstall.
get git.
./makefusion8 clone
install
./makefusion8 install

If all went well, give it a try.

Good Luck.

DaveRM

---

