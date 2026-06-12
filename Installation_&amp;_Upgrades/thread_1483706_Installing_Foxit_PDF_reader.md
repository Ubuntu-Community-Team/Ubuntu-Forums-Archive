---
title: "Installing Foxit PDF reader"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by bradydehart on 2010-05-14
I am brand new to Linux and I can't get Foxit to install. I followed the instructions on this site "https://help.ubuntu.com/community/Foxit " but here is what is happening.

paola@paola-laptop:~$ rm FoxitReader10_Linux_enu_i386.tar.bz2
paola@paola-laptop:~$ wget -c [http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2](http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2)
--2010-05-14 20:11:11--  [http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2](http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2)
Resolving mirrors.foxitsoftware.com... 68.178.243.64
Connecting to mirrors.foxitsoftware.com|68.178.243.64|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdn02.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2](http://cdn02.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2) [following]
--2010-05-14 20:11:11--  [http://cdn02.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2](http://cdn02.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2)
Resolving cdn02.foxitsoftware.com... 208.109.191.4, 68.178.243.64
Connecting to cdn02.foxitsoftware.com|208.109.191.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1920565 (1.8M) [application/x-bzip2]
Saving to: `FoxitReader10_Linux_enu_i386.tar.bz2'

100%[======================================>] 1,920,565   3.19M/s   in 0.6s    

2010-05-14 20:11:12 (3.19 MB/s) - `FoxitReader10_Linux_enu_i386.tar.bz2' saved [1920565/1920565]

paola@paola-laptop:~$ tar -jxvf FoxitReader10_Linux_enu_i386.tar.bz2 
tar: Record size = 8 blocks
Foxit/
Foxit/FoxitReader
Foxit/dependencies_20090118.txt
Foxit/Readme_20090118.txt
Foxit/fum.fhd
paola@paola-laptop:~$ sudo mkdir /opt/foxit
mkdir: cannot create directory `/opt/foxit': File exists
paola@paola-laptop:~$ sudo mv Foxit /opt/foxit/
mv: cannot move `Foxit' to `/opt/foxit/Foxit': Directory not empty
paola@paola-laptop:~$ rm FoxitReader10_Linux_enu_i386.tar.bz2
paola@paola-laptop:~$ wget -c [http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2](http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2)
--2010-05-14 20:19:16--  [http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2](http://mirrors.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2)
Resolving mirrors.foxitsoftware.com... 68.178.243.64
Connecting to mirrors.foxitsoftware.com|68.178.243.64|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdn02.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2](http://cdn02.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2) [following]
--2010-05-14 20:19:17--  [http://cdn02.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2](http://cdn02.foxitsoftware.com/pub/foxit/reader/desktop/unix/1.x/1.0/enu/FoxitReader10_Linux_enu_i386.tar.bz2)
Resolving cdn02.foxitsoftware.com... 208.109.191.4, 68.178.243.64
Connecting to cdn02.foxitsoftware.com|208.109.191.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1920565 (1.8M) [application/x-bzip2]
Saving to: `FoxitReader10_Linux_enu_i386.tar.bz2'

100%[======================================>] 1,920,565   3.43M/s   in 0.5s    

2010-05-14 20:19:17 (3.43 MB/s) - `FoxitReader10_Linux_enu_i386.tar.bz2' saved [1920565/1920565]

paola@paola-laptop:~$ tar -jxvf FoxitReader10_Linux_enu_i386.tar.bz2 
tar: Record size = 8 blocks
Foxit/
Foxit/FoxitReader
Foxit/dependencies_20090118.txt
Foxit/Readme_20090118.txt
Foxit/fum.fhd
paola@paola-laptop:~$ sudo mkdir /opt/foxit
mkdir: cannot create directory `/opt/foxit': File exists
paola@paola-laptop:~$ sudo mv Foxit /opt/foxit/
mv: cannot move `Foxit' to `/opt/foxit/Foxit': Directory not empty



The third step will not work because it says that it can not move the file because the directory is not empty. What can I do to work around this?

Thank you so much for all your help!

---

### Post by Matt G Dalian on 2010-05-20
Hi,

I just installed foxit myself on my netbook running Ubuntu 10.04 Lucid Lynx.
I also followed the instructions on:
[https://help.ubuntu.com/community/Foxit](https://help.ubuntu.com/community/Foxit)

But a little differently, part terminal part Nautilus (Ubuntu's file manager).

Here's what I did:

1. Download the tar.bz2 from
[http://www.foxitsoftware.com/downloads/index.php](http://www.foxitsoftware.com/downloads/index.php)
(It's towards the bottom of the page, under Foxit Reader for Desktop Linux)

2. That will probably go in your ~/Downloads folder as FoxitReader-1.1.0.tar.bz2

Right click on the file and click on "extract here"

3. That will extract everything to a folder in ~/Downloads called 1.1-release. I renamed that folder to foxit (just right-click on the folder and select "rename")

4. Now we pick up where the instructions left off:
Move the foxit folder to the /opt directory:
```
$ sudo mv ~/Downloads/foxit /opt
```

5. Now let's make a link between /opt/foxit/FoxitReader and the command /usr/bin/foxit :
```
$ sudo ln -s /opt/foxit/FoxitReader /usr/bin/foxit
```

6. The last step is (probably) to make it so PDFs automatically open with Foxit Reader.
To do this, right click on any .pdf file and click on Properties, then click on the 4th tab that says "Open With"
You probably won't see Foxit Reader as a choice, so click on "Add" and enter a custom command: /usr/bin/foxit

And you're done.

---

