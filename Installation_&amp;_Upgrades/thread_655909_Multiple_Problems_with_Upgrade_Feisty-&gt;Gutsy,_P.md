---
title: "Multiple Problems with Upgrade Feisty-&gt;Gutsy, PLEASE HELP"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by t.z0n3 on 2008-01-01
I know that this won't make much sense because it's all in here together, but I'm going to try and give as much information as possible.

I recently tried to update Feisty to Gutsy, and it would NEVER get everything. It would come up saying 1 file, 1 tiny file from the 'multiverse' section was unable to be fetched. My father said to simply uncheck the multiverse, because then it would not go looking for it. I did this, and the update worked. It puked midway through the update, so I had to restart my computer, and continue from there. It eventually finished, and I was running Gutsy. Yay.

We wanted to try the desktop effects first, to confirm that my 3D acceleration worked. I have an ATI Radeon 9600 card that was semi-supported under Feisty. The actual effects said the following when I clicked on either the 'normal' or the 'extra' options under 'appearance':

"The composite extension is not available."

We had no idea what that meant, but for shits and grins, we inserted the ubuntu disk into the drive, and ran the live CD version. The effects under THAT form of Gutsy worked on ALL levels. So something wasn't installed right.

We also had several third party programs that I'd tried to install via WINE that hadn't been supported under Feisty that apparently are under Gutsy. They installed themselves when I upgraded. I really didn't want them, so I prepared to blow away my installation, and reload from the disk (I had previously been using the 'Update' button in the update manager). 

We tried to copy my home directory configuration files (all are hidden) to a DVD. It would not copy the hidden files, but would say "Link To (insert file name here)". That's not what we wanted. So we tried copying these files to a NAS device. That didn't work either, although my Dad prescribed the villain in this case as SAMBA (which I don't particularly care about, he says he can work that out in a few days). In any case, we then tried to put the hidden files into a directory, and copy the directory over to a DVD. However, the hidden files were now 'unreadable'. So dad tried to make them readable by changing ownership. He used every command he knew (and several he learned about at the time) to copy them over. "chown" and "chgrp" (or something like that, I'm not good at this) were some of them he used. He made them recursive throughout all directories, and told them to do it to every file. In the console we were looking at, the list view confirmed EVERY FILE, hidden or not, as belonging to me. However, when we actually looked at the file's properties, it showed as belonging to root. No matter what we do, we can't make a backup of these files.

I'm very frustrated right now because nothing we've done has worked. I love Ubuntu very much, but I'd also love to wring it's little neck right now (if it had one). I'm at the point of just starting over completely, because I need my computer up and working so I can do my homework due when I get back from break. Somebody PLEASE help me on SOMETHING, anything. I just need some suggestions of what to do, or where to look for what to do, because we just aren't getting anywhere. :(

---

### Post by donatell0 on 2008-01-01
Its probably not possible now (that you have already upgraded), but you can add extra respositories (for example [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com")) in your /etc/apt/sources.list file, assuming some of your default repos are down. This will give alternate locations for Ubuntu to download the installation files. Google around for information on how to do this.

This happened to me too:

> "The composite extension is not available."

We had no idea what that meant, but for shits and grins, we inserted the ubuntu disk into the drive, and ran the live CD version. The effects under THAT form of Gutsy worked on ALL levels. So something wasn't installed right.

Unfortunately, I still have no idea what the solution is.

I also have no idea why you are unable to copy the hidden files from your home folder. But I suggest a compromise in case you are desperate to get to work. Forget the configuration files. This may not be a great option for you (but tell me why, if it is so), but it was fine for me. Just save your data files in a DVD and reinstall through the live CD. Since the 3d effects works in the live CD, I think your install (which will be a copy of the settings in the live CD bootup) will also have 3d effects working.

---

### Post by sonofusion82 on 2008-01-02
yeah.. i ran into problems when upgrading to gutsy recently.
eventually, I gave up and just download the live CD and perform a fresh install.

---

### Post by t.z0n3 on 2008-01-02
I'll try to add the extra repos, but at this point, I don't really see why. Thanks for your help. This thread is still open for help. I'm not doing anything to it just yet.

---

### Post by gerbman on 2008-01-02
> **t.z0n3 said:**
> We tried to copy my home directory configuration files (all are hidden) to a DVD. It would not copy the hidden files, but would say "Link To (insert file name here)". That's not what we wanted. So we tried copying these files to a NAS device. That didn't work either, although my Dad prescribed the villain in this case as SAMBA (which I don't particularly care about, he says he can work that out in a few days). In any case, we then tried to put the hidden files into a directory, and copy the directory over to a DVD. However, the hidden files were now 'unreadable'. So dad tried to make them readable by changing ownership. He used every command he knew (and several he learned about at the time) to copy them over. "chown" and "chgrp" (or something like that, I'm not good at this) were some of them he used. He made them recursive throughout all directories, and told them to do it to every file. In the console we were looking at, the list view confirmed EVERY FILE, hidden or not, as belonging to me. However, when we actually looked at the file's properties, it showed as belonging to root. No matter what we do, we can't make a backup of these files.

To save/reuse your hidden files/folders, I would give the following a try:

1) Change to home directory
```

cd ~

```

2) Get list of hidden files/folders to archive:
```

ls -a | egrep '^\.[^.].*$' > files.txt

```
files.txt should contain a line for every hidden file/folder.

3) Create archive of hidden stuff:
```

tar -cvzf home_hidden.tar.gz -T files.txt

```
home_hidden.tar.gz should contain all hidden files/folders...save this somewhere

4) Unpack in new home directory:
```

tar -xvzf home_hidden.tar.gz

```

---

### Post by t.z0n3 on 2008-01-02
Gerbman, whatever the heck that command just said worked. Granted that I haven't blown everything away yet, there's no reason it shouldn't work. Thank you so much. :)

---

### Post by gerbman on 2008-01-02
> **t.z0n3 said:**
> Gerbman, whatever the heck that command just said worked. Granted that I haven't blown everything away yet, there's no reason it shouldn't work. Thank you so much. :)

Glad it helped. Some quick explanations.

2) Get list of hidden files/folders to archive:
```

ls -a | egrep '^\.[^.].*$' > files.txt

```
"ls -a" lists all files/folders in the current directory (-a includes hidden ones). The "|" takes the output of ls and gives it as input to egrep. The "^\.[^.].*$" is a standard regular expression that matches a hidden file/folder. If you read the man page for egrep (type "man egrep" in the terminal) you should get a feel for what REs are.

3) Create archive of hidden stuff:
```

tar -cvzf home_hidden.tar.gz -T files.txt

```
A standard tar command to create a gzipped tar archive. -T reads the input file list from the given file.

Not sure if that helps or if you cared to read it, but there it is.

---

### Post by t.z0n3 on 2008-01-09
I'm still trying to figure that code out, so I did care a lot. Thanks. ^_^

---

