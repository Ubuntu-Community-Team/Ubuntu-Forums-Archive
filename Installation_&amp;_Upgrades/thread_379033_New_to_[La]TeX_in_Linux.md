---
title: "New to [La]TeX in Linux"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by Timtro on 2007-03-08
Hello all,

I'm completely new to TeX in a Linux Environment. I started out five years ago using MiKTeX and WinEdt, now I am completely getting away from typesetting in the Windows  Environment.

What are my choices? I have read about TeXLive and teTeX, but I'm unsure which to use? How do I control package installation?  Is there anything like MiKTeX's auto package install?

For document editing, I'm trying out Kile, but I'm open to other options. What do the pros use? For a plain text editor, and most programming I do (usually command-line on a cluster), I use Vim. I know about gVim (I've been using it in Windows), but what are my better options?

Thanks so much!

Cheers,


Tim.

---

### Post by xadder on 2007-03-08
I think texlive is more "modern", but I installed tetex for reasons that I can't quite remember now. I think it was though that tetex was more compatable with latex2rtf and/or latex2html and/or prosper. 

For editing I know many like kile (and it can be run from gnome too, with some easy tweaks which the documentation explains). Many will recommend Lyx, but I have always ended up going back to LaTeX for real work. (Could be my inexperience with Lyx though.) Recently I have been trying vim-latex which has lets me keep using vim as I have done for years. Seems really nice, but the mailing list seems really inactive also.

---

### Post by tkjacobsen on 2007-03-08
> **Timtro said:**
> 
How do I control package installation?  

For document editing, I'm trying out Kile, but I'm open to other options. What do the pros use?

If you install texlive-full (from the repos) don't worry about package installation. It includes _MANY_ packages..

Kile is very good. You can also try texmaker, its made by the guy who started kile and requires less kde libraries, so it should run in gnome.. Also it has a possibility to insert bibtex entries in to a bibtex database -- very handy.

---

### Post by Timtro on 2007-03-08
I have all of the KDE libs installed anyway, so thats not a big deal.

My real choice is teTeX v.s. TeXLive.

If you say TeXLive is more modern, then I'll go with it, especially since it doesn't look like there will be more updates anyhow.

Thanks!

---

### Post by frisket on 2007-03-08
> **Timtro said:**
> I'm completely new to TeX in a Linux Environment. I started out five years ago using MiKTeX and WinEdt, now I am completely getting away from typesetting in the Windows  Environment.

Welcome to the right side of the railroad tracks :-)

> **Timtro said:**
> What are my choices? I have read about TeXLive and teTeX, but I'm unsure which to use? How do I control package installation?  Is there anything like MiKTeX's auto package install?

Yes. The default package on most Linux systems (ie the one you can install from a package manager) is teTeX, but the principal maintainer recently said he won't be doing this any more. It's excellent, but a number of distros (Ubuntu included) have taken it upon themselves to "improve" it by moving files and directories around into unexpected places, but for daily work this is unimportant as the config takes care of it. It only becomes a problem when you want to install non-standard stuff manually because you have to go and find out where to put it.

The alternative is the TeX Users Group's "TeX Collection" DVD, sent to all members (but you can download the ISO from CTAN and burn it). This is a snip to install: read the doc, run the script, and usually just accept the defaults unless you want to select some of the less common stuff.

The MikTeX auto-package-installer has been ported to Linux, but AFAIK it's not part of the standard distro yet. I hear very good reports of it though. 

I have the Ubuntu teTeX on my office desktop and TC2005 on my Edgy laptop and both work fine. 

> **Timtro said:**
> For document editing, I'm trying out Kile, but I'm open to other options. What do the pros use? For a plain text editor, and most programming I do (usually command-line on a cluster), I use Vim. I know about gVim (I've been using it in Windows), but what are my better options?

Kile is excellent. I use GNU Emacs because I grew up using it, and I'm not a great fan of button control when I can use keys, but that's a personal preference. I also use Emacs heavily for other tasks (XML/XSLT and a lot more), so sticking to one interface is simply convenience. I've never used vi[m] except in emergencies because I dislike having to press one button to start typing and another to stop, but again that's a personal matter and I believe it works fine with TeX. I know a lot of math users swear by Xemacs and AUCTeX, but I've never managed to get Xemacs to do anything sensible: it's probably just customisation needed, but the fact that it doesn't work out of the box is enough for me to know to leave it alone. 

The other things you'll need are JabRef for managing your BIBTeX file[s]; GIMP for your graphics (although xv saves better PostScript if you need it); and InkScape for making vector graphics diagrams.

///Peter

---

### Post by yigal.weinstein on 2007-03-09
Well not to have a holy war but I use vim with vim-latexsuite with Gnome.  Doesn't matter as you are using Kile.  But if you have a relatively decent internet connection go for texlive.  It is what is being developed tetex is going to be anymore.  texlive has more packages and while Kile will help you out with reverse and forward searching there are packages that tetex may not have that texlive will.  When I say texlive I mean all of it.

The only problem you may have is certain rediculous dependency problems.  Tetex has been around for quite some time and certain programs will be built to "depend" on tetex.  This is _NOT_ really the case and texlive can be substituted in almost every case - I am sure there are exceptions but I really can't think of one.  

If you want for instance to install mediawiki, wikipedia webdesign, with its lovely wiki-math stuff this depends on tetex but texlive works anyways and who, as a personal user is really going to want to install mediawiki (actually I did as a PIM didn't work so well.)  

Best, 

P.S. install texlive.

---

### Post by Timtro on 2007-03-09
Brilliant. Thank you all so much.

I did find it tremendously easy to get things working with Kile and TeXLive. Now I've got to go about figuring out how to install my personal .sty packages :) But I'm sure there is plenty of wonderful documentation for that.

Thanks again to all of you for your wonderful advice.

Kind regards,


Tim.

---

### Post by yigal.weinstein on 2007-03-09
A simple way of installing personal .sty files is to move them to 
```

sudo mv "your".sty /usr/share/texmf-texlive/tex/latex/base/
sudo texhash

```

thats it, your done.

---

### Post by ahmatti on 2007-03-16
I just found the Miktex package manager for adding .sty packages. Works great for me! A really easy way to add packages. I also use Texlive, which works much better for me than tetex. I even got finnish hyphenation working! :) 

Howto for installing: [https://help.ubuntu.com/community/MiktexPackageManager](https://help.ubuntu.com/community/MiktexPackageManager)

Oh yeah, remember to run  $sudo mktexlsr  after adding packages.

---

### Post by cscherf on 2007-03-20
It looks like many of you like texlive. Could one of the texlive fans tell me how to get latex2rtf, latex2html, and rtf2latex working?

Thanks,
Chris

---

### Post by venik212 on 2007-04-27
I installed Texlive on Kubuntu, but when I use either Kile or Lyx I get empty output files (when I try to get pdflatex).  This worked fine under Ubuntu/Gnome.  What am I doing wrong?

---

### Post by Maratonda on 2008-05-14
> **ahmatti said:**
> I just found the Miktex package manager for adding .sty packages. Works great for me! A really easy way to add packages. I also use Texlive, which works much better for me than tetex. I even got finnish hyphenation working! :) 

Howto for installing: [https://help.ubuntu.com/community/MiktexPackageManager](https://help.ubuntu.com/community/MiktexPackageManager)

Oh yeah, remember to run  $sudo mktexlsr  after adding packages.

Why is the link in the wiki not working anymore? :confused:

---

