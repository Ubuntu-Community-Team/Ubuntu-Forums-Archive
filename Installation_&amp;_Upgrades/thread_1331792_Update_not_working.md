---
title: "Update not working"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by Abadon125 on 2009-11-19
Hey everyone.  I was trying to get JDK installed yesterday (which I still have not gotten solved) and things went wrong.  See the thread linked below for details on that.

What is happening now is that it will not let me run update until I solve this error:

[INDENT]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
[/INDENT]
Please see the screenshot below.  I tried running the command in terminal and the window on the left shows what happens. It is the error that I keep getting and do not know what to do about.  If anyone can help that would be amazing!
Thanks.

---

### Post by lemming465 on 2009-11-21
Things may not be quite as horribly wrong as you fear.  Due to Sun's licensing, they can't bundle the documentation files in the JDK with the executables, and you have to pause in mid-install to download them by hand yourself.  That's the point you are stuck at.  

Bring up Firefox, point it at the cited URL, scroll down toward the bottom where it says "Java SE documentation", click the download button, accept the license agreement, download the file, move to to /tmp, do *sudo chown root.root /tmp/jdk*zip*, and then press enter at the stubborn shell prompt.  It should complete the install.

Debian package installs are occasionally interactive, and this is one of those occasions.

---

### Post by Abadon125 on 2009-11-21
I got it working.  Thank you anyways though :)

---

