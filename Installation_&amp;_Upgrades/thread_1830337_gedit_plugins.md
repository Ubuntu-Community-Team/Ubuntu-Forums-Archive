---
title: "gedit plugins???????"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by pedro_miguel on 2011-08-21
Hi there guys;

I need help with two things the first one how do i install gedit plugins i know i have to create a new directory so first i tried to go to the directory and create a folder which did not work because there is no option to do so, then I've open terminal and typed the following ```
sudo mkdir /home/File System/usr/local/share/gedit/plugins/
``` but it did not work, i get a message saying "no such file or directory" so im a bit lost now lol how do i do??? After the directory is created how do i copy the files in?? Also i've moved to Ubuntu last Friday (thats why these stupid questions) and deleted windows for good(i was tired of it) but i have this wd external hard drive with 500gbytes that refuses to mount : ) i know that there are loads of tutorials on how to do it but i just dont want to loose everything i have inside the hard disk the error i get is the following ```
Error mounting: mount exited with exit code 12: Failed to read last sector (976771119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

``` Thanks a lot in advance guys and sorry about the questions i just moved to Ubuntu.

---

### Post by nmaster on 2011-08-21
press Alt+F2 and enter xterm (or gnome-terminal or lxterminal) to open a terminal. to install a variety of gedit plugins just do this:
```
sudo apt-get install gedit-plugins
```

ps: to keep threads more organized, its better to open a separate thread for the issues with the external drive.

---

### Post by pedro_miguel on 2011-08-21
Hey nmaster;
It did work thanks for the tip, still i would like to keep my Ubuntu a bit more organized by creating a folder or at least by saving the new plugins into the same folder as the existing ones how can i do this??? Ohhh and yes i will post the external hard drive problem in another post sorry for that.

---

### Post by oldos2er on 2011-08-21
Do you actually have a folder named 'File System' in /home? Or were you trying to create a folder in /usr/local/share/gedit/ ?

---

### Post by pedro_miguel on 2011-08-22
> **oldos2er said:**
> Do you actually have a folder named 'File System' in /home? Or were you trying to create a folder in /usr/local/share/gedit/ ?

No No No i dont have a folder named 'File System' in /home, im trying to create a folder in /usr/local/share/gedit/plugins so that i can store the downloaded plugins but to access this i have to go to 'File System' first and then usr/local/share and so on because usr/local/.... is inside 'File System'.....so how do i create a folder in this directory????

---

### Post by oldos2er on 2011-08-22
```
sudo mkdir /usr/local/share/gedit/plugins/
```

But according to [http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins) the folder should be /usr/lib/gedit/plugins/ or .local/share/gedit/plugins/ if you only need the plugins for your user.

---

### Post by lisati on 2011-08-22
I think I see where some of the confusion might have come from.

In Linux, when someone talks about *file system*, they're not necessarily talking about a file with the name "system". Have a look [here]("http://en.wikipedia.org/wiki/File_system").

---

### Post by pedro_miguel on 2011-08-22
Ok oldos2er i tried to do what you said and this was what i got from the terminal:
```
pedro@pedro-HP-Pavilion-dv1000-EF025EA-AB9:~$ sudo mkdir /usr/local/share/gedit/plugins
mkdir: cannot create directory `/usr/local/share/gedit/plugins': No such file or directory
pedro@pedro-HP-Pavilion-dv1000-EF025EA-AB9:~$
```

---

### Post by pedro_miguel on 2011-08-22
Or maybe i,m doing something wrong : / OK so lets start by the beginning I've downloaded the plugins to the desktop since i couldn't download them to the specified directory then right click on the file and click on download here

---

### Post by Idefix82 on 2011-08-22
Assuming you are on Ubuntu 11.04,

```

cd Desktop
sudo mkdir /usr/lib/gedit-2/plugins
sudo cp MyFavourtitePluginThatIsSavedOnTheDesktop /usr/lib/gedit-2/plugins

```

The probability is high that the mkdir command is unnecessary because you should have the folder already (it will tell you so).

The last line needs to be modified according to what you want to install. Usually, there should be a file called somethingsomething.gedit_plugin. This file needs to go directly into the folder /usr/lib/gedit-2/plugins, so in the last command above, substitute the name of that file for MyFavourite... Further, there should be a whole folder containing the actual code of the plugin. That folder also needs to be copied into the same location. This is done with the same command (cp) but needs an extra parameter to indicate that it's a folder, and not just a single file:
```

sudo cp -r TheFolderContainingTheActualPlugin /usr/lib/gedit-2/plugins

```
The -r means "copy the folder and all subfolders and everything you can find in there".

If this is too general, then just tell us what plugin you have downloaded and what version of Ubuntu you are on, and we will give you the precise commands.

P.S. Because I am pedantic bastard, I can't resist: there is no syntactical meaning attached to more than one question mark in a row. One can sort of guess what you wanted to express, probably something like "this is a really questionny question", but then that doesn't make much sense, does it ;-)

---

### Post by pedro_miguel on 2011-08-22
Hey idefix82 thank you so much for your help i did as shown below:


cd Desktop

sudo mkdir /usr/lib/gedit-2/plugins [COLOR=SeaGreen]/* i didnt need to creat this folder  as i received a message saying that the folder was already created  so i  moved on to the next one */[/COLOR]

sudo cp smart_highlighting-2.0.0.tar.gz /usr/lib/gedit-2/plugins[COLOR=SeaGreen] /*  which copied the file saved on the desktop to specified directory */[/COLOR]

sudo cp -r smart_higlighting-2.0.0 /usr/lib/gedit-2/plugins [COLOR=SeaGreen]/* which  copied the extracted folder containing the plugin to the specified   directory */[/COLOR]



then i opened the folder containing the plugin on  the desktop and and clicked 2 on the install.sh file to install the  plugin and it worked like a charm lol

By the way is there any way of installing the plugin in the terminal rather then opening the saved file and click 2 on the install.sh ?


Ohhh and thanks for pointing out the lack of question marks on my questions lol sorry about that.
Once again Thank you very much

---

### Post by Idefix82 on 2011-08-22
> **pedro_miguel said:**
> 
Ohhh and thanks for pointing out the lack of question marks on my questions lol sorry about that.
Once again Thank you very much

Hehe. I was actually referring to too many question marks in the title :D

Since there was an install file, you didn't even have to copy anything into that folder, the install file probably did it for you. Many plugins come without an install file. In that case, you need to unpack the tar.gz or whatever packaging the plugin comes in, onto your desktop, and then copy the .gedit_plugin and the folder containing the plugin itself into the /usr/lib/gedit-2/plugins folder using the commands above. Note that copying the .tar.gz file itself into that directory will not help.

If the plugin works, you can safely delete everything from your desktop.

When you unpack the archive, you can usually use the GUI. But if you want to know how to do it in the terminal, here is what you do:
```

tar -xzf MyPlugin.tar.gz

```
Again, the basic pattern is "command modifiers". The command is tar, that's used both for packing and unpacking. Then come the modifiers: x means extract (if instead you wanted to create a new archive, you would replace x by c), z means that the file is compressed with gzip. If the file name ended on just .tar, you wouldn't need that. If it ended on .tar.bz2, you would have to replace z by j, so tar would know to use a different extraction algorithm. These are the most common ones. Finally, f means "and now I will tell you which file to unpack". After that just the file name.

---

