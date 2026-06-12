---
title: "creating launcher for software installed using wine"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by madeel2 on 2012-01-13
I installed an accounting software using wine. It get installed and in working condition. However, I want to create its launcher. In the web, it was suggested visiting program file folder located in virtual drive C created by wine. But there isn't any folder for that software. 

Another issue is that I can't close the program. A message pops up that can't close visual fox pro. 

Any help? Thanks.

---

### Post by carl4926 on 2012-01-13
Are you sure there isn't a launcher in the menu?

The program is in hidden files/folder

/.wine/drive_c/Program Files/

---

### Post by madeel2 on 2012-01-13
I went to the program files folder, right click the workspace and select, 'show hidden'. Nothing appears.

---

### Post by IPEX-731BA5DD06 on 2012-01-13
to access hidden folders;

1) Open Places (top of screen) 
2) Go to Home folder
3) Control-H to view Hidden folders
4) Navigate from .wine (hidden folder)

to close that program 

1) System (top of screen in menu bar)
2) Administration
3) System Monitor
4) Click on Processes tab, arrange by name and highlight program, click end program

---

### Post by IPEX-731BA5DD06 on 2012-01-13
to access hidden folders;

1) Open Places (top of screen) 
2) Go to Home folder
3) Control-H to view Hidden folders
4) Navigate from .wine (hidden folder)

to close that program 

1) System (top of screen in menu bar)
2) Administration
3) System Monitor
4) Click on Processes tab, arrange by name and highlight program, click end process

---

### Post by madeel2 on 2012-01-13
Lubuntu has the task manager. So I went their and killed the process. So the program did shut down. But there should be some better way. For now, this issue can be considered resolve :)

However, I couldn't locate the wanted folder in the program file folder.

---

