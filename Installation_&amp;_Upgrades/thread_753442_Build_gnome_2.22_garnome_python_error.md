---
title: "Build gnome 2.22 garnome python error"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by ordealbyfire83 on 2008-04-12
Hello,
I am trying to build Gnome 2.22 from source using garnome. However I can't get past gnome-desktop, where the following error appears. It seems to be a problem with python but I can't seem to find anything out on it. Thanks in advance for any help.

[===== NOW BUILDING:    gnome-desktop-2.22.0    =====]
        [fetch] complete for gnome-desktop.
        [checksum] complete for gnome-desktop.
        [extract] complete for gnome-desktop.
        [patch] complete for gnome-desktop.
        [fixup] complete for gnome-desktop.
        [configure] complete for gnome-desktop.
 ==> Running make in work/main.d/gnome-desktop-2.22.0
make[1]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0'
make  all-recursive
make[2]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0'
Making all in po
make[3]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/po'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/po'
Making all in libgnome-desktop
make[3]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/libgnome-desktop'
Making all in libgnome
make[4]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/libgnome-desktop/libgnome'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/libgnome-desktop/libgnome'
Making all in libgnomeui
make[4]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/libgnome-desktop/libgnomeui'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/libgnome-desktop/libgnomeui'
make[4]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/libgnome-desktop'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/libgnome-desktop'
make[3]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/libgnome-desktop'
Making all in gnome-about
make[3]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/gnome-about'
Making all in headers
make[4]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/gnome-about/headers'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/gnome-about/headers'
make[4]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/gnome-about'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/gnome-about'
make[3]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/gnome-about'
Making all in pixmaps
make[3]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/pixmaps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/pixmaps'
Making all in desktop-docs
make[3]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/desktop-docs'
Making all in fdl
make[4]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/desktop-docs/fdl'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/desktop-docs/fdl'
Making all in gpl
make[4]: Entering directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/desktop-docs/gpl'
if ! test -d ar/; then mkdir ar/; fi
if [ -f "C/gpl.xml" ]; then d="../"; else d="/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/desktop-docs/gpl/"; fi; \
        (cd ar/ && \
          `which xml2po` -e -p \
            "${d}ar/ar.po" \
            "${d}C/gpl.xml" > gpl.xml.tmp && \
            cp gpl.xml.tmp gpl.xml && rm -f gpl.xml.tmp)
Traceback (most recent call last):
  File "/home/garnome/garnome/bin/xml2po", line 35, in <module>
    import libxml2
  File "/var/lib/python-support/python2.5/libxml2.py", line 1, in <module>
    import libxml2mod
ImportError: /var/lib/python-support/python2.5/libxml2mod.so: undefined symbol: xmlParseQuotedString
make[4]: *** [ar/gpl.xml] Error 1
make[4]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/desktop-docs/gpl'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0/desktop-docs'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/garnome/Desktop/garnome-2.22.0/desktop/gnome-desktop/work/main.d/gnome-desktop-2.22.0'
make: *** [build-work/main.d/gnome-desktop-2.22.0/Makefile] Error 2

---

