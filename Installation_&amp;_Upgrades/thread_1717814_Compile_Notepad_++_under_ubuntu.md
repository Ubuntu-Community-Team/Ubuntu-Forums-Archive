---
title: "Compile Notepad ++ under ubuntu?"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by Zaric on 2011-03-30
Hello,
Is it possible to compile Notepad++ (my favorite text-editor:D)
under ubuntu?

I know i can run it in wine, but i would like to run it outside wine.

The source code can you download over here:
[http://download.tuxfamily.org/notepadplus/5.8.7/npp.5.8.7.src.7z](http://download.tuxfamily.org/notepadplus/5.8.7/npp.5.8.7.src.7z)

Some one help me?

---

### Post by kellemes on 2011-03-30
No, you need visual studio for that.

Luckely there are many better alternatives for Linux, or cross-platform.
[http://alternativeto.net/software/notepad-plus-plus/?platform=linux]("http://alternativeto.net/software/notepad-plus-plus/?platform=linux")

I prefer Geany.

---

### Post by Zaric on 2011-03-30
But is it possible with GCC?

---

### Post by kellemes on 2011-03-30
No, it is very much Window-native..
You need vs.
[http://sourceforge.net/apps/mediawiki/notepad-plus/index.php?title=Compiling_Notepad%2B%2B]("http://sourceforge.net/apps/mediawiki/notepad-plus/index.php?title=Compiling_Notepad%2B%2B")

---

### Post by doas777 on 2011-03-30
yep, i'm afraid that NPP is windows only on a far deeper level than compilation. you might be able to get it to compile via mono i suppose, but it would never run on the linux kernel.

I tend to use Geany on ubuntu. has many of the same features I value in n++

---

### Post by Zaric on 2011-03-30
Hmm, thanks for your help


I will try Geany, it looks the same as gPHPedit, but it didn't like gPHPedit.

---

### Post by directhex on 2011-03-30
> **doas777 said:**
> yep, i'm afraid that NPP is windows only on a far deeper level than compilation. you might be able to get it to compile via mono i suppose, but it would never run on the linux kernel.

It's C++. Nothing to do with Mono.

---

### Post by doas777 on 2011-03-31
> **directhex said:**
> It's C++. Nothing to do with Mono.
[Npp's major runtime dependency is MS VC++]("http://sourceforge.net/apps/mediawiki/notepad-plus/index.php?title=Compiling_Notepad%2B%2B"). that means MSVCRT.dll, which mono implements. 
[http://www.mono-project.com/CPlusPlus](http://www.mono-project.com/CPlusPlus)

thanks for playing, but bonus points for the vorlon proverb.

---

### Post by Zaric on 2011-03-31
Hi,

geany is a very good replace for Notepad++
has almost the same functions as Notepad++ (execpt ftp plugin)

---

### Post by directhex on 2011-03-31
> **doas777 said:**
> [Npp's major runtime dependency is MS VC++]("http://sourceforge.net/apps/mediawiki/notepad-plus/index.php?title=Compiling_Notepad%2B%2B"). that means MSVCRT.dll, which mono implements. 
[http://www.mono-project.com/CPlusPlus](http://www.mono-project.com/CPlusPlus)

thanks for playing, but bonus points for the vorlon proverb.

[[img]http://primates.ximian.com/~miguel/pictures/well_actually_trollcat.jpg[/img]](qa.debian.org/developer.php?login=directhex%40apebox.org&comaint=yes)

No, Mono doesn't implement the Microsoft Visual C++ runtime DLL. There's no point, since apps which use it (via C++/CLI) are explicitly not cross-platform other than a tiny never-used subset. Mono has no C++ compiler of any description. At best, as mentioned on the link you posted, there is some embryonic work on making GCC emit CIL. But this is, of course, no use when an app is using Win32 headers and calls in the first place, rather than .NET ones.

So... nope. Sorry.

---

### Post by slooksterpsv on 2011-03-31
This may sound .... well.... but what's so good about Notepad++? I use gedit, bluefish, eclipse and that. Linux has lots of variations that work just like NPP as far as I know. - [http://www.osalt.com/notepad++](http://www.osalt.com/notepad++) 

I need to try Notepad++ and see what the fuss is =P.

Hope that link helps.

---

### Post by pogsquog on 2011-12-23
You can compile win32 applications in linux using winelib.

[http://www.winehq.org/site/winelib](http://www.winehq.org/site/winelib)

---

