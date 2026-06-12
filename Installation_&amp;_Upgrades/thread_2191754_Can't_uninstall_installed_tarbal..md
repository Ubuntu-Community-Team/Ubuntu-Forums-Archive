---
title: "Can't uninstall installed tarbal."
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by Rubeast on 2013-12-04
I'm relatively new to Linux and have gathered a LOT of info from these forums!
I installed Kubuntu a month ago and I really like it.

Today I downloaded and installed the copy.com software on my system. (It is something like dropbox)
In the install-wizard it asked the folder I would like to use to sync data with.
I chose the home folder and it automatically went to the next step, I couldn't go back and change it, so I cancelled the wizard, but it already was too late.

I can't move the folder now. It gives me "Failed to move your copy folder" message.
It also seem to have messed with my permissions, but am not really sure.
So I would like to uninstall. But I can't find an uninstaller script.
This is the content of the directory: [http://imgur.com/z4uWIfI](http://imgur.com/z4uWIfI)
You can find the download here: [https://copy.com/install/linux/Copy.tgz](https://copy.com/install/linux/Copy.tgz)
I also tried some commands with make, but I can't seem to get it working.

---

### Post by Lars Noodén on 2013-12-04
There isn't an uninstall script.  That's one of the big reasons why it is so highly recommended to stick only with packages, preferably those from the repositories.  

How exactly did you do the installation? The one tarball you have seems to have pre-compiled binaries.  If you copied those manually, then you'll have to uninstall them manually, too.  If all you did was unpack the tarball and leave things there, then all you have to do is delete that directory and its contents.

---

### Post by heir4c on 2013-12-04
There is nothing to uninstall because it start up with the executble file: CopyAgent
You had to make a account before you use it. So, there must be a account online, no?
So, go to your account and I think you can change it there. 
I downloaded it and extract it. And I could start it up but I don't created a account and close the window. 
So I don't now how it go further.

---

### Post by Rubeast on 2013-12-04
> **Lars Noodén said:**
> There isn't an uninstall script. That's one of the big reasons why it is so highly recommended to stick only with packages, preferably those from the repositories. 


How exactly did you do the installation? The one tarball you have seems to have pre-compiled binaries. If you copied those manually, then you'll have to uninstall them manually, too. If all you did was unpack the tarball and leave things there, then all you have to do is delete that directory and its contents.




I just had to run the CopyAgent file to start the wizard.


But, your post got me thinking.
I seemed that it didn't really install files to my system.
It just ran that one CopyAgent file each time.


To uninstall Copy I did the following:
- Remove the copy directory that I extracted from the archive.
- Remove directory /home/<user>/.copy
- Remove directory /home/<user>/.config/Barracuda..something
- Remove the autostart input.

Edit: 
I seems that re-installing it doesn't go so well.
I'm also experiencing other problems with my system so I think I'm going to do a clean install of kubuntu.
Do you guys maybe recommend some backup/snapshotting tools? :)

---

