---
title: "firefox broken after upgrade to  22.04 LTS Desktop"
date: 2022-05-31
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2022-05-31
After upgrading my Desktop tp  22.04 LTS (GNU/Linux 5.15.0-33-generic x86_64) I cannot use firefox any longer as it cannot access user-dirs.dirs and user-dirs.locale.

The error indicates that it lacks permission to read the files.

user-dirs.dirs has "-rw-------"

user-dirs.locale has "-rw-rw-r--"

I assume this is snap related, but not sure how to fix it.

---

### Post by vanadium on 2022-05-31
Why do you need to access user-dirs.dirs with your webbrowser? Current version is a sandboxed version installed as Snap. By design, it only has access to your Downloads folder and visible folders in your Home directory. So no, it does not appear to be broken based on the information you provide.

---

### Post by TenPlus1 on 2022-05-31
The snap version of firefox has caused a few issues although if you really need a .deb version for previous behaviours to work you could try this guide: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by TheFu on 2022-05-31
> **vanadium said:**
> Why do you need to access user-dirs.dirs with your webbrowser? Current version is a sandboxed version installed as Snap. By design, it only has access to your Downloads folder and visible folders in your Home directory. So no, it does not appear to be broken based on the information you provide.

While I generally agree that using a tool in the specific way intended is desirable, firefox has allowed access to view HTML files stored anywhere on the system for decades - literally DECADES.  Many programs ship documentation in HTML format.  LibreOffice can output files in HTML.  Lots of tools create html files.  Why must those be stored only in HOME directories when they are read-only?

Documentation for Caja is shipped as html. goocanvas2 does too.  I'm seeing over 900 HTML documentation files AND _none_ of them are in my HOME directory.

Snap packaging is broken. Until local control for locations can be overridden in the constraints, it will remain broken.

I can only guess that Canonical thought because Chromium snap packages didn't get too many complaints that all was well.  It wasn't.  We used Chromium as a snap for 1 set of needs, but retained the non-snap version of other browsers to access local files/documents and found other workarounds when chromium was still useful, without all the limitations of scaps.

---

### Post by lister171254 on 2022-05-31
My gues is that during the conversion from the 'old' firefox to snap. something didn't quite work.

To prove this theory, I 

[LIST=1]
[*]Deleted my snap/firefox folder
[*]Started firefox
[*]Message indicated that everything in .mozilla is being copied to snap/firefox...
[*]Everyting is now working as expected
[*]
[/LIST]

---

