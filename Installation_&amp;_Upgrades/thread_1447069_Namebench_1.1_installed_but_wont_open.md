---
title: "Namebench 1.1 installed but wont open"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by slashwannabe94 on 2010-04-04
i have installed namebench 1.1 using terminal. its saved to my directories yet i still cant open it. does anyone know what may be wrong ?

---

### Post by RobsonGrangeiro on 2010-05-04
Hi,

A. Are you installed "python-tk" package?
B. After untar the namebench.tar file, are you run this installation command?
[FONT=Courier New]
sudo python setup.py install[/FONT]

If the two steps are ok, follow this other steps.

To execute (after installation process) try this:

1. Go to folder /usr/local/lib/python2.6/dist-packages/
2. Verify if the file "namebench.py" exists. 
3. If exists, you can run this command:
[FONT=Courier New]
sudo python ./namebench.py[/FONT]

This work with me, good luck!

---

