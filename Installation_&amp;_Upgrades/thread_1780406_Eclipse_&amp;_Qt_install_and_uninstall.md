---
title: "Eclipse &amp; Qt install and uninstall"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by hpng on 2011-06-11
Hello:

Not sure where to post this:
machine:  Ubuntu 10.04 LTS, AMD64

i downloaded Eclipse CDT (Helios), a C++ IDE, and install it directly via a double click
 after taring it.
I was able to compile a Hello World sample.  No problem running it.

i did not go through a package manager.

Then I install Qt plug-in downloaded from Qt.
I followed the Qt installation instructions.
When I open Eclipse, I do not see Qt folder when selecting a New project.
I also do not see any Qt text when I select in Eclipse this:  Windows>Preferences 

So I decide to start all over.  That means uninstalling eclipse.
I can delete the Eclipse directory since I created a separate eclipse folder.
Since I am a Linux beginner, I like to know the appropriate steps do a clean delete.
Again:  I did not use a package manager to install this.
I do not want to delete Eclipse's folder, and then not delete other information about eclipse 
stored somewhere used by Ubuntu.
 
Please explain what to do. 
Do I just delete the eclipse directory since everything is there ( I assume) or 
there is a better clean un-install method?

By the way, how do I remove an installed application if it was installed via a package manager?

Please note that the installed eclipse software does not show up in Ubuntu Software Center application under "Installed Software".

We are in the 21st century, and I am still surprise we still have install problems like this.

---

### Post by mp035 on 2011-06-12
You should always install from the repositories if possible.  Eclipse is available, and all plug ins will be configured correctly for you.
> 
We are in the 21st century, and I am still surprise we still have install problems like this. 

Package managers were designed to prevent this kind of problem, unfortunately, even in the 21st century there is no software that can help you if you don't use it. ;)

If you want to uninstall eclipse, go ahead and delete the directory that was created when you untarred.  Eclipse is a self-contained java install, it does not rely on anything outside the folder.

for more info see this forum post:
[http://www.javalobby.org/java/forums/t18678.html](http://www.javalobby.org/java/forums/t18678.html)

If you want to remove personal preference files, look for hidden files and directories in your home folder which begin with .eclipse they will be where preferences are stored.

THIS IS IMPORTANT!

If you are a beginner, always install software from the package manager.  Go to System->Administration->Synaptic Package Manager, in the search box type "eclipse" and you will be presented with all of the eclipse packages available.  Click on the checkbox next to the one you want to install, and select "Mark for Installation" and then click apply.  Follow the same process to remove, but select "Mark for Removal" instead.  There should also be Qt plugins available.

I would however recommend the qtcreator package if you want a good IDE for working with qt.  It has much better Qt support and an excellent wysiwyg interface designer.

Edit:
> 
Please note that the installed eclipse software does not show up in Ubuntu Software Center application under "Installed Software".


The Ubuntu Software centre will only manage software installed by the software centre itsef, or synaptic, apt-get, aptitude or dpkg.  If you do a manual install it will not be registered, and as such not managed.

I believe I have ranted for long enough now about the importance of using managed packages :)

---

### Post by hpng on 2011-06-12
Thanks.
Now, what if the plug-in does not exist in the package manager?
Which means I have to manually download it and manually install it also, right? 

I just accidentally deleted my menu items in the default panel.
how do I restore it?

Thanks.

---

### Post by mp035 on 2011-06-13
Hi,

Yeah, if you can't find the plugin (which does happen quite often) the best course of action is to install the version of eclipse available from the package manager and then manually install the plugin for said version of eclipse.

The advantage of doing it this way is if the plugin screws up eclipse then you can easily remove and reinstall it from the package manager.  Also you do not need to worry about manually removing the plugin when you uninstall.  It should be automatically removed with eclipse.  

Regarding the default menu, I use xubuntu which has a different desktop environment so I am not able to check this on my system, but IIRC, you should be able to right click on the gnome panel and select something that says "add new items" or something similar.  There will be an item that is "Application Menu" or something like that, add it to the panel.  IIRC there are 2 types of menu, the default gnome style and the Ubuntu specific one, be sure to choose the one you want.

---

### Post by hpng on 2011-06-13
Thanks MP03.
I solve the problem by directly installing Eclipse, bypassing Package manager.
It turns out that Eclipse is a self-contained package, so I can just delete its directory if needed.
Not need to go thru Package manager.

---

