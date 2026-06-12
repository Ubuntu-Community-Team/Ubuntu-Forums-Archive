---
title: "installing fonts, or copying them to the correct folder to show up in openoffice"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by charlieluna on 2011-04-03
Here is what i did. it was very simple actually.

1. i downloaded the files and extracted them to the desktop. makes it easy to find them.

2. create a new folder in your home folder with whatever name you want for your fonts.

3. open the extracted font files and drag the .ttf files to the new folder in your home folder for your fonts. 

here is where it gets technical.

1. open the terminal and type this code:
sudo cp -r /home/yourusername/font_folder_name/* /usr/share/fonts/truetype

that should do the trick. now you will have all those fonts available in any word processing program you use. if this doesn't work, i might have typed in the wrong code. let me know. good luck and have fun!!

---

### Post by walt.smith1960 on 2011-04-03
I think Charlie's procedure will make those fonts available to all users.  If you just want them available to one user it's even easier.  When you create a folder in your home directory, make it a hidden folder by putting a dot before the name and call the folder "fonts".  Any .ttf files in the "fonts" folder in the user's home folder will be available to that user only.

---

### Post by ajgreeny on 2011-04-03
Nearly right, I think, but once the fonts are in the proper folder we need to install them properly in Ubuntu.

Open a terminal and cd to your /usr/share/fonts/truetype folder, then use the following ```
sudo fc-cache -f -v
``` This will install the fonts so that your applications like OpenOffice and others can use them.  Without that command I don't think they will be seen by the system, unless things have changed over the last year or two.

---

### Post by charlieluna on 2011-04-03
things must have changed because when i open openoffice and open the list of fonts, the ones i downloaded are there. but i will do what you suggest as well just to cover all my bases. thanks for the heads up. and again, i'm almost a complete noob at linux. i am learning as i go since i have had no formal training on how to do all of this command line stuff.

i just did you what you said to do and there weren't any errors so i guess everything is ok. i am going to open openoffice and make sure they are still there but i am sure they are. i appreciate the extra help.

---

