---
title: "LaTex failure"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Alabamian on 2008-02-01
I've got a generic clone laptop, the brand is "Linux Certified" so it's about as generic as it gets.  Anyway, I installed a new copy of Ubuntu 7.10 over an old Fedora, assuming this would work better, and have been installing all the software the client wants.

Unfortunately, using the standard

[FONT="Courier New"]sudo apt-get install texlive-latex-base[/FONT]

and then, this ...

[FONT="Courier New"]sudo apt-get install texlive texlive-latex-extra texlive-math-extra texlive-pstricks latex-beamer[/FONT]

both produced this error

[FONT="Courier New"]prompt>latex
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
**[/FONT]

and then it hangs there, forever.

I'm a newbie to Ubuntu but have to support it just like I do OS-X and XP boxes.  I have absolutely no particular devotion to texlive or any other version of latex, and just want to get one installed that works.  Any advice is appreciated, but please be detailed in explanation, as I don't possess the familiarity of the installation process of the more Linux-oriented posters on this forum.

Thank you ahead of time

---

### Post by kalwisti on 2008-02-17
Hello, Alabamian,

I don't what might have happened to cause your problem, but this is my best guess as to how you might fix it. (Caveat lector: I am a new Ubuntu user, but have been using Linux for over a year and LaTeX for almost two years. So this advice is not totally off the wall).

(a). I would recommend using the Synaptic Package Manager to remove any and all texlive packages you've already installed. You can find it under System --> Administration --> Synaptic Package Manager.

It will first prompt you for your password. Once that's done, press the Reload button at the top of its toolbar, then use the Search button to find the texlive packages you've installed. (If they were actually installed, you should see the package's checkbox colored green as well as info given under the "Installed Version" column, e.g., texlive-latex-base  2005.dfsg.3-1). Right-click on the package you wish to remove and select "Mark for Removal." Click on the Apply button, and Synaptic should churn away, remove the package and then notify you that it has been removed.

(b). Next you can follow the instructions given in the thread below 

[http://ubuntuforums.org/showthread.php?t=693392&highlight=texlive]("http://ubuntuforums.org/showthread.php?t=693392&highlight=texlive") 

to try installing TeX Live again.

Although teTeX still exists, it is no longer supported by its developer (Thomas Esser) and will increasingly become outdated. So TeX Live is a better choice for the future, and the Texmaker front-end editor is very user-friendly.

Note: I saw some forum members recommending TeXmacs as an editor; however, installing TeXmacs will also install teTeX, so that would mess up your TeX Live installation ...

HTH,
=david

---

### Post by frisket on 2008-03-20
> **Alabamian said:**
> 
[FONT="Courier New"]prompt>latex
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6)
 %&-line parsing enabled.
**[/FONT]

and then it hangs there, forever.

That's correct. You have to give latex a file to process,
otherwise it will expect input from the terminal (NOT recommended).

Write a minimal LaTeX file and type latex filename.tex

P

---

