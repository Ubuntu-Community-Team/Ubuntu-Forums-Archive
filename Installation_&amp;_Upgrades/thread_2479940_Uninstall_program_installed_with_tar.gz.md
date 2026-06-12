---
title: "Uninstall program installed with tar.gz"
date: 2022-10-13
forum: Installation &amp; Upgrades
---

### Post by luncaaa on 2022-10-13
Hello o/

How can I uninstall a program I installed by downloading a tar.gz file, uncompressing it and running the file it had inside? I deleted the original tar.gz file and the uncombressed folder along with the installation file.

The file is JetBrains Toolbox in case it helps.

---

### Post by vanadium on 2022-10-13
Impossible to say in general. A tar.gz is a general archive format, just like the zip format. Anything can be in there. If it contains a program, the way the program must be installed and can be uninstalled totally depends on how the developer intended it. Sometimes, the program can be directly run from the uncompressed directory, otherwise an installation script is provided.

Download the tar.gz file again, and carefully look at its contents. At best, there is a README file that tells how the program must be installed. If you are lucky, there are also instructions on how the program can be removed. If not, then looking at the installation script may give a hint of what that script has done to your system.

---

### Post by luncaaa on 2022-10-13
It does not include a README file, but I did find instructions on how to uninstall in their website. Thanks for your help!

---

