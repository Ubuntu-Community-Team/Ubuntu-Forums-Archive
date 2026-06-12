---
title: "installation of Miktex"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by mahsa2010 on 2010-05-11
Hello Everyone,
I have installed texlive on ubuntu 8.10.
Now I want to use xepersian package, so I have to install Miktex as these instructions:
[https://help.ubuntu.com/community/MiktexPackageManager](https://help.ubuntu.com/community/MiktexPackageManager)
but when I "make" it , it errors as this:
####################################################
In file included from CommandLine.cpp:24:
internal.h:2085: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2085: error: expected ';' before '<' token
internal.h:2086: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2086: error: expected ';' before '<' token
internal.h:2087: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2087: error: expected ';' before '<' token
internal.h:2088: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2088: error: expected ';' before '<' token
internal.h:2089: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2089: error: expected ';' before '<' token
internal.h:2090: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2090: error: expected ';' before '<' token
internal.h:2091: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2091: error: expected ';' before '<' token
internal.h:2092: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2092: error: expected ';' before '<' token
internal.h:2093: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2093: error: expected ';' before '<' token
internal.h:2094: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2094: error: expected ';' before '<' token
internal.h:2095: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2095: error: expected ';' before '<' token
internal.h:2096: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2096: error: expected ';' before '<' token
internal.h:2097: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2097: error: expected ';' before '<' token
internal.h:2098: error: ISO C++ forbids declaration of 'auto_ptr' with no type
internal.h:2098: error: expected ';' before '<' token
make[3]: *** [libmiktex_core_la-CommandLine.lo] Error 1
make[3]: Leaving directory `/home/mahsa/SOFTWARE-Source/Miktex/miktex-tools-2.5.2398-beta-14/Libraries/MiKTeX/Core'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mahsa/SOFTWARE-Source/Miktex/miktex-tools-2.5.2398-beta-14/Libraries/MiKTeX/Core'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mahsa/SOFTWARE-Source/Miktex/miktex-tools-2.5.2398-beta-14'
make: *** [all] Error 2
################################
I have also tried installing it by other ways, such as getting the .deb file:
[http://tug.ctan.org/tex-archive/systems/win32/miktex/setup/](http://tug.ctan.org/tex-archive/systems/win32/miktex/setup/)
But it still errors!
I don't know what to do!!
Would you please help me solve this?
Mahsa

---

### Post by dino99 on 2010-05-11
seems to be a cpp release problem, have to know which one to use.

[http://packages.ubuntu.com/intrepid/devel/](http://packages.ubuntu.com/intrepid/devel/)

check if your system is updated and run: sudo apt-get install -f , then: sudo dpkg --configure -a

[http://groups.google.com/group/farsilatex/browse_thread/thread/a75d3945a0f0f91c](http://groups.google.com/group/farsilatex/browse_thread/thread/a75d3945a0f0f91c)

[http://promberger.info/linux/2008/06/15/miktex-package-manager-for-ubuntu-linux/#comments](http://promberger.info/linux/2008/06/15/miktex-package-manager-for-ubuntu-linux/#comments)

---

### Post by sanderd17 on 2010-05-11
Why do you need MikTeX? MikTeX is good for Windows cause they don't have a package manager but in Ubuntu, you can use the default package manager.

If you go to System->administration->Synaptic and you do a search for xepersian, you see it's in the Ubuntu texlive-xetex package. So all you have to do is install that package.

If you have to install LaTeX, Just go to the software center, install an editor (kile, texmaker ...) and the LaTeX distribution will come with it.

Hope it helped.

---

### Post by mahsa2010 on 2010-05-15
Thank you very much. I was going wrong way.
I just needed to install texlive.
 I emphasis to others that have this problem that just install texlive2009, if they want to install xepersian. And then some fonts.
This is the link I used:
[http://fa.parsilatex.wikia.com/wiki/&#1585;&#1575;&#1607;&#1606;&#1605;&#1575;&#1740;_&#1606;&#1589;&#1576;_&#1586;&#1740;*&#1662;&#1585;&#1588;&#1740;&#1606;](http://fa.parsilatex.wikia.com/wiki/&#1585;&#1575;&#1607;&#1606;&#1605;&#1575;&#1740;_&#1606;&#1589;&#1576;_&#1586;&#1740;*&#1662;&#1585;&#1588;&#1740;&#1606;)

---

### Post by thelastblack on 2011-10-19
> **mahsa2010 said:**
> Thank you very much. I was going wrong way.
I just needed to install texlive.
 I emphasis to others that have this problem that just install texlive2009, if they want to install xepersian. And then some fonts.
This is the link I used:
[http://fa.parsilatex.wikia.com/wiki/&#1585;&#1575;&#1607;&#1606;&#1605;&#1575;&#1740;_&#1606;&#1589;&#1576;_&#1586;&#1740;*&#1662;&#1585;&#1588;&#1740;&#1606;]("http://fa.parsilatex.wikia.com/wiki/%D8%B1%D8%A7%D9%87%D9%86%D9%85%D8%A7%DB%8C_%D9%86%D8%B5%D8%A8_%D8%B2%DB%8C*%D9%BE%D8%B1%D8%B4%DB%8C%D9%86")

the link is dead. no content.

hey
i have a problem with xepersian.
i installed everything(texlive) from USC in ubuntu 11.10 but when i use:
```
\usepackage{xepersian}
\settextfont{Arial}
\setlatintextfont{Arial}
```
in a document(compiling is made using texmaker) i get error about not finding fonts.
Arial is a very generic font and sure is installed in my system.
i dont have this problem in miktex in windows and this compiles very nice in windows.
plz help, i'm in rush.
thx in advance

---

### Post by sanderd17 on 2011-10-19
Arial is one of the fonts owned by microsoft. I believe you can install them from the software center, do a search for "microsoft font".

---

### Post by thelastblack on 2011-10-20
hey, i found the solution. it wasnt problem with fonts but with my "texmaker"
arial is installed in my system, i have it in libreoffice
i just had to change "QuickBuild" command to 
```

xelatex -interaction=nonstopmode %.tex

```
and it works! gr8!
thx for ur attention

---

