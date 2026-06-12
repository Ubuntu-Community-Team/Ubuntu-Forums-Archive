---
title: "How to keep Ubuntu 18.04 for marking a launcher as unsafe?"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2018-04-27
When I try to launch pdfstudio12.desktop, Ubuntu says, "The application launcher 'pdfstudio12.desktop" has not been marked as trusted.  If you do not know the source of this file, launching it may be unsafe.

Okay, how do I mark a launcher as safe?

John

---

### Post by kerry_s on 2018-04-27
it should have a option for trust in that same dialog.
it's suppose to go in ~/.local/share/applications then it will be in your menu.

open the file manager & press ctrl+h to show hidden

---

### Post by ajgreeny on 2018-04-27
You may just need to make the launcher **pdfstudio12.desktop** file executable; I get the same error message sometimes for new launchers on my Xubuntu 16.04 and there, as mentioned by kerry_s there is a dialogue box with the two options, **Mark as trusted**, or, **Make executable**; doing either removes that continual error.

---

### Post by cigtoxdoc on 2018-04-27
Thank you very much.  Your suggestion worked.

John

---

