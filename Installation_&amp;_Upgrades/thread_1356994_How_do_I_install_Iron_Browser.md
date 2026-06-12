---
title: "How do I install Iron Browser??"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by SVEN1 on 2009-12-16
In Ubuntu 8.10
I downloaded the tar file.
[http://www.srware.net/forum/viewtopic.php?f=18&t=835]("http://www.srware.net/forum/viewtopic.php?f=18&t=835")

---

### Post by wojox on 2009-12-16
When you move it you need to be in the directory you downloaded it.

First move it:

```
sudo mv iron-linux.tar.gz /opt/
```

Unpack:

```
tar xvf iron-linux.tar.gz
```

Move into directory:

```
cd /opt/iron-linux/
```

Read the READ ME

Then build:

```

./configure
make
sudo make install

```

---

### Post by mkvnmtr on 2009-12-16
The instruction given did not work for me. I double clicked on the file and the archive manager opened. Then I extracted it right where it was on the desk top. Then when I opened the file and cliked on the Iron file  the browser opened. Now I just have to find a place to put it and make an icon.

---

### Post by SVEN1 on 2009-12-16
Downloaded the file to the desktop, my documents etc. then ran the terminal
and this is what I get:

sven@sven-desktop:~$ sudo mv iron-linux.tar.gz /opt/
mv: cannot stat `iron-linux.tar.gz': No such file or directory
sven@sven-desktop:~$

---

### Post by wojox on 2009-12-16
Okay you have to be in the directory you downloaded it. Here's an easier way:

```
gksudo nautilus
```

Opens nautilus as root. Now copy and paste it in /opt and double click it.

---

### Post by SVEN1 on 2009-12-16
Tried that here's what I get:
sven@sven-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:10250): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root
--> file:///
--> file:///root/Desktop

(nautilus:10250): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 3 elements at quit time (keys above)

(nautilus:10250): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time
seahorse nautilus module shutdown
sven@sven-desktop:~$ 

I am a nooby when it comes to this.
So maybe a step by step instructions right from the start.
Lets say I am at the website and am ready to hit the download button in Firefox browser.

Appreciate all the help.

---

