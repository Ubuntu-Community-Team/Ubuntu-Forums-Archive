---
title: "TCPDF install issues"
date: 2023-03-01
forum: Installation &amp; Upgrades
---

### Post by jural1 on 2023-03-01
I am running Ubuntu 22.04 with Apache2 and PHP8.  I am writing a script and need to use tcpdf.  I have tried to install the ext in php.ini with no love.  The install goes fine.  ie Sudo apt-get install php-tcpdf.  Say that it is already installed and at the latest version.  However my script gives me, [COLOR=#000000][FONT=&quot]TCPDF extension is not loaded!.  Any ideas on how to get the extension loaded?  I also looked for tcpdf.so and it is nowhere to be found on the drive.  Thanks for the help.  It is appreciated.

Jural[/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2023-03-01
TCPDF is written in PHP, no external libraries are needed.

Holger

---

### Post by MAFoElffen on 2023-03-02
Using the library seems fairly straight forward, according to the tips on installing and using from it's GitHub page: [https://github.com/naitsirch/tcpdf-extension](https://github.com/naitsirch/tcpdf-extension)

Although, it does say:
> 
TCPDF is a PHP library to generate PDF documents. It is very feature rich, [COLOR=#ff0000]but not easy to use[/COLOR].


---

