---
title: "Installing XeTeX on Feisty"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by sndrspk on 2007-11-07
I'm having difficulties installing XeTeX on my Feisty kubuntu system.

The XeTeX site only offers binaries for Breezy, which I tried anyway. It gave the following error:

```
san@terribleangel:~/Desktop$ sudo dpkg --install xetex_0.995-1_i386.deb
(Reading database ... 210885 files and directories currently installed.)
Preparing to replace xetex 0.995-1 (using xetex_0.995-1_i386.deb) ...
Unpacking replacement xetex ...
Setting up xetex (0.995-1) ...
no
texhash: Updating /usr/local/share/texmf/ls-R...
texhash: Updating /var/lib/texmf/ls-R-TEXMFMAIN...
texhash: Updating /var/lib/texmf/ls-R-TEXMFDIST-TETEX...
texhash: Updating /var/lib/texmf/ls-R...
texhash: Done.
[: 76: ==: unexpected operator
/var/lib/dpkg/info/xetex.postinst: 76: -p:: not found
/var/lib/dpkg/info/xetex.postinst: 76: -p:: not found
/var/lib/dpkg/info/xetex.postinst: 76: -p:: not found
/var/lib/dpkg/info/xetex.postinst: 76: -p:: not found

san@terribleangel:~/Desktop$
```

So, I tried to build from source. She make-script went fine it seems, but when running the install-script I get a similar error:

```

root@terribleangel:/home/san/xetex-0.996# sh install-xetex
[: 52: ==: unexpected operator
texhash: Updating /usr/local/share/texmf/ls-R...
texhash: Done.
[: 17: ==: unexpected operator
./rebuild-formats: 42: -p:: not found
./rebuild-formats: 42: -p:: not found
./rebuild-formats: 42: -p:: not found
./rebuild-formats: 42: -p:: not found
root@terribleangel:/home/san/xetex-0.996# 
```

I could get rid of the first error, by running it with bash instead of sh (contrary to the instructions on the website):

```
root@terribleangel:/home/san/xetex-0.996# bash install-xetex
texhash: Updating /usr/local/share/texmf/ls-R...
texhash: Done.
[: 17: ==: unexpected operator
./rebuild-formats: 42: -p:: not found
./rebuild-formats: 42: -p:: not found
./rebuild-formats: 42: -p:: not found
./rebuild-formats: 42: -p:: not found
root@terribleangel:/home/san/xetex-0.996# 
```

Still, that seccond error remains. I'm having the feeling it's something really easy, since I'm already into the installation process. I guess I'm still too much a newbie. Who can help me out?

---

### Post by sndrspk on 2007-11-07
By the way, I hope this is the right place for this question. It seemed to be the best category I could find. If not, sorry!

---

### Post by NooneReally on 2007-11-07
why use XeTeX? is it just for the unicode support? I use the standard TeX packages that are in the ubu repo's and have never had any problems with any publications, and I'm pretty sure unicode support has been in there for a while. Looking at the xetex site it would seem that all the functionality has been merged into the standard TeX distributions anyways.

---

### Post by sndrspk on 2007-11-08
The first reason is curiosity. The second reason is the acclaimed support for easy use of opentype en truetype fonts.

---

### Post by rosslaird on 2007-11-12
xetex uses different font tags, so if you create a xetex file you can no longer compile it with tex. In other words, you can't go back. If you want to use opentype fonts etc in latex, your best bet (in my view) is to use John Owens' script:

