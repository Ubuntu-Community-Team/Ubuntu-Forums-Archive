---
title: "Automated Upgrade and Install Problem"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by TCarr on 2008-09-27
I'm trying to create a script to automate the installation of a LAMP server using Ubuntu 8.04 Server version. 

The process involves using apt-get install dist-upgrade. In doing so, a screen pops up requiring the user to navigate to "OK" and press enter. I have tried apt-get -qq -y install dist-upgrade and still that screen comes up halting everything until the user navigates to the "OK and presses enter. I do not want this. Is there a way to bypass that screen and auto-assume "OK"?

Also, when installing ProFTPd there's a screen that comes up asking for "for inetd" or "standard". Is there a way to bypass this and select "standard" by default?

This is so I can create an automated installation/configuration script and not have to be at the computer waiting for prompts and catching them just so the process can continue.

---

### Post by TCarr on 2008-10-03
Bump. Still looking for a solution if anyone has any? Thanks.

---

