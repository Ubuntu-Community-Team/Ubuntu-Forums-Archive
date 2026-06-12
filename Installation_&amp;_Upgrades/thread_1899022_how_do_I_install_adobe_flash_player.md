---
title: "how do I install adobe flash player"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by Fertech on 2011-12-22
I have ubuntu 9.04 and I'm trying to install adobe flash player to watch youtube any information would be nice?

---

### Post by darkod on 2011-12-22
Go to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) and take a look if it reports your system and browser correctly. If it does, in the drop-down box select .tar.gz for other Linux.

When the file downloads, right click on it and open it with Archive Manager. Extract it where ever you want (remember the location).

The way I am doing it, I use only one single file from the archive, the libflashplayer.so
In my case I am using Firefox. Open your Home folder and press Ctrl + H to see the hidden folders/files. Open the folder .mozilla
If it doesn't exist, create a folder called plugins there.
Copy the libflashplayer.so into plugins
Restart firefox and now you have the latest flash player.

---

### Post by Rockin-ubu on 2011-12-22
Why not Update?
 Anyways....
You technically could just go to ubuntu software center and search "Adobe" and its there :D

---

### Post by darkod on 2011-12-22
Actually I never tried that in 11.10. :) In earlier versions it never worked with 64bit ubuntu. So it became a habit to simply drop the .so file in the folder.

But looking in Software Centre now, it seems again the player it will try to install is 32bit and I run 64bit. The procedure I suggested above correctly identified my system as 64bit and browser as firefox, and after the download it's simple copy-paste.

---

### Post by spcwingo on 2011-12-23
I thought 9.04 had reached EOL.  :confused:

---

