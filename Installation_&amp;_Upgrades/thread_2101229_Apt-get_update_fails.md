---
title: "Apt-get update fails"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by Alaza on 2013-01-04
Hi guys.

I recently upgraded from Ubuntu 10.04 to 12.04, but after doing so I'm trying to upgrade my Chromium installation.

However, when doing this through apt-get I get the error message that I have included in the attached text file.

Do you have any idea how to fix this?

Thanks a lot.

```
Reading package lists...
Building dependency tree...
Reading state information...
chromium-browser is already the newest version.
The following package was automatically installed and is no longer required:
  gnome-power-manager
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Setting up emacs23 (23.3+1-1ubuntu9.1) ...
emacs-install emacs23
install/a2ps: Handling install for emacsen flavor emacs23
Wrote /usr/share/emacs23/site-lisp/a2ps/a2ps-print.elc
Wrote /usr/share/emacs23/site-lisp/a2ps/a2ps.elc
install/dictionaries-common: Already byte-compiled for emacs23. Skipping ...
install/ecb: Handling install for emacsen flavor emacs23
Loading /etc/emacs/site-start.d/00debian-vars.el (source)...
Loading /etc/emacs/site-start.d/50a2ps.el (source)...
Loading /etc/emacs/site-start.d/50asymptote.el (source)...
Loading /etc/emacs/site-start.d/50autoconf.el (source)...
Loading /etc/emacs/site-start.d/50cedet-common.el (source)...
Loading /etc/emacs/site-start.d/50devhelp.el (source)...
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /etc/emacs/site-start.d/50eieio.el (source)...
Loading /etc/emacs/site-start.d/50emacs-goodies-el.el (source)...
Package emacs-goodies-el not fully installed.  Skipping setup.
Loading /etc/emacs/site-start.d/50psvn.el (source)...
Loading /etc/emacs/site-start.d/51ede.el (source)...
Loading /etc/emacs/site-start.d/51speedbar.el (source)...
Loading /etc/emacs/site-start.d/52semantic.el (source)...
Loading /etc/emacs/site-start.d/53cedet-contrib.el (source)...
Loading /etc/emacs/site-start.d/53cogre.el (source)...
Loading /etc/emacs/site-start.d/55ecb.el (source)...
Error while loading 55ecb: Cannot open load file: ecb-autoloads
Source file `/usr/share/emacs23/site-lisp/ecb/silentcomp.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-util.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/tree-buffer.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-mode-line.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-face.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-advice-test.el:46:1:Error: Failed to find version for newly installed cedet
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-analyse.el:34:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-autogen.elc
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-compilation.el' newer than byte-compiled file

In toplevel form:
ecb-buffertab.el:51:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-common-browser.el:47:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-compatibility.el:44:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-compilation.elc

In toplevel form:
ecb-create-layout.el:49:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-cycle.el:66:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-eshell.el:80:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-examples.el:62:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-face.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-file-browser.el:36:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-help.el:43:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-jde.el:57:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout-defs.el:46:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout.el:119:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-method-browser.el:35:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-mode-line.elc
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-multiframe.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-navigate.el:42:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic-wrapper.el:40:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic.el:32:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-speedbar.el:68:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-symboldef.el:49:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-tod.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-upgrade.el:1150:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-util.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-winman-support.el:101:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb.el:141:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/follow-mouse.elc
Wrote /usr/share/emacs23/site-lisp/ecb/silentcomp.elc
Wrote /usr/share/emacs23/site-lisp/ecb/tree-buffer.elc
emacs-install: /usr/lib/emacsen-common/packages/install/ecb emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs23 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs23 | emacs23-lucid | emacs23-nox; however:
  Package emacs23 is not configured yet.
  Package emacs23-lucid is not installed.
  Package emacs23-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ecb:
 ecb depends on emacs23 | emacsen; however:
  Package emacs23 is not configured yet.
  Package emacsen is not installed.
  Package emacs which provides emacsen is not configured yet.
  Package emacs23 which provides emacsen is not configured yet.
dpkg: error processing ecb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs-goodies-el:
 emacs-goodies-el depends on emacs23 | emacsen; however:
  Package emacs23 is not configured yet.
  Package emacsen is not installed.
  Package emacs which provides emacsen is not configured yet.
  Package emacs23 which provides emacsen is not configured yet.
