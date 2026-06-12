---
title: "Texlive dependenties on ubuntu"
date: 2018-02-04
forum: Installation &amp; Upgrades
---

### Post by vimallr on 2018-02-04
Hi,

I was installing DataDog on my ubuntu machine and i came across Texlive Dependencies for which i ran this cmd [COLOR=#111111][FONT=Consolas]aptitude install texlive-latex-base [/FONT][/COLOR]and got reply as "resolve these dependencies by hand [N/+/-/_/: /?] " .
In the options i selected N and it got aborted.

How can go about please help me


Vimal

---

### Post by QIII on 2018-02-04
Hello!

Would you please copy and paste the entirety of the commands executed and the responses in code tags?  A complete record would be much more helpful.

To enclose text in code tags, highlight text and click the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

When using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by vimallr on 2018-02-05
HI,

When i installed DATADOG application i got the "TEXLIVE" dependencies as shown in below.

**You might want to run 'apt-get -f install' to correct these:**
**The following packages have unmet dependencies:**
**context : Depends: texlive-base (>= 2013) but 2009-15 is to be installed**
**Depends: lmodern (>= 2.004.4) but 2.004.1-3.1ubuntu1 is to be installed**
**Recommends: fonts-freefont but it is not installable**
**latex-cjk-common : Depends: libkpathsea6 but it is not going to be installed**
**ibedataserverui-3.0-1 : Depends: libebook-1.2-12 (>= 3.2.3) but it is not installable**
**luatex : Depends: libkpathsea6 but it is not going to be installed**
**texlive-base : Depends: texlive-doc-base (>= 2009-1) but it is not installable**
**Depends: texlive-common (>= 2009-1) but it is not installable**
**texlive-bibtex-extra : Depends: texlive-base (>= 2013.20130512) but 2009-15 is to be installed**
**Depends: texlive-binaries (>= 2013.20130512)**
**texlive-binaries : Depends: texlive-common (>= 2009) but it is not installable**
**texlive-doc-bg : Depends: texlive-lang-european (>= 2013.20130512) but it is not going to be installed**
**texlive-doc-en : Depends: texlive-base (>= 2013.20130512) but 2009-15 is to be installed**
**Depends: texlive-lang-english (>= 2013.20130512) but it is not going to be installed**
**texlive-doc-fi : Depends: texlive-lang-european (>= 2013.20130512) but it is not going to be installed**
**texlive-doc-ja : Depends: texlive-lang-cjk (>= 2013.20130512) but it is not going to be installed**
**texlive-doc-ko : Depends: texlive-lang-cjk (>= 2013.20130512) but it is not going to be instal led**
**texlive-doc-nl : Depends: texlive-lang-european (>= 2013.20130512) but it is not going to be installed**
**texlive-doc-si : Depends: texlive-lang-european (>= 2013.20130512) but it is not going to be installed**
**texlive-doc-tr : Depends: texlive-lang-european (>= 2013.20130512) but it is not going to be installed**
[COLOR=#212121][FONT=wf_segoe-ui_normal][B][COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR][/B][SIZE=3][COLOR=#000000][FONT=Calibri]Below are the commands that i ran and same out put i received as shown above . 

[/FONT][/COLOR][B]"add-apt-repository ppa:jonathonf/texlive"
"apt update && sudo apt install texlive-full"[/B]
[COLOR=#000000][FONT=Calibri]

Executed below command  [/FONT][/COLOR][COLOR=#000000][FONT=Calibri]to over come the texlive dependencies problem and the out put i received shown below.

[/FONT][/COLOR]***"aptitude install texlive-latex-base"***[COLOR=#000000][FONT=Calibri]

Output i received as  
[/FONT][/COLOR]***"resolve these dependencies by hand [N/+/-/_/: /?] " *. **[/SIZE]

[COLOR=#000000]
[SIZE=3]From the above options i selected . Later i tried with  
[/SIZE][/COLOR][SIZE=3][COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR][/SIZE][/FONT][/COLOR][SIZE=3][COLOR=#000000][FONT=wf_segoe-ui_normal]**"N" -  the installation was aborted.**
[/FONT][/COLOR][COLOR=#212121][FONT=wf_segoe-ui_normal][COLOR=#000000][FONT=Calibri]tried with 
[/FONT][/COLOR][/FONT][/COLOR]**[COLOR=#000000][FONT=wf_segoe-ui_normal]"+" option and i got reply as [/FONT][/COLOR]**[/SIZE][COLOR=#212121][FONT=wf_segoe-ui_normal][COLOR=#000000][FONT=Calibri]
 [/FONT][/COLOR]
[/FONT][/COLOR][SIZE=3][B][COLOR=#000000][FONT=Calibri][COLOR=#ff0000]*The following ESSENTIAL packages will be BROKEN by this action:*[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][COLOR=#ff0000]* perl-base : Conflicts: perl-base:i386 but 5.18.2-2ubuntu1.3 is to be installed.*[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][COLOR=#ff0000]* perl-base:i386 : Conflicts: perl-base but 5.18.2-2ubuntu1.1 is installed and it is kept back.*[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri][COLOR=#ff0000]*WARNING: Performing this action will probably cause your system to break!*[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][COLOR=#ff0000]*         Do NOT continue unless you know EXACTLY what you are doing!*[/COLOR][/FONT][/COLOR]
[/B][COLOR=#000000][FONT=Calibri][COLOR=#ff0000][I]**To continue, type the phrase "I am aware that this is a very bad idea":**

[/I][/COLOR]Please help me .

Vimal[/FONT][/COLOR]
[/SIZE][COLOR=#212121][FONT=wf_segoe-ui_normal]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by QIII on 2018-02-05
Rather than breaking things up and trying to explain, simply cut and paste the entire exchange from beginning to end -- the commands themselves and all following messages.  That will provide context and make sure that any important diagnostic information is not missed.  Also, please use code tags as I described above.  That preserves formatting and makes you post much easier to read and understand.  Please also use the default font and color.

---

### Post by vimallr on 2018-02-06
Here You go Error output while installing DATADOG in Ubuntu14.04

> [COLOR=#000000][FONT=Calibri]You might want to run 'apt-get -f install' to correct these:[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]The following packages have unmet dependencies:[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] context : Depends: texlive-base (>= 2013) but 2009-15 is to be installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]           Depends: lmodern (>= 2.004.4) but 2.004.1-3.1ubuntu1 is to be installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]           Recommends: fonts-freefont but it is not installable[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] latex-cjk-common : Depends: libkpathsea6 but it is not going to be installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] libedataserverui-3.0-1 : Depends: libebook-1.2-12 (>= 3.2.3) but it is not installable[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] luatex : Depends: libkpathsea6 but it is not going to be installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri] texlive-base : Depends: texlive-doc-base (>= 2009-1) but it is not installable[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]                Depends: texlive-common (>= 2009-1) but it is not installable[/FONT][/COLOR]
[SIZE=2][/SIZE][COLOR=#000000][FONT=Calibri]
> 
# aptitude install texlive-latex-base
The following packages are RECOMMENDED but will NOT be installed:
  texlive-latex-base-doc
18 packages upgraded, 89 newly installed, 0 to remove and 1064 not upgraded.
Need to get 74.9 MB/93.7 MB of archives. After unpacking 174 MB will be used.
The following packages have unmet dependencies:
 texlive-lang-czechslovak : Depends: texlive-base (>= 2013.20130512) but 2009-15 is installed and it is kept back.
 libidn11-dev : Depends: libidn11 (= 1.28-1ubuntu2.1) but 1.28-1ubuntu2.2 is to be installed.
 texlive-humanities-doc : Depends: texlive-base (>= 2013.20130512) but 2009-15 is installed and it is kept back.
 texlive-lang-french : Depends: texlive-base (>= 2013.20130512) but 2009-15 is installed and it is kept back.
 ubuntuone-client-gnome : Depends: libebook-1.2-12 (>= 3.2.3) but it is not installable.
 libijs-0.35 : Conflicts: libijs-0.35:i386 but 0.35-8build1 is to be installed.
 libijs-0.35:i386 : Conflicts: libijs-0.35 but 0.35-8build1 is installed.
 texlive-lang-polish : Depends: texlive-base (>= 2013.20130512) but 2009-15 is installed and it is kept back.
texlive-xetex : Depends: texlive-base (>= 2013.20130512) but 2009-15 is installed and it is kept back.
 libtasn1-6-dev : Depends: libtasn1-6 (= 3.4-3ubuntu0.5) but 3.4-3ubuntu0.6 is to be installed.
 texlive-bibtex-extra : Depends: texlive-base (>= 2013.20130512) but 2009-15 is installed and it is kept back.
Resolve these dependencies by hand? [N/+/-/_/:/?] +
The following ESSENTIAL packages will be BROKEN by this action:
 perl-base : Conflicts: perl-base:i386 but 5.18.2-2ubuntu1.3 is to be installed.
 perl-base:i386 : Conflicts: perl-base but 5.18.2-2ubuntu1.1 is installed and it is kept back.


WARNING: Performing this action will probably cause your system to break!
         Do NOT continue unless you know EXACTLY what you are doing!
To continue, type the phrase "I am aware that this is a very bad idea":




[/FONT][/COLOR]

Vimal

---

