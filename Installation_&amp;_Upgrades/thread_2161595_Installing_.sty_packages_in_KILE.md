---
title: "Installing .sty packages in KILE"
date: 2013-07-11
forum: Installation &amp; Upgrades
---

### Post by manolovaza on 2013-07-11
I am starting to use KILE but I have a problem with a long url that leaves the justified format of my document. I have searched and found out I need the url package but I haven't yet figured out how to install/add/import them in an easy way. I remember a friend using a package manager, export the packages to Miktex with \usepackage{}. I don't use Miktex because is windows based. I have fould [this]("http://ubuntuforums.org/showthread.php?t=864916") thread but it didn't help installing texlive, and as far as I know is another tex distro. Hope anyone there could help me.

Regards,

---

### Post by marianoa on 2013-07-11
texlive is probably already installed on you system since it's a dependency of kile. As for the url.sty package, it's strange that you don't have it in your latex installation. You can try to find the file in your system with
```

sudo updatedb
locate url.sty
```

If it cannot be found anywhere you can download it form here 
[http://www.ctan.org/tex-archive/macros/latex/contrib/url/](http://www.ctan.org/tex-archive/macros/latex/contrib/url/)
save it in the folder where your tex file is and then try to recompile after adding
```
\usepackage{url}
```
in your tex preamble

---

### Post by manolovaza on 2013-07-11
Thank you marianoa.

Indeed it was already installed but tought it wasn't because it had no effect in breaking in the slash. After reading [this]("http://tex.stackexchange.com/questions/3033/forcing-linebreaks-in-url") I desided to remove it because the address was too long and ugly. But \usepackage[hyphens]{url} partially worked.

Regards,

---

