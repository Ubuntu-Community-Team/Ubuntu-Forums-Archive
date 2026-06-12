---
title: "Create .deb from gambas proyect"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by mauricio288 on 2012-06-09
I have been working with Gambas 2 (the one in the software center), Actially I took the source code of other program and create a new program basen on that.

But now that I finished, I can't create .deb files, gambas show me this error:
La creación del paquete ha fallado.
Package.MakeDebPackage.368: File or directory does not exist

So I dont know what to do now, I really need this program.

I tried with Gambas 3, but is too much work to do that the program based in Gmabas 2 works in Gambas 3, also I tried creating a .deb package and gambas get frozen.

Please some help :-(

---

### Post by WillyESB on 2012-08-21
Hi,

These kind of Gambas problems are best posted on the Gambas mailing list.

But before that check your Gambas version (latest version is 2.24).
If you have an older version (<=2.23) then uninstall it.
Make sure to remove the source from the software resources if you used Gambas2  from another PPA.

Next install the version from the PPA of Kendek (= version 2.24):
[https://launchpad.net/~nemh/+archive/gambas](https://launchpad.net/~nemh/+archive/gambas)

Now try to make a .deb package again with the new version.
If the problem persists best  post your Gambas related problems on the [Gambas mailing list]("https://lists.sourceforge.net/lists/listinfo/gambas-user")

Good luck

---

