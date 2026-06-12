---
title: "Installing photoshop cs3"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Kognit on 2008-08-18
Hi

I am using ubuntu 8.04 and i want to install Photoshop CS3. I've got Wine, but it doesnt work. I have installation files on computer not CD.

If someone can help me  it would "shine" my day

---

### Post by ajgreeny on 2008-08-18
Assuming there is a file in the installation files called **setup.exe** or something similar, and that the installation files are in a folder in your home called cs3, you would navigate to that folder in terminal with ```
cd cs3
``` and then use the command ```
wine setup.exe
``` If the setup.exe file is in a subfolder you will need to give the path to that folder or just navigate down further with ```
cd path/to/setup.exe
```and then run the wine command.

---

### Post by Kognit on 2008-08-19
i tried that already before but didn't work. Any other suggestion?

---

