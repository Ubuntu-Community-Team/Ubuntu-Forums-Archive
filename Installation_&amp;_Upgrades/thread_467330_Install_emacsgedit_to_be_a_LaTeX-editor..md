---
title: "Install emacs/gedit to be a LaTeX-editor."
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Thorun on 2007-06-07
I need a good LaTeX editor and compiler. 
I have installed Emacs and gedit is installed pr. default. 

I know, that both can be used to compiling LaTeX-documents - but i have no idea what to do with either programms.

I'm wery new to Ubuntu and i have just installed emacs with:  

```
sudo apt-get install emacs21 
```
and i think it made the a shortcut in the "applications --> programming". 

I need either emacs or gedit to work 100% compiling LaTeX-documents (due to my work). compare it to when installing MSOffice when you chek the "install all".
But i have no idea if i need a LaTeX compiler installed too, or how to make emacs and/or gedit work ?!

My questions is:
do i need anything else than Emacs or gedit to compile LaTeX-documents? If yes - what? and how is it installed?

How do i make emacs and/or gedit compile the LaTeX-documents?


Thankyou in advance.

/Rune
Denmark.

---

### Post by mannheim on 2007-06-07
As a first step, you will need to install tetex-bin using
```
sudo apt-get install tetex-bin
```
to get a tex and latex compiler. (There is also "texlive" as an alternative to "tetex" in the repositories. I think tetex is not maintained any longer; but it is still in the main Ubuntu repository.)

---

### Post by Thorun on 2007-06-07
tetex-bin is now installed. If i choose to install the livetex at another time - should i uninstall tetex-bin first?

If i have made a latex-document that requires a package that is not installed by the tetex-bin, then what do i do?

---

### Post by mannheim on 2007-06-08
> **Thorun said:**
> tetex-bin is now installed. If i choose to install the livetex at another time - should i uninstall tetex-bin first?

If i have made a latex-document that requires a package that is not installed by the tetex-bin, then what do i do?

I think that texlive and tetex are mutually exclusive.

If you need to install additional tex or latex packages, you can copy the necessary files into either /usr/local/share/texmf/ (for things to be available system wide), or into ~/texmf/ (for things available just to your username). The latter might be ~/.texmf now, I'm not sure what the default is. You may need to run the command "texhash" or "sudo texhash" in a terminal afterwards, to update tetex's internal list of available files.

Below the texmf directory, there are standard subdirectories you need to put the various different types of files in. Examine the existing /usr/share/texmf-tetex/ and its subdirectories to get the idea. For example, latex looks for ".sty" files in the directory ~/texmf/tex/latex/ and below. So if you have a new latex style file "mystyle.sty" for the "mystyle" package, you can copy it to ~/texmf/tex/latex/mystyle/mystyle.sty.

---

