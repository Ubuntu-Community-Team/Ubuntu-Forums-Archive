---
title: "Desktop Shortcuts"
date: 2016-09-17
forum: MINT
---

### Post by oskar44 on 2016-09-17
About 10 now on Linux, first started with Ubuntu and now I found Linuxmint Sarah (Cinnamon) much better. Coming from a Windows environment, everything is so new to me.
 
Is it possible to create a shortcut on the Desktop and how do you do this?
 
I would like to copy a weather link into my Desktop and when I click it to take me to this site
 
Perhaps I must use the Terminal but I don’t know what command(s) to write

---

### Post by howefield on 2016-09-17
Thread moved to the "*MINT*" sub forum.

---

### Post by yetimon_64 on 2016-09-17
> **oskar44 said:**
> About 10 now on Linux, first started with Ubuntu and now I found Linuxmint Sarah (Cinnamon) much better. Coming from a Windows environment, everything is so new to me.
 
Is it possible to create a shortcut on the Desktop and how do you do this?
 
I would like to copy a weather link into my Desktop and when I click it to take me to this site
 
Perhaps I must use the Terminal but I don’t know what command(s) to write

Rather than a "shortcut" I'd suggest you try making a desktop config file. Below is an example you could adapt to the particular site by altering the "Exec" line.
 To make a desktop config file open gedit from dash and copy/paste in the example contents of the code box below.
```

[Desktop Entry]
Type=Application
Name=Weather
GenericName=Weather.
Comment=Open weather site in a new tab in firefox.
Exec=firefox -new-tab https://weather.com
Icon=
Categories=GNOME;GTK;Network;WebBrowser;
NoDisplay=true
```

Change the address in the exec line to the site/page you want to open. Copy and paste the exact address from your browser address bar and replace the "https://weather.com" section in the Exec line with what you want to open. Change any other details and add an icon address if you like (it will work fine without an icon though). By using the  -new-tab switch you will open the site in a new tab if you already have firefox open, without it a new window would otherwise open instead. When you are happy with the contents save the file as "weather.desktop" on you Desktop. Then right click on the new file and open the "Properties" option, go to the "Permissions" tab and tick the box at the bottom of the tab to set the file as executable.

You can now just double click the desktop config file on your Desktop and it will open your site/page in a new tab in firefox.

---

