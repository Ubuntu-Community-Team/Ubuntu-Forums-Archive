---
title: "How to compile tar.gz files"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by ultimate_aektzis on 2008-07-17
I found a game in tar.gz format.After googling I found that this is the source code of the game and I have to compile it via terminal.The question is which are those commands that allow me to compile the game.
thanks in advance

---

### Post by tuxxy on 2008-07-17
```
tar xvzf gamename.tar.gz

```
Then it should created a directory so move to that dir;

```
cd dirname
```

Then you should run de configure script;

```
sudo ./configure
```

Then compile it;

```
sudo make
```

Then finally;

```
sudo make install
```

---

### Post by ultimate_aektzis on 2008-07-17
Hmm,when I run the 1st command the following message appears

> periklis@p:~$ tar xvzf scilab-4.1.2.bin.linux-i686.tar.gz
tar: scilab-4.1.2.bin.linux-i686.tar.gz: &#916;&#949;&#957; &#949;&#943;&#957;&#945;&#953; &#948;&#965;&#957;&#945;&#964;&#942; open: No such file or directory
tar: &#932;&#959; &#963;&#966;&#940;&#955;&#956;&#945; &#948;&#949;&#957; &#949;&#943;&#957;&#945;&#953; &#949;&#960;&#945;&#957;&#959;&#961;&#952;&#974;&#963;&#953;&#956;&#959;: &#964;&#949;&#961;&#956;&#945;&#964;&#953;&#963;&#956;&#972;&#962; &#964;&#974;&#961;&#945;
tar: Child returned status 2
tar: &#922;&#945;&#952;&#965;&#963;&#964;&#941;&#961;&#951;&#963;&#949; &#964;&#959; &#963;&#966;&#940;&#955;&#956;&#945; &#949;&#958;&#972;&#948;&#959;&#965; &#945;&#960;&#972; &#960;&#961;&#959;&#951;&#947;&#959;&#973;&#956;&#949;&#957;&#945; &#963;&#966;&#940;&#955;&#956;&#945;&#964;&#945;
periklis@p:~$ 



If you dont understand something just tell me to translate:)

---

### Post by Partyboi2 on 2008-07-17
If you are trying to install Scilab, the Matrix-based scientific software it is in the ubuntu repos.
```
 sudo apt-get install scilab
```Edit: Here is some info on compiling from source
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

After you have extracted it, read the readme or install file to see how to install it as not all programs are installed with: 
./configure
make
sudo make install

---

### Post by ultimate_aektzis on 2008-07-17
I know about the repos ;)
But as a newbie I want to try compilation.Its very "funny",as far as I know.:)

---

### Post by Vivaldi Gloria on 2008-07-17
> **ultimate_aektzis said:**
> I found a game in tar.gz format.After googling I found that this is the source code of the game and I have to compile it via terminal.The question is which are those commands that allow me to compile the game.
thanks in advance

Make sure that you have build-essential installed.

Right click on tar.gz and choose extract it (or whatever it's called in the english ubuntu).

Then read the installation instructions in the folder.

---

### Post by Partyboi2 on 2008-07-17
> **ultimate_aektzis said:**
> Hmm,when I run the 1st command the following message appears



If you dont understand something just tell me to translate:)
Did you change directory to where the file is located? For example if the downloaded file is on the Desktop you would first need to cd to that directory before trying to extract it.
```
cd ~/Desktop
```then
```
tar xvzf scilab-4.1.2.bin.linux-i686.tar.gz
``` if you notice the file that you downloaded is a binary file which has a different install process then if you were compiling from source (check the readme file) If you are wanting to compile from source you would need to download the source version. You can download that from [[COLOR=Blue]here[/COLOR]]("http://www.scilab.org/download/index_download.php")
To install the binary file after you have extracted it and change directory (cd) into the newly created scilab-4.1.2 folder you would type
```
make
```
then to run it you would need to change into the /scilab-4.1.2/bin directory and type
```
./scilab
```

---

### Post by steveneddy on 2008-07-17
You have to tell the teminal where the application is first.

If you downloaded the .tar.gz file to the desktop, then in terminal

```
cd ~/Desktop
```

then do the 

./configure
sudo make 
sudo make install
sudo make clean

You must always cd (change directory) to the location of the files that you want to work with.

---

### Post by ultimate_aektzis on 2008-07-20
I put the file in home folder so I dont need cd ;).I think that the problem is the

>  if you notice the file that you downloaded is a binary file which has a different install process then if you were compiling from source (check the readme file) If you are wanting to compile from source you would need to download the source version. You can download that from here
To install the binary file after you have extracted it and change directory (cd) into the newly created scilab-4.1.2 folder you would type


I will try again and for further information I will ask you again.thank you all:)

---

