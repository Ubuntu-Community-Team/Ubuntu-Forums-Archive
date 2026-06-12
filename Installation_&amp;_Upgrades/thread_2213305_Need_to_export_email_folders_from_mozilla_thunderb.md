---
title: "Need to export email folders from mozilla thunderbird ubuntu"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by Bryant_Arrington on 2014-03-25
I am installing everything from Ubuntu 13.04 Inspiron Dell to a Dell Inspiron with Linux Mint 16 Mate desktop.  I can't figure out how to get all the folders I have in Mozilla thunderbird (about 10) exported and then into the Linux Mint machine.

Any help please???

thanks!!!

---

### Post by kc1di on 2014-03-26
go to file manager click on show hidden files find the .thunderbird folder copy the .thunderbird/<filename>.default/Mail/Local Folders  file and past it to the same place on the thunderbird install on the other machine.  your folders and mail should be there.  (use a usb stick , cloud storage , or cd  to transfer the file. or if the machines are networked together you should be able to copy that file over.) good luck

---

### Post by Bryant_Arrington on 2014-03-26
Sorry, I'm new to Ubuntu.  Where is or how do I access File Manger?  Thanks very much!!
Edit - I found show hidden files, but can't find the mozilla folder.  I found 4 mozilla folders but can't find the mail folder.

---

### Post by kc1di on 2014-03-26
your not looking for Mozilla but .thunderbird it's a hidden folder in your home directory.

---

### Post by Bryant_Arrington on 2014-03-26
Thanks for your patience.  I have search for Thunderbird in computer and find 3 thunderbird folders and four with other add on names like, thunderbird-addons, thunderbird-local-en, thunderbird-locale-en-us, thunderbird-globalmenu, thunderbird-gnomesupport.

I do not find inside of any of them  "<filename>.default/Mail/Local Folders  file".   What is the most likely name for <filename>??

---

### Post by coffeecat on 2014-03-26
kc1di has already told you where the thunderbird folder is:

> **kc1di said:**
> your not looking for Mozilla but .thunderbird it's a hidden folder in your home directory.

Open a file browser window in your home directory. If you are using Ubuntu with Unity simply click on the second icon down in the launcher. Now either press ctrl-H to show hidden files/folders or use the menu to select show hidden folders. The folder you are looking for has a leading dot ".thunderbird" - that is what distinguishes hidden files/folders in Linux.

The <filename> part of <filename>.default is a random string and is different for each installation.

---

### Post by Bryant_Arrington on 2014-03-26
Thanks, your description did it for me.  Got it!!!

---

### Post by kc1di on 2014-03-27
Glad you got , enjoy :)

---