[http://www.ece.ucdavis.edu/~jowens/code/otfinst/]("http://www.ece.ucdavis.edu/~jowens/code/otfinst/")

This method is not as simple as xetex, but it preserves the latex document structure -- and it works.

Cheers.

Ross

---

### Post by hugmenot on 2007-11-14
I like XeTeX a lot. The argument that you cannot go back is bogus. Just remove the font switching commands then.

The problem you see above is that the so-called shebang in the script points to /bin/sh but the script uses "bashisms". Change it to /bin/bash and it will work.

If you had Gutsy I could send you my XeTeX svn .deb package.

---

### Post by rosslaird on 2007-11-14
> **hugmenot said:**
> I like XeTeX a lot. The argument that you cannot go back is bogus. Just remove the font switching commands then.

Yes, of course you can remove the font commands. But then you have to re-edit the document structure, which may or may not be a pain depending on how you work and how many documents you have. The xetex authors have suggested that people not use xetex for regular documents that do not have need of special alphabets and so on. The fork is very new, and there are issues. Also, the command formats are likely to change in the future (according to xetex developers):

"At present, the Linux implementation
should still be considered a prototype..."

So it might be easier for regular users to use latex for now, unless they feel adventurous. The xetex system will almost surely require that documents created with xetex today will require tweaking to work with xetex a year or two from now.

But, the bleeding edge is always fun.

R.

---

### Post by hugmenot on 2007-11-14
I really  don&#8217;t know what you are on about there ...

```
\defaultfontfeatures{Scale=MatchLowercase,Mapping=tex-text}
\setmainfont[Numbers=OldStyle]{Arno Pro}
\setsansfont{Cronos Pro}
\setmonofont{Inconsolata}

\font\upperarno="Arno Pro:letterspace=3,+cpsp" at 12pt
\font\uppercronos="Cronos Pro:letterspace=3,+cpsp" at 12pt

\setkomafont{disposition}{\itshape}
\setkomafont{section}{\upperarno\MakeUppercase}
%\setkomafont{title}{\bfseries\itshape}   % make this \sffamily for less pompousness

```
Now, this is my fonts section. In which way is it a problem to comment out the XeTeX specific stuff and replace it with LaTeX stuff? This is actually from my header-xlx.tex file. As you might guess there&#8217;s a header.tex too, which is plain LaTeX. In the actual text the markup is done just the same, i.e., semantically.
XeTeX actually makes stuff /a lot/ easier, and a lot more plausible. There&#8217;s only one thing that I miss from pdftex: the microtypographic extensions, that XeTeX doesn&#8217;t have.

BTW, your website needs more visual contrast.

---

### Post by rosslaird on 2007-11-15
Sure, I agree that in some ways xetex is going to make things easier. But let's say you are (like me) a professional writer, and you have many hundreds, perhaps thousands, of documents. Under such conditions consistency is quite important. You'd need new text applications to be backwards-compatible with older standards, and you wouldn't want to go back and revise the structure of all those documents. So, from my point of view, while I am very intrigued by xetex, I don't want to switch quite yet because I have a document system that applies to many documents. I don't want the system to be part xetex and part latex, and while xetex is still a prototype it's a bit premature of me to make the switch. Once either a) xetex gets all the functionality and ease of latex, or b) xetex evolves to the point that it becomes the default application for tex documents, and replaces latex -- I feel that I should stick with the current standard. For me, it's not a matter of changing just a few files.

But having said that, can you send me a basic xetex file so I can test it out?
And, do you have a cvs deb?

Cheers!

Ross

---

### Post by hugmenot on 2007-11-15
Sure thing. [My header]("ftp://ftp.tuebingen.mpg.de/kyb/towolf/header-xlx.tex"), and a [snapshot of current XeTeX trunk (built on Gutsy)]("ftp://ftp.tuebingen.mpg.de/kyb/towolf/xetex_0.997+svn537-1_i386.deb")

A font with optical sizes works best, you have to substitute your own, of course.

---

### Post by rosslaird on 2007-11-17
Thanks for the files.

...But I'm not getting far. I get this, right at xelatex startup:

```
I can't find the format file `xelatex.fmt'!
```

According to various web posts, this has something to do with language.dat and hyphenation; but no fix seems immediately obvious.

Ross

EDIT:

Fix:

```
fmtutil --enablefmt xelatex
```


EDIT 2:

And now... it works!

---

