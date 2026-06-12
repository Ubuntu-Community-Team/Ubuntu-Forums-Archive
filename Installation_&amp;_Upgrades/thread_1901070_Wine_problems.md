---
title: "Wine problems"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2011-12-27
Opening up separate thread from the one stop lubuntu thread:

> 
    I can not see the Wine entry in the applications list. I have just updated wine. It did not make it appear in the applications list. How do I edit the application list (the one that is on the panel that shows all the applications that I can open)?

    How do I get a program file showing in
    /home/robin/.wine/drive_c/Program Files/AnyProgram.exe

    to load from the cairo dock? I have tried both dragging the exe file and a link but both do not open from within cairo?

Well, you need a .desktop file. This is a combined icon, title, tooltip, and command file. These appear in /usr/share/applications, and are what appear in lxpanel and cairo dock.

Can you post how you run your application from the command-line? Once you can tell me that, I can make a .desktop for you.
I do not know how to run the program from the command line because of the involvement of wine.

Normally I would double click on the exe file and it would be opened by the wine program loader, which is a right click option.

The location of the file is:

/home/robin/.wine/drive_c/Program Files/Any Password/AnyPass.exe


I am surprised that wine is not appearing in my applications and so I can not access any of the programs run from wine via the list of applications or the docks.

Is it possible to drag and drop a windows program into the cairo dock and the panel?

---

### Post by MG&amp;TL on 2011-12-27
Nope, not so far as I know, as I said, you're only actually dropping the .desktop file into cairo or whatever. The actual binary is usually located in /usr/bin/

Anyway, copy-paste the following into a text-file:

```

[Desktop Entry]
Version=1.0
Type=Application
Name=AnyPass
Exec=wine /home/robin/.wine/drive_c/Program Files/Any\ Password/AnyPass.exe

```

and save it as "AnyPass.desktop" in your "Documents" folder

Now open a terminal (Ctrl-Alt-T) and enter:

```
sudo cp ~/Documents/AnyPass.desktop /usr/share/applications
```

and then hit RETURN, then enter your password (you can't see it!), then return again. Done!

You should now be able to see it in your apps menu, and presumable drag and drop into cairo too. It will look bad with no icon, you can add the icon (if you have one) by adding:

```
Icon=/path/to/my/icon
``` 

to the file. :)

Hope this helps, and sorry about the mix up with the thread, my bad. :(

---

### Post by Robbyx on 2011-12-28
Thank you very much for your help. It is now much clearer.I can set other such situations.

Robin

PS if you could comment on my firefox query in the lubuntu thread I would very grateful. It is in that thread because the problem has only arisen since I switched to lubuntu.

---

