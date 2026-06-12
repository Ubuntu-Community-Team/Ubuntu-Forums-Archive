---
title: "Font Problem (Kile)"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by behnamf on 2008-10-01
Hello

I just installed the ubuntu 7 and I am using Kile. I have got some problems with kile, as when I am trying to comile some TEX documents I get the following error message:

ptmr7t at 10.0pt not loadable: Metric (TFM) file not found. \normalfont

I was receiving the very same message in my previous ubuntu installation and somehow I could mange to solve it, but right now, it seems un-solvable to me. Any help, suggestion will highly appreciated.

Thank you!

---

### Post by cariboo on 2008-10-02
Waht did you do to solve the problem on the previous version of Ubuntu.

Jim

---

### Post by behnamf on 2008-10-07
Hi Jim

I do not remember! I just played with it and it got solved!! but this time I am not going to be that lucky.

thanks

---

### Post by meho_r on 2008-10-07
It says that font metric at that size isn't available. Try other font (or maybe change size) to see if that helps. BTW, it has nothing to do with Kile.

---

### Post by behnamf on 2008-10-07
Hi

I need that specific font as it is a part of the template that I should use for my paper. using other templates I do not receive that error msg.

Behnam

---

### Post by meho_r on 2008-10-07
It looks like Times New Roman font. Did you try loading **mathptmx** package? It provides Times New Roman font including all that's needed for typesetting mathematics.

---

### Post by behnamf on 2008-10-07
No it did not help. The error msg is casued in a .cls file, the part od the .cls file that causes the error msg reads as following:

% IEEE uses Times Roman font, so we'll default to Times.
% These three commands make up the entire times.sty package.
\renewcommand{\sfdefault}{phv}
\renewcommand{\rmdefault}{ptm}
\renewcommand{\ttdefault}{pcr}

\@IEEEcompsoconly{\typeout{-- Using IEEE Computer Society mode.}}

% V1.7 compsoc nonconference papers, use Palatino/Palladio as the main text font,
% not Times Roman.
\@IEEEcompsocnotconfonly{\renewcommand{\rmdefault}{ppl}}

% enable Times/Palatino main text font
\normalfont\selectfont




the last line causes the above mentioned msg.

Thanks

---

### Post by meho_r on 2008-10-07
In presented code Times New Roman is used for main text (roman/serif), Helvetica as Sans Serif font and Courier as Typewriter font. Reading commented lines I assume that you're using Palatino/Palladio font somewhere in the document but it isn't in the code presented. Is it declared anywhere else? Since this is only part of the preamble I cannot test it.

However, maybe you should post a question here: [http://www.latex-community.org/]("http://www.latex-community.org/")

EDIT: There is Palatino indeed (ppl). My bad :(

---

### Post by behnamf on 2008-10-07
Hi 

I managed to solve my problem and I am mentioning the steps for the ones who may get the same problem as I took few days for me to solve it:

1- download all the tfm fonts from here:
[http://packages.ubuntu.com/feisty/all/tfm-arphic-bkai00mp/download](http://packages.ubuntu.com/feisty/all/tfm-arphic-bkai00mp/download)
2- install the downloaded package by right-clicking on the package and selecting GDebi installer packege
3- wait some time as it may take a while and then you are ready to go!

Thank you!

---

### Post by wimmelis on 2009-01-15
Dear all, 


I came across this thread as I have had similar problems, though in the past I solved them a different way, and it took me some time to find the solution back, but that also worked. So maybe interesting. 
Go to synaptic and install the following packages: texlive-latex-recommended, texlive-fonts-extra and texlive-fonts-recommended.


WM

---

### Post by Markjsca1 on 2009-01-26
Thanks. I tried the first solution, given by behnamf, and it worked for me :)

---

### Post by dvchops on 2009-05-05
> **wimmelis said:**
> Dear all, 


I came across this thread as I have had similar problems, though in the past I solved them a different way, and it took me some time to find the solution back, but that also worked. So maybe interesting. 
Go to synaptic and install the following packages: texlive-latex-recommended, texlive-fonts-extra and texlive-fonts-recommended.


WM

I had the same problem, this fixed it. Thanks!

---

### Post by imapostdoc on 2009-08-26
> **wimmelis said:**
> Dear all, 


I came across this thread as I have had similar problems, though in the past I solved them a different way, and it took me some time to find the solution back, but that also worked. So maybe interesting. 
Go to synaptic and install the following packages: texlive-latex-recommended, texlive-fonts-extra and texlive-fonts-recommended.


WM

wimmelis is awesome. A whole afternoon of headaches has come to an end...
Thanks!

---

