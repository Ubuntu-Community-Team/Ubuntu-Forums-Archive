---
title: "installing .deb files from CD collection"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by David J Bush on 2007-02-17
[COLOR=Indigo][FONT=Georgia]I have Kubuntu Edgy preinstalled. I also have 14 CDs of Debian Sarge. My modem is not working yet. (I posted this from a different machine.) I would like to find a way to install some .deb packages using Adept or something similar. I saw on the page [https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal) a way to do just that, but it requires dpkg-scanpackages, which I do not have. It's not listed as either an installed or uninstalled package according to Adept. There is no man page for it.

I realize Sarge is old, but like I said, my modem isn't working yet. The preinstalled Edgy doesn't have much. When I was running Sarge on a different machine, I was able to use aptitude and it used the CD collection as a repository. It would tell me "insert disc N" at the appropriate moments. I didn't have to copy any files nor run any scripts beforehand. It just read the repository straight off the CDs. Is there some way to get Adept, or aptitude, or some user-friendly installation manager to do the same thing under Edgy?

I would have posted this in the Forum "Repositories & Backports" but a sticky there warned me:
 [/FONT][/COLOR]
                                 ****Before You Post****             
                          This forum is for the installation, configuration, and usage of software supported by Ubuntu. That is, all the software in the **main** and **restricted** repositories.
 
 Please only post relevant topics here.

[COLOR=Indigo][FONT=Georgia]It seems odd that other repositories are regarded as "not relevant," but that's what it says.

Thanks for your time!
[/FONT][/COLOR]

---

### Post by solar george on 2007-02-17
Use the Add cdrom option in the edit menu in synaptic.

Or
```
sudo apt-cdrom add
```
in the terminal.

---

### Post by David J Bush on 2007-02-18
[COLOR=Indigo][FONT=Georgia][SIZE=3]Here is an excerpt from my terminal session. I used disc 1 of 14.[/SIZE]
[FONT=Courier New][COLOR=Black]
david@kubuntu:~$ sudo apt-cdrom add
Password:
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press Enter
Mounting CD-ROM...
Identifying.. [55444b048138eee203661d89d2975e89-2]
Scanning disc for index files...
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
E: Unable to locate any package files, perhaps this is not a Debian disc
[/COLOR][/FONT][/FONT][/COLOR][COLOR=Indigo][FONT=Georgia][FONT=Courier New][COLOR=Black]david@kubuntu:~$ man synaptic
No manual entry for synaptic
[/COLOR][/FONT][/FONT][/COLOR][COLOR=Indigo][FONT=Georgia][FONT=Courier New][COLOR=Black]david@kubuntu:~$ which synaptic
[/COLOR][/FONT][/FONT][/COLOR][COLOR=Indigo][FONT=Georgia][FONT=Courier New][COLOR=Black]david@kubuntu:~$

[COLOR=Indigo][FONT=Georgia][SIZE=3]On the CD itself, it says: Produced by LAN Comp Systems, Issaquah, Washington USA, Ics.issaquah.wa.us[/SIZE]
[/FONT][/COLOR][/COLOR][/FONT][/FONT][/COLOR]

---

### Post by David J Bush on 2007-02-18
[COLOR=Indigo][SIZE=3][FONT=Georgia]To anticipate your possible responses, I did try apt-cdrom again, using the -a option for a more thorough scan of the disk. Same result.

To show you what the directory structure of the disk looks like, here is how the mount point /cdrom/ looks. I added the underscores and slashes.

[COLOR=Black][SIZE=2][FONT=Courier New].disk\
debian\
dists__\
doc_____\
install__> These are all subfolders or links.
isolinux/
pics___/
pool__/
tools/
autorun.bat
autorun.inf
md5sum.txt
README.html
[/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][COLOR=Indigo][SIZE=3][FONT=Georgia][COLOR=Black][SIZE=2][FONT=Courier New]README.mirrors.html
[/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][COLOR=Indigo][SIZE=3][FONT=Georgia][COLOR=Black][SIZE=2][FONT=Courier New]README.mirrors.txt
[/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][COLOR=Indigo][SIZE=3][FONT=Georgia][COLOR=Black][SIZE=2][FONT=Courier New]README.txt

[COLOR=Indigo][SIZE=3][FONT=Georgia]Here is part of the folder /cdrom/pool/main/. These are all subfolders.

[COLOR=Black][SIZE=2][FONT=Courier New]a
b
c
d
...

[FONT=Georgia][SIZE=3][COLOR=Indigo]These subfolders in turn contain folders for specific packages, and those contain the .deb files.

It all worked just fine under Debian. Why won't apt-cdrom read my disc? Thanks again.
[/COLOR][/SIZE][/FONT][/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR][/FONT][/SIZE][/COLOR]

---

### Post by David J Bush on 2007-02-19
[COLOR=Indigo][SIZE=3][FONT=Georgia]This thread gets a lot of volume. A post 20 hours old might be overlooked. So, at the risk of being rude, I repeat my question: Why doesn't **apt-cdrom** work for me? How can I get it to work?

Thanks
[/FONT][/SIZE][/COLOR]

---

### Post by justleen on 2007-02-19
how about dpkg -i and install the package without apt?

---

### Post by David J Bush on 2007-02-19
[COLOR=Indigo][SIZE=3][FONT=Georgia]Is dpkg going to read a Debian CD? The man page for dpkg doesn't mention that capability. apt-cdrom, on the other hand, is specifically supposed to read a Debian CD and add its packages to the available repositories. I would like to understand why apt-cdrom does not work for me. Has no one else encountered the same problem? Official Debian 3.1 Sarge should be readable by apt-cdrom under Kubuntu. Is this a bug? If so, I should report it.

WRT transferring .deb files to the hard drive and then installing them, it might be possible to do this, but the only documentation I found detailing the procedure (see the link in my first post) requires the tool dpgk-scanpackages, which is not installed on my machine. In any event, I believe I should be able to use adept or aptitude or another user-friendly installation manager.
[/FONT][/SIZE][/COLOR]

---

