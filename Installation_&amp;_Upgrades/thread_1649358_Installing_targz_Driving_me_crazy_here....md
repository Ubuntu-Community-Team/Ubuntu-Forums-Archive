---
title: "Installing targz? Driving me crazy here..."
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by johangusten on 2010-12-20
So, i installed Ubuntu again (might say i have crawled back) and now i'm dualbooting with Windows 7. I have never been quite the master at Linux, and for being the most "user-friendly" OS, installing files in Ubuntu baffles me.

The file is a .targz which i assume is exactly the same as a tar.gz, all the threads everywhere has said something similar to 'type #cd 'application name' in terminal# or such, but i can't operate the terminal at all, since i don't even know what the application name is when it's compressed. Is there not anyone sane?
A begnner's guide would be helpful ;)
Maybe i'll *stay* for more than 2 days on linux this time.

Here's the soft if anyone needs me to be more specific.
[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

Thank you all in advance.
Now i'm late.

---

### Post by iponeverything on 2010-12-20
just double click on it, extract it, open folder it creates and look at any readme or install files you find.

---

### Post by lmarmisa on 2010-12-20
Welcome to the forums.

If you wish to see the files included in that .targz file, open a terminal and type these commands:

```

cp yourfile.targz yourfile.tar.gz
gzip -d yourfile.tar.gz
tar tvf yourfile.tar

```If you want to extract the files of the tar file, type this command:

```

tar xvf yourfile.tar

```

---

### Post by ronnielsen1 on 2010-12-20
What are you trying to install? There might be an easier way

---

### Post by johangusten on 2010-12-20
> **ronnielsen1 said:**
> What are you trying to install? There might be an easier way
See the link in the OP.
It's a streaming thingie for streaming music to my xbox.

---

### Post by johangusten on 2010-12-20
> **iponeverything said:**
> just double click on it, extract it, open folder it creates and look at any readme or install files you find.

Okay i'll attach an image of the extracted file's content, none of it seems installable.

[IMG]http://oi51.tinypic.com/53nuyh.jpg[/IMG]


'linux' folder contains an exe by the way (for some reason)...

---

### Post by johangusten on 2010-12-20
> **lmarmisa said:**
> Welcome to the forums.

If you wish to see the files included in that .targz file, open a terminal and type these commands:

```

cp yourfile.targz yourfile.tar.gz
gzip -d yourfile.tar.gz
tar tvf yourfile.tar

```If you want to extract the files of the tar file, type this command:

```

tar xvf yourfile.tar

```
I already extracted it manually, and i just don't know if this would help me in any way... but how the hell does terminal know where the files are located? Are there no type of \location\folder\file.etc thingies needed? 
:roll: I don't think i'm a linux guy

---

### Post by ronnielsen1 on 2010-12-20
right click on the PMS.sh

Choose properties

Click permissions tab and make sure that Allow Executing file as program is marked 

Double click the PMS.sh file 

Click Run


But this is for a PS3

---

### Post by ronnielsen1 on 2010-12-20
or in terminal:

cd philip/Dokument/pms-linux-1.20.412/linux 



chmod +x PMS.sh

./PMS.sh

---

### Post by ronnielsen1 on 2010-12-20
I found these links that might help with an xbox
[http://lifehacker.com/392336/stream-music-from-ubuntu-to-an-xbox-360](http://lifehacker.com/392336/stream-music-from-ubuntu-to-an-xbox-360)
[http://ubuntuforums.org/showthread.php?t=346098](http://ubuntuforums.org/showthread.php?t=346098)
[http://ubuntuforums.org/showthread.php?t=632428](http://ubuntuforums.org/showthread.php?t=632428)

---

### Post by ronnielsen1 on 2010-12-20
> I don't think i'm a linux guy

Don't give up. It becomes worth it once it starts sinking in.

---

### Post by ronnielsen1 on 2010-12-20
I know you're wanting to stream music to your xbox, but if you have a newer tv, you might check out [Boxee]("http://www.boxee.tv/"). It might meet some of your needs. It does music too.

They have downloads for Ubuntu which are easy to install

Click on Make a Boxee tab > Downloads > Other

---

