---
title: "Latex not working after upgrade to 14.04"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by Jonathon_Peterson on 2014-08-18
I upgraded from 12.04 to 14.04 today. Now, I cannot compile my .tex files with latex or pdflatex. Whenever I try to compile anything I get the following message.
 ```
This is pdfTeX, Version 3.1415926-2.5-1.40.14 (TeX Live 2013/Debian)
 restricted \write18 enabled.
---! /var/lib/texmf/web2c/pdftex/latex.fmt doesn't match pdftex.pool
(Fatal format file error; I'm stymied)

```

I'm not sure what to do about this. When I was doing the upgrade today, I did get an error message that (if I remember correctly) said that the package tex-common didn't install. However, when I check in synaptic package manager that package is installed. I'm as stymied (and so is my latex compiler apparently). Anybody got any ideas on what to do?

---

### Post by Jonathon_Peterson on 2014-08-19
I did some searching and I found this information on what I thought might be the problem 
[https://wiki.archlinux.org/index.php/TeX_Live_FAQ#Q:_I_just_updated_texlive_and_it_stopped_working.](https://wiki.archlinux.org/index.php/TeX_Live_FAQ#Q:_I_just_updated_texlive_and_it_stopped_working.)
I tried recompiling the *.fmt files manually using the command ```
fmtutil --all
``` as was suggested, but that didn't seem to work. I also tried moving the latex.fmt file to a new directory and then using the command ```
sudo fmtutil-sys --all
``` to regenerate the .fmt file but that didn't work either. Finally, I put the latex.fmt file back and tried the command ```
sudo fmtutil-sys --refresh
``` to try refreshing all the .fmt files. None of these options have worked. I'm still getting the same error message as before.

---

### Post by steeldriver on 2014-08-19
Not sure if it's relevant, but there seem to be a few people having success by renaming / deleting the user's ~/.texmf-var

[http://tex.stackexchange.com/questions/2191/tex-live-error-on-ubuntu-10-04-pdflatex-fmt-doesnt-match-pdftex-pool](http://tex.stackexchange.com/questions/2191/tex-live-error-on-ubuntu-10-04-pdflatex-fmt-doesnt-match-pdftex-pool)

---

### Post by Jonathon_Peterson on 2014-08-19
Thanks, but that didn't seem to work either. I'm starting to suspect that I need to uninstall and then reinstall texlive. What is the best way to do this to make sure I get a clean uninstall and then reinstall? I'm assuming the best would be to use Synaptic Package Manager to do a "complete removal" of anything with texlive in it. However, I noticed that that will even uninstall things like Kile, which I don't really want to remove if I don't have to. Is there a better way to do this?

---

### Post by Jonathon_Peterson on 2014-08-19
Thanks, but that didn't seem to work either. I'm starting to suspect that I need to uninstall and then reinstall texlive. What is the best way to do this to make sure I get a clean uninstall and then reinstall? I'm assuming the best would be to use Synaptic Package Manager to do a "complete removal" of anything with texlive in it. However, I noticed that that will even uninstall things like Kile, which I don't really want to remove if I don't have to. Is there a better way to do this?

---

### Post by Jonathon_Peterson on 2014-08-20
I ended up doing a complete removal and then reinstall of essentially all of texlive on my computer. That seemed to fix things! Not the most elegant solution but it worked.

---

