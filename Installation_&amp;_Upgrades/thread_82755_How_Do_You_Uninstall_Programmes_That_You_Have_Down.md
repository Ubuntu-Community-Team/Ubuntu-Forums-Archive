---
title: "How Do You Uninstall Programmes That You Have Downloaded?"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by rickon on 2005-10-27
Hi, all have looked in the various help sections, but am still unsure how to uninstall programmes.  That programmes already installed and ones you have downloaded.

Appreciate any help

Thanks 

Rickon

---

### Post by nocturn on 2005-10-27
[QUOTE=rickon]Hi, all have looked in the various help sections, but am still unsure how to uninstall programmes.  That programmes already installed and ones you have downloaded.

Appreciate any help

Thanks 

Rickon[/QUOTE]

I assume you are talking about self-compiled programs (debs can be removed via synaptic).

The ones you already have, use make uninstall in their src directory.  For new installs, I recommend checkinstall, it generates debs for make install.

---

### Post by rickon on 2005-10-27
[QUOTE=nocturn]I assume you are talking about self-compiled programs (debs can be removed via synaptic).

The ones you already have, use make uninstall in their src directory.  For new installs, I recommend checkinstall, it generates debs for make install.[/QUOTE]

Hi, thanks for the reply.  I understand the first sentence about synaptic and can use that but I do not understand the second sentence.  Do I use the terminal? .......and what and how is the src directory......sorry if I seem so dumb!

Is there a guide about this somewhere?

Thanks 

Rickon

---

### Post by Pablo_Escobar on 2005-10-27
1. If You installed some application via apt-get or via Synaptic then Synaptic remove packages -> that's dead simple :)
2. If You compiled something by hand (downloaded source code, ./configure, make, make install) then it's a bit tricky. 
First of all You need to have the directory from which You compiled the program intact. Then you need to "cd" to that directory and "sudo make uninstall".
If You deleted that directory, then it's a big problem, there are no easy way to do it. :(

---

### Post by nocturn on 2005-10-27
[QUOTE=rickon]Hi, thanks for the reply.  I understand the first sentence about synaptic and can use that but I do not understand the second sentence.  Do I use the terminal? .......and what and how is the src directory......sorry if I seem so dumb!

Is there a guide about this somewhere?

Thanks 

Rickon[/QUOTE]

You don't seem dumb at all!  

How did you install the programs you mentioned?  This will determine how to get rid of them.

---

### Post by rickon on 2005-10-27
Thanks for the reply:  I installed the programmes by downloading to the desktop and then following the instructions in the easy user guide.

For example Limewire...it appears in the applications list but then I get the following error:

Cannot launch entry

Details: Failed to execute child process "runLime.sh" (No such file or directory)

Thats why I thought it best to uninstall and start again.

Regards

Rickon

---