dpkg: error processing emacs-goodies-el (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs23
 emacs
 ecb
 emacs-goodies-el

```

---

### Post by zvacet on 2013-01-04
```
sudo dpkg --configure -a
```

---

### Post by dino99 on 2013-01-04
when you get conflicts, mainly after a huge upgrade (dist-upgrade), tehn you can purge the conflicting packages then reinstall them.
Of course its always a good idea to clean the system first, and desactivate/update the non genuine repo(s) like ppa(s):

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg-reconfigure -phigh -a
(be patient, can take a while, dont stop it yourself)

sudo apt-get update

sudo apt-get purge emacs23
sudo apt-get purge emacs
sudo apt-get purge ecb

sudo apt-get install emacs
sudo apt-get install emacs23
sudo apt-get install ecb

then logout/in and check your logs

---

### Post by Alaza on 2013-01-04
Thank you for the quick answers.

I just tried every step you suggested, dino99, however I still have got more or less the same issues. Now the problem is this:

```
Reading package lists...
Building dependency tree...
Reading state information...
libjpeg62 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Setting up ecb (2.40+cvs20110608-2) ...
install/ecb: Handling install for emacsen flavor emacs23
Loading 00debian-vars...
Loading /etc/emacs/site-start.d/50a2ps.el (source)...
Loading /etc/emacs/site-start.d/50asymptote.el (source)...
Loading /etc/emacs/site-start.d/50autoconf.el (source)...
Loading /etc/emacs/site-start.d/50cedet-common.el (source)...
Loading /etc/emacs/site-start.d/50devhelp.el (source)...
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /etc/emacs/site-start.d/50ecb.el (source)...
Source file `/usr/share/emacs23/site-lisp/ecb/silentcomp.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-util.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
Error while loading 50ecb: Failed to find version for newly installed cedet
Loading /etc/emacs/site-start.d/50eieio.el (source)...
Loading /etc/emacs/site-start.d/50emacs-goodies-el.el (source)...
Loading /etc/emacs/site-start.d/50psvn.el (source)...
Loading /etc/emacs/site-start.d/51ede.el (source)...
Loading /etc/emacs/site-start.d/51speedbar.el (source)...
Loading /etc/emacs/site-start.d/52semantic.el (source)...
Loading /etc/emacs/site-start.d/53cedet-contrib.el (source)...
Loading /etc/emacs/site-start.d/53cogre.el (source)...
Source file `/usr/share/emacs23/site-lisp/ecb/tree-buffer.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-mode-line.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-face.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-advice-test.el:46:1:Error: Failed to find version for newly installed cedet
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-analyse.el:34:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-autogen.elc
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-compilation.el' newer than byte-compiled file

In toplevel form:
ecb-buffertab.el:51:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-common-browser.el:47:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-compatibility.el:44:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-compilation.elc

In toplevel form:
ecb-create-layout.el:49:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-cycle.el:66:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-eshell.el:80:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-examples.el:62:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-face.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-file-browser.el:36:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-help.el:43:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-jde.el:57:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout-defs.el:46:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout.el:119:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-method-browser.el:35:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-mode-line.elc
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-multiframe.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-navigate.el:42:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic-wrapper.el:40:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic.el:32:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-speedbar.el:68:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-symboldef.el:49:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-tod.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-upgrade.el:1150:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-util.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-winman-support.el:101:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb.el:141:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/follow-mouse.elc
Wrote /usr/share/emacs23/site-lisp/ecb/silentcomp.elc
Wrote /usr/share/emacs23/site-lisp/ecb/tree-buffer.elc
emacs-package-install: /usr/lib/emacsen-common/packages/install/ecb emacs23 emacs23 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing ecb (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ecb

```

---

### Post by dino99 on 2013-01-04
well, ecb complaint about the right missing required version.
how are you trying to install ? from repo ? from which ubuntu ? 32 or 64 bits ?

[https://launchpad.net/ubuntu/+source/ecb](https://launchpad.net/ubuntu/+source/ecb)

---

### Post by Alaza on 2013-01-04
> **dino99 said:**
> well, ecb complaint about the right missing required version.
how are you trying to install ? from repo ? from which ubuntu ? 32 or 64 bits ?

[https://launchpad.net/ubuntu/+source/ecb](https://launchpad.net/ubuntu/+source/ecb)

I seem to get the error trying to install anything from apt-get. Is ECB used for this?

My Ubuntu installation is a 64 bit, running XUbuntu.

Should I try and download ECB from the link you posted?

---

### Post by fdrake on 2013-01-04
try this:
```

sudo add-apt-repository ppa:a-v-shkop/chromium
sudo apt-get update
sudo apt-get install chromium-browser

```

if that fails than download the *.deb file from here and run install from the download

[http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel)

---

### Post by Alaza on 2013-01-04
> **fdrake said:**
> try this:
```

sudo add-apt-repository ppa:a-v-shkop/chromium
sudo apt-get update
sudo apt-get install chromium-browser

```

if that fails than download the *.deb file from here and run install from the download

[http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel)

I tried your suggestion, but unfortunately it doesn't solve the problem. I guess the ECB problem has to be fixed first?

What I get now is this:

```
Reading package lists...
Building dependency tree...
Reading state information...
chromium-browser is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Setting up ecb (2.40+cvs20110608-2) ...
install/ecb: Handling install for emacsen flavor emacs23
Loading 00debian-vars...
Loading /etc/emacs/site-start.d/50a2ps.el (source)...
Loading /etc/emacs/site-start.d/50asymptote.el (source)...
Loading /etc/emacs/site-start.d/50autoconf.el (source)...
Loading /etc/emacs/site-start.d/50cedet-common.el (source)...
Loading /etc/emacs/site-start.d/50devhelp.el (source)...
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /etc/emacs/site-start.d/50ecb.el (source)...
Source file `/usr/share/emacs23/site-lisp/ecb/silentcomp.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-util.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
Error while loading 50ecb: Failed to find version for newly installed cedet
Loading /etc/emacs/site-start.d/50eieio.el (source)...
Loading /etc/emacs/site-start.d/50emacs-goodies-el.el (source)...
Loading /etc/emacs/site-start.d/50psvn.el (source)...
Loading /etc/emacs/site-start.d/51ede.el (source)...
Loading /etc/emacs/site-start.d/51speedbar.el (source)...
Loading /etc/emacs/site-start.d/52semantic.el (source)...
Loading /etc/emacs/site-start.d/53cedet-contrib.el (source)...
Loading /etc/emacs/site-start.d/53cogre.el (source)...
Source file `/usr/share/emacs23/site-lisp/ecb/tree-buffer.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-mode-line.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-face.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-advice-test.el:46:1:Error: Failed to find version for newly installed cedet
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-analyse.el:34:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-autogen.elc
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-compilation.el' newer than byte-compiled file

In toplevel form:
ecb-buffertab.el:51:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-common-browser.el:47:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-compatibility.el:44:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-compilation.elc

In toplevel form:
ecb-create-layout.el:49:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-cycle.el:66:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-eshell.el:80:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-examples.el:62:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-face.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-file-browser.el:36:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-help.el:43:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-jde.el:57:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout-defs.el:46:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout.el:119:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-method-browser.el:35:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-mode-line.elc
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-multiframe.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-navigate.el:42:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic-wrapper.el:40:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic.el:32:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-speedbar.el:68:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-symboldef.el:49:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-tod.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-upgrade.el:1150:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-util.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-winman-support.el:101:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb.el:141:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/follow-mouse.elc
Wrote /usr/share/emacs23/site-lisp/ecb/silentcomp.elc
Wrote /usr/share/emacs23/site-lisp/ecb/tree-buffer.elc
emacs-package-install: /usr/lib/emacsen-common/packages/install/ecb emacs23 emacs23 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing ecb (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ecb

```

---

### Post by fdrake on 2013-01-04
what about 
```

sudo apt-get update --fix-broken
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Alaza on 2013-01-04
> **fdrake said:**
> what about 
```

sudo apt-get update --fix-broken
sudo apt-get update && sudo apt-get upgrade

```

By running the --fix-broken argument everything seems okay, and I get a "Reading package lists... Done" in the end.

When running "sudo apt-get update && sudo apt-get upgrade" I get the code attached. I guess ECB still isn't fixed then. :/

```
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Setting up ecb (2.40+cvs20110608-2) ...
install/ecb: Handling install for emacsen flavor emacs23
Loading 00debian-vars...
Loading /etc/emacs/site-start.d/50a2ps.el (source)...
Loading /etc/emacs/site-start.d/50asymptote.el (source)...
Loading /etc/emacs/site-start.d/50autoconf.el (source)...
Loading /etc/emacs/site-start.d/50cedet-common.el (source)...
Loading /etc/emacs/site-start.d/50devhelp.el (source)...
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /etc/emacs/site-start.d/50ecb.el (source)...
Source file `/usr/share/emacs23/site-lisp/ecb/silentcomp.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-util.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
Error while loading 50ecb: Failed to find version for newly installed cedet
Loading /etc/emacs/site-start.d/50eieio.el (source)...
Loading /etc/emacs/site-start.d/50emacs-goodies-el.el (source)...
Loading /etc/emacs/site-start.d/50psvn.el (source)...
Loading /etc/emacs/site-start.d/51ede.el (source)...
Loading /etc/emacs/site-start.d/51speedbar.el (source)...
Loading /etc/emacs/site-start.d/52semantic.el (source)...
Loading /etc/emacs/site-start.d/53cedet-contrib.el (source)...
Loading /etc/emacs/site-start.d/53cogre.el (source)...
Source file `/usr/share/emacs23/site-lisp/ecb/tree-buffer.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-mode-line.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-face.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-advice-test.el:46:1:Error: Failed to find version for newly installed cedet
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-analyse.el:34:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-autogen.elc
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-compilation.el' newer than byte-compiled file

In toplevel form:
ecb-buffertab.el:51:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-common-browser.el:47:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-compatibility.el:44:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-compilation.elc

In toplevel form:
ecb-create-layout.el:49:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-cycle.el:66:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-eshell.el:80:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-examples.el:62:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-face.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-file-browser.el:36:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-help.el:43:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-jde.el:57:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout-defs.el:46:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout.el:119:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-method-browser.el:35:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-mode-line.elc
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-multiframe.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-navigate.el:42:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic-wrapper.el:40:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic.el:32:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-speedbar.el:68:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-symboldef.el:49:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-tod.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-upgrade.el:1150:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-util.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-winman-support.el:101:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb.el:141:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/follow-mouse.elc
Wrote /usr/share/emacs23/site-lisp/ecb/silentcomp.elc
Wrote /usr/share/emacs23/site-lisp/ecb/tree-buffer.elc
emacs-package-install: /usr/lib/emacsen-common/packages/install/ecb emacs23 emacs23 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing ecb (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ecb

```

---

### Post by dino99 on 2013-01-04
you get : "1 not fully installed or removed."

so you need to know about that broken package: open synaptic for ease, then select the broken one from the left pane, and watch the properties of that package (dependencies)

---

### Post by Alaza on 2013-01-04
> **dino99 said:**
> you get : "1 not fully installed or removed."

so you need to know about that broken package: open synaptic for ease, then select the broken one from the left pane, and watch the properties of that package (dependencies)

I'm not experienced in this at all, so I'm guessing my way forward, but I guess what you mean is what I've attached as a screenshot here. The conflict seems to be with "cedet", assuming that ECB is the problem, and that it's the right package I've found in Synaptic?

---

### Post by dino99 on 2013-01-04
if cedet is installed, then yes you get a conflict with ecb; meaning that you need to purge cedet then reinstall ecb
but you might not have it as lucid was the latest ubuntu release with that package.

---

### Post by Alaza on 2013-01-04
> **dino99 said:**
> if cedet is installed, then yes you get a conflict with ecb; meaning that you need to purge cedet then reinstall ecb
but you might not have it as lucid was the latest ubuntu release with that package.

I tried this, but I get the exact same log file I'm afraid. When running "sudo apt-get purge cedet" I get this:

```
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up ecb (2.40+cvs20110608-2) ...
install/ecb: Handling install for emacsen flavor emacs23
Loading 00debian-vars...
Loading /etc/emacs/site-start.d/50a2ps.el (source)...
Loading /etc/emacs/site-start.d/50asymptote.el (source)...
Loading /etc/emacs/site-start.d/50autoconf.el (source)...
Loading /etc/emacs/site-start.d/50cedet-common.el (source)...
Loading /etc/emacs/site-start.d/50devhelp.el (source)...
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading /etc/emacs/site-start.d/50ecb.el (source)...
Source file `/usr/share/emacs23/site-lisp/ecb/silentcomp.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-util.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
Error while loading 50ecb: Failed to find version for newly installed cedet
Loading /etc/emacs/site-start.d/50eieio.el (source)...
Loading /etc/emacs/site-start.d/50emacs-goodies-el.el (source)...
Loading /etc/emacs/site-start.d/50psvn.el (source)...
Loading /etc/emacs/site-start.d/51ede.el (source)...
Loading /etc/emacs/site-start.d/51speedbar.el (source)...
Loading /etc/emacs/site-start.d/52semantic.el (source)...
Loading /etc/emacs/site-start.d/53cedet-contrib.el (source)...
Loading /etc/emacs/site-start.d/53cogre.el (source)...
Source file `/usr/share/emacs23/site-lisp/ecb/tree-buffer.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-mode-line.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-face.el' newer than byte-compiled file
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-advice-test.el:46:1:Error: Failed to find version for newly installed cedet
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.el' newer than byte-compiled file
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-analyse.el:34:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-autogen.elc
Source file `/usr/share/emacs23/site-lisp/ecb/ecb-compilation.el' newer than byte-compiled file

In toplevel form:
ecb-buffertab.el:51:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-cedet-wrapper.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-common-browser.el:47:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-compatibility.el:44:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-compilation.elc

In toplevel form:
ecb-create-layout.el:49:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-cycle.el:66:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p

In toplevel form:
ecb-eshell.el:80:1:Error: Symbol's value as variable is void: ecb-compilation-buffer-list-changed-p
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-examples.el:62:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-face.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-file-browser.el:36:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-help.el:43:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-jde.el:57:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout-defs.el:46:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-layout.el:119:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-method-browser.el:35:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-mode-line.elc
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-multiframe.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-navigate.el:42:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic-wrapper.el:40:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-semantic.el:32:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-speedbar.el:68:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-symboldef.el:49:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-tod.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-upgrade.el:1150:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/ecb-util.elc
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb-winman-support.el:101:1:Error: Failed to find version for newly installed cedet
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'
"/usr/share/emacs23/site-lisp/cedet-common/" added to `load-path'

In toplevel form:
ecb.el:141:1:Error: Failed to find version for newly installed cedet
Wrote /usr/share/emacs23/site-lisp/ecb/follow-mouse.elc
Wrote /usr/share/emacs23/site-lisp/ecb/silentcomp.elc
Wrote /usr/share/emacs23/site-lisp/ecb/tree-buffer.elc
emacs-package-install: /usr/lib/emacsen-common/packages/install/ecb emacs23 emacs23 failed at /usr/lib/emacsen-common/emacs-package-install line 30, <TSORT> line 1.
dpkg: error processing ecb (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ecb

```

---

### Post by Alaza on 2013-01-04
I found this bug reported:

[https://bugs.launchpad.net/ubuntu/+source/ecb/+bug/861533](https://bugs.launchpad.net/ubuntu/+source/ecb/+bug/861533)

It doesn't seem like a trivial issue to solve, nor does it seem that a solution exists.

What can I do here? :)

Edit:

Okay, so I found this as well:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=644185](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=644185)

"We believe that the bug you reported is fixed in the latest version of
ecb, which is due to be installed in the Debian FTP archive:

ecb_2.40+cvs20110608-2.debian.tar.gz
  to main/e/ecb/ecb_2.40+cvs20110608-2.debian.tar.gz
ecb_2.40+cvs20110608-2.dsc
  to main/e/ecb/ecb_2.40+cvs20110608-2.dsc
ecb_2.40+cvs20110608-2_all.deb
  to main/e/ecb/ecb_2.40+cvs20110608-2_all.deb"

I don't know how exactly how to get these files and what to do with them if I get them. Any tips?

---

### Post by fdrake on 2013-01-04
you can find them here:
[http://ftp.sv.debian.org/ubuntu/ubuntu/pool/universe/e/ecb/](http://ftp.sv.debian.org/ubuntu/ubuntu/pool/universe/e/ecb/)

---

