---
title: "sudo dpkg --configure -a error"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by peterbug on 2007-04-09
when I type "sudo dpkg --configure -a" in to the konsole I get out :

 bug@bug:~$ sudo dpkg --configure -a
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--03:35:17--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--03:35:27--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--03:35:37--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--03:35:47--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... 1.0.0.0
Connecting to aleron.dl.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up.

--03:35:52--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--03:36:02--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::20
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::20|:80... failed: Network is unreachable.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts


whats wrong?

(ubuntu n00b please don't flame)

---

### Post by zvacet on 2007-04-09
System>administration>software properties Enable all repositories,because msttcorefonts are in multiverse repository.After that
```
sudo aptitude update && sudo aptitude upgrade
```

and when you are finish with that 
```
sudo aptitude install msttcorefonts

```

---

