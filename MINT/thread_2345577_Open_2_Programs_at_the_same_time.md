---
title: "Open 2 Programs at the same time"
date: 2016-12-05
forum: MINT
---

### Post by oobvi on 2016-12-05
Is there any where to open 2 programs at the same time with a single click? I would like to do it on my desktop, not in the terminal. I am using Mint. 

In the terminal, I am able to open the programs by typing "program1" or "program2", but I would like to be able to put a link on my desktop that I could click on, and have both of them open.

---

### Post by Jeroen_Mathon on 2016-12-06
Hey Oobvi,

You could create a shortcut on your desktop that will execute the following `program1 && program2`

Could you try doing that for me?

---

### Post by oobvi on 2016-12-06
I used the launcher and inputted under "Command" [COLOR=#000000]`program1 && program2`, without the quotations. However, when I run it, it opens program 1 and tries to open a file called '&&' in program 1, gives an error message, and then tries to open program2 as a file within program 1, and gives another error message. When I reversed the two, it opens program 2 and tries to import the other program into program 2.

It seems to take anything that comes after the first application as part of that application. [/COLOR]

---

### Post by kpatz on 2016-12-06
Try putting this in the command:```
/bin/bash -c "program1 & program2 &"
```

Use a single ampersand, not a double, after each program name, and using the bash shell it should launch both programs.

---

### Post by oobvi on 2016-12-06
It worked, thanks for your help!

---

