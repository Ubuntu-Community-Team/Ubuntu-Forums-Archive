---
title: "Run TeX Live after installation (12.04)"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by czrog on 2012-07-07
I'm new to Ubuntu so bare with me...

I've installed TeX Live and now I want to run the program so I can start exploring, but am unsure how to proceed. 

All suggestions are appreciated! 

Thanx!

---

### Post by zwygart on 2012-07-07
Are you familiar with the terminal? Just go to the place where you wrote your file and type : latex filename.tex  
Just typing "latex" also works, but you should type the entire doc. 

If your not familiar with terminal, I suggest using Texmaker which is a tex IDE.

---

### Post by czrog on 2012-07-07
> **zwygart said:**
> Are you familiar with the terminal? Just go to the place where you wrote your file and type : latex filename.tex  
Just typing "latex" also works, but you should type the entire doc. 

If your not familiar with terminal, I suggest using Texmaker which is a tex IDE.


@ zwygart: First, let me say thanks a bunch for helping me. I am attempting to be a part of the Ubuntu Manual Team because I'm pursuing a career in technical writing. So I need TeX Live.

 These are the instructions I followed in the terminal:

Instead of installing the upstream TeX-Live manually, it's best to install the **official** backports of the latest (2012) TeX-Live via their PPA.
  To do so from the terminal, first run:
  sudo apt-add-repository ppa:texlive-backports/ppa   And then run:
  sudo apt-get update && sudo apt-get install texlive-full 

Now it says:

Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 texlive-full : Depends: texlive-music (>= 2012.20120516) but it is not going to be installed
                Depends: latex-sanskrit but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Any idea what I should do from here?

---

### Post by zwygart on 2012-07-09
Sorry for being late. 

Wich version of Ubuntu do you use? 

You may try to install directly from the website of LaTeX : [http://www.latex-project.org/ftp.html](http://www.latex-project.org/ftp.html)

The link is : mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz
Extract it and Launch ./install-tl via a terminal. 

This will take some time, and unfortunatly, LaTeX will not be updated this way when you use Ubuntu's package manager. You will have to maintain it manually. If I found a better way, I will post it.

---

