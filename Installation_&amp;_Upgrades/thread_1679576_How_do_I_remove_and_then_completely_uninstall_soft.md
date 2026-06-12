---
title: "How do I remove and then completely uninstall software?"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by Catbells on 2011-02-01
When Ubuntu Software Centre removes software, it leaves files behind in File System which is owned by Root preventing me from deleting them.  
1.  Could this be why Update Manager is insisting that I install updates for software that I have removed and do not use?
2.  There is one application I would like to re-install because it asked me technical questions before I installed it.  I think I gave the wrong answer and when I re-installed it, it didn't ask the question again.  It seems likely that there is a file somewhere that Ubuntu Software Centre didn't remove, and I could do with deleting but is owned by Root.  How do I do this?
3.  Should I have posted this query under 'Absolute Beginner Talk?'  Please treat me as an absolute beginner.
I'm using Ubuntu 10.04 LTS Lucid Lynx.

---

### Post by lisati on 2011-02-01
From the command line, you can do something like this:
```
sudo aptitude purge *package-name*
```

This will uninstall the program and clean out the configuration files.

---

### Post by Catbells on 2011-02-01
Thank you so much for the lightning quick reply.  How would I work out the package name, say for Pidgin or Fish Fillets?

---

### Post by weblordpepe on 2011-02-01
Hi dude there's a way you can do this graphically.

Usually you'd click on Applications, and then Ubunutu Software Centre. It has the ability to remove programs, but I don't remember what it does with the configuration exactly.  

I would suggest the best way to find out the package name and do it all in one swoop using your mouse would be to run the program called **Synaptic.**
Its for managing packages in advanced ways just like what you're doing. Its found under** System**, then** Administration**.

You can type in the search box to find your program, and then right click it (say for Pidgin) and click '**completely remove (including configuration)**'. 

Its just what ya need. If you know the name of the package, and want to be quick about it, the command listi showed you works perfect.

Additional info:

There's always two types of configuration for programs: **System-wide** configuration and **per-user** configuration:

** The system-wide configuration is stored in **/etc/fart** where **fart** is the name of some program.

** Per-user configuration is found in a hidden folder under your home directory with the name of the program. Its hidden because the name starts with a full stop. For example: **/home/weblordpepe/.gimp** for the GIMP program.

I know off the top of my head that pidgin makes a directory called /home/yourusername/**.purple** (cos Pidgin is part of a suite of libpurple programs that share the same config). There's a convention that programs follow sorta these days which is storing the configuration in a single configuration directory, called **.local**. VLC follows this convention and stores its crap in **/home/yourusername/.local/vlc**

---

### Post by Catbells on 2011-02-01
M'Weblord Pepe, That solved!  Many thanks for the crystal clear explanation, and the additional information gave me the context to really feel I understood what I was doing. . . . big . . . THANK YOU!

---

