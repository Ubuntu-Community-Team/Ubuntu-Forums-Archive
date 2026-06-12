---
title: "LaTeX, Texmaker installation and setup"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-02-09
This is a little complex; but here goes...

**System info**: Ubuntu 9.10
**Texmaker**: 1.9.9
**TexLive 2009** (important)
**Relevant environment variables**:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/texlive/2009/bin/i386-linux
MANPATH=/usr/local/texlive/2009/texmf/doc/man
INFOPATH=/usr/local/texlive/2009/texmf/doc/info

1. I initially used the Synaptic Package Manger to install LaTeX; but, then realized that a 2007 vers. was installed.

2. I then uninstalled completely vers. 2007 with all dependencies.

3. I downloaded from CTAN a rather large file with TeXLive 2009 (that contained the latest release of LaTex). I followed the installation instructions and indeed I now have TeXLive on my system and I am able to use it. The Synaptic Package Manager does not see that TexLive 2009 is installed!

Finally, to the problem...

All of the files and directories for LaTeX are now located in:

  /usr/local/texlive

All the *.cls and *.sty files that were included in TeXLive 2009 are in:

  /usr/local/texlive/2009/texmf-dist/tex/latex

Questions:
1) How can I setup my system so that** all files associated with TexLive 2009** are updated automatically?

I have some *.cls and *.sty files that I have written and are needed by some of the *.tex files that I compile with Texmaker. However, **Texmaker can only find these *.cls or *.sty files if they are in the same directory as the *.tex file that needs it**. I would like very much to have all of my custom *.cls and *.sty files in: 

  /virgil/LaTeX_cls_sty_files

so that they can be shared by different *.tex files that may need them.

2) How can I configure Texmaker or setup the system so that Texmaker will find the *.sty and *.cls files in this directory?

3) How can I configure Texmaker or setup the system so that Texmaker does not require that I have my *.bib files in the same directory as my *.tex file?


Thank you, 

--V
PS. Please keep in mind that I am very new to Ubuntu ;)

---

