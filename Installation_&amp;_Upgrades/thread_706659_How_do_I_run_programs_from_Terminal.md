---
title: "How do I run programs from Terminal?"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by m5b on 2008-02-24
[FONT=Arial][SIZE=3]I have a number of programs that I can't get to run. They are not listed in the Applications Menu, and when I navigate to them in the Terminal and try to run them I get a message like "no such command"

Nevertheless, teh command is clearly llisted even though, when I type that command, the system tells me that the command does not exist.

And here is a related problem:

I have installed some document files, and they, too show up when I navigated to them in the Terminal. But I can't seem to find a way to read them. What do I need to do?
[/SIZE][/FONT]

---

### Post by jpeddicord on 2008-02-24
What commands were you trying to run? Keep in mind that $ at the start of a line usually isn't a part of a command. For example:

```
$ ls
```

This means you run the command "ls" as-is. The $ is there to show that it is a terminal command.

---

### Post by zvacet on 2008-02-24
You have dektop version installed,do you?Which app you try to run?You can make launcher  for them if they are not in menu.Why don´t you navigate to the files with nautilus?When you find files thar way just right click on it and you will see option **open with** and dropdown menu and select **text editor**.But if you realy want to run apps from terminal type **man app** (app is name of application you want to run) and you will find there how to do it.If it is no man run** app --help.**

---

### Post by Pumalite on 2008-02-24
Most of the time programs that do not appear in the menu can be run simply writing the name of the program.

---

