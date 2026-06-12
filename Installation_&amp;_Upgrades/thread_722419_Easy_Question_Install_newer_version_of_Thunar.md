---
title: "Easy Question: Install newer version of Thunar"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by Seeb on 2008-03-12
Hi, please don't be scared, this is many text for a small problem : - )

I use Xubuntu and because of that I also use Thunar. But after a few minutes of work
Thunar uses 90% of my CPU power. However I tried other browsers but now i want to
stick back to Thunar. I want to try the newer version 0.9 which is not avilable in synaptics.

After unpacking and running ./configure it says the following error msg:

[FONT="Arial Narrow"]checking for bind_textdomain_codeset... (cached) yes
checking for locales directory... ${datarootdir}/locale
checking for additional xgettext flags... --keyword=Q_ --from-code=UTF-8
checking for pkg-config... /usr/bin/pkg-config
checking for pkg-config >= 0.9.0... 0.22
[COLOR="Red"]checking for exo-0.3 >= 0.3.4... not found[/COLOR]
*** The required package exo-0.3 was not found on your system.
*** Please install exo-0.3 (atleast version 0.3.4) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.[/FONT]

[COLOR="Magenta"](I followed this small guide: [http://thunar.xfce.org/pwiki/documentation/installation](http://thunar.xfce.org/pwiki/documentation/installation))[/COLOR]

[COLOR="SeaGreen"]PROBLEM:[/COLOR] I dont know how to set this line "export PKG_CONFIG_PATH="/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH"" since i don't know where my libexo is installed! 

Can anyone help me?

---

