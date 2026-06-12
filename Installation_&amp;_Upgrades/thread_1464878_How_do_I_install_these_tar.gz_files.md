---
title: "How do I install these tar.gz files"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by CShaum on 2010-04-28
I have read much on this on this subject but so far it has never worked. I'm trying to install X-lite_install.tar.gz. How does one make it work??:confused: I much appreciate your help. I got it extracted onto my desktop. But how do I go from here?? Does one use the root terminal??

---

### Post by randumnumber on 2010-04-28
In order to use the root terminal you goto applications>accessories>terminal this will open a terminal typing ```
sudo
``` before a command will execute it as root, it will ask you for your root password, so if you need to install something as root you would do for instance:
```
sudo apt-get install apache2
```
this will install apache2 as a root user

pwd - prints your current working directory
cd .. will change your directory to the parent directory
cd will bring you to your home directory
ls will list the files in your current directory
cd /file/path will take you to file path

so you have a file extracted on your desktop you should open terminal and go there by typing
```
cd Desktop
```
Then you will be able to see the files on yoru desktop with the command ls
navigate to the folder you are trying to install and follow the instructions on how to install the file from there...

if there is a make file you need to make it and then install it...here is a guide on how to do that:
[http://ubuntuforums.org/archive/index.php/t-58257.html](http://ubuntuforums.org/archive/index.php/t-58257.html)
this is a link on how to decompress a tar.gz file
[http://ubuntuforums.org/showthread.php?t=416444](http://ubuntuforums.org/showthread.php?t=416444)

---

### Post by CShaum on 2010-04-28
I followed the terminal path to open a terminal but I can't get it to respond to any commands. Its says terminal at the top and a blank screen with a blinking cursor. If I go to system tools and use root terminal I get a responds but is that the terminal I should be using??

---

### Post by randumnumber on 2010-04-29
This is very strange. What version of ubuntu are you using? I have 9.04 and 9.10 installed, and i don't have a "root terminal" or anything terminal related under system tools..I did a quick search if you are using 8.10 then you are in the correct place with the root terminal, but be extreamly careful, removing or altering things in root can screw up your system. if you are just installing something i think you should be ok. 

one question:
the regular terminal has a blinking curser but doesnt respond to anything? does it have something like server@server:~ or is it just a blinking curser?

---

### Post by neotifa on 2010-04-29
You can extract them directly (right click -> extract here). Later follow the readme file and install the program.

---

### Post by CShaum on 2010-04-29
I'm using ver. 9.10. I got the root through the main menu and tick it. and now its in my system tools. My regular terminal says nothing, just a blank screen and a blinking cursor. I tried it again typed in sudo and nothing happen, the cursor just move down to the next line. I typed in all the commmand as directed nothing happen. I read what neotifa said to read but still can't figure out what is going on. My regular terminal must not be working the way it should. I admit I am new at this so please bear with me. I do appreciate your input.

---

### Post by randumnumber on 2010-04-29
That is weird i'm not sure what is wrong, it has never happened to me before. That might be something you should check into google something like "no prompt at terminal" but for now, you should be able to use the root terminal you are talking about.

here is a guide i have found that might help you as i have never used or installed xlite:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1014094](http://www.uluga.ubuntuforums.org/showthread.php?t=1014094)

Hope this helps.
If you encounter any errors when trying to execute the program this means you are missing libraries that support the program, it should list them for you and you can goto System>admin>synaptic from there you can search for the packages you need.

p.s. if you are new to linux here are a few tips:
ubuntuforums is awesome and google is your best friend

---

### Post by CShaum on 2010-05-02
Can you tell me what I'm doing wrong? I'm using the root terminal. Like I wrote earlier I do have extracted on my desktop and also I install apache2 as stated earlier. no problems there. Here is the list that I typed in my terminal: 
Setting up apache2 (2.2.12-1ubuntu2.2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@carl-laptop:/home/carl# cd Desktop
root@carl-laptop:/home/carl/Desktop# xtensoftphone
xtensoftphone: command not found
root@carl-laptop:/home/carl/Desktop# install
install: missing file operand
Try `install --help' for more information.
root@carl-laptop:/home/carl/Desktop# xten-xlite
xten-xlite: command not found
root@carl-laptop:/home/carl/Desktop# 
I tried, install and xtensoftphone.   xten-xlite is the name of the extracted file on my desktop. Any advice??

---

### Post by CShaum on 2010-05-02
I did a google search and got my regular terminal going. CTRL+C. Got it back and running. CTRL+C stops all script and commands. And now I have a prompt. That is solved! But no luck with these tar packages. Sure be nice if someone would invent a better way to install these things for dumbing like me. But I do want to learn how to install these things.

---

### Post by CShaum on 2010-05-02
I tried the link that was mentioned.  And I found help there. I can execute it but it won't install. I think I'll move my problem to that other thread. Thanks

---

### Post by randumnumber on 2010-05-03
no problem, just remember if it is a normal install file you should run a ./configure this configures the install files to work with your machine, then you will make the install file with make install command, then you actually install the program....you have solved your tar.gz file problems, you should search around for how to use a make file.


good luck

---

### Post by randumnumber on 2010-05-03
> **CShaum said:**
> Can you tell me what I'm doing wrong? I'm using the root terminal. Like I wrote earlier I do have extracted on my desktop and also I install apache2 as stated earlier. no problems there. Here is the list that I typed in my terminal: 
Setting up apache2 (2.2.12-1ubuntu2.2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@carl-laptop:/home/carl# cd Desktop
root@carl-laptop:/home/carl/Desktop# xtensoftphone
xtensoftphone: command not found
root@carl-laptop:/home/carl/Desktop# install
install: missing file operand
Try `install --help' for more information.
root@carl-laptop:/home/carl/Desktop# xten-xlite
xten-xlite: command not found
root@carl-laptop:/home/carl/Desktop# 
I tried, install and xtensoftphone.   xten-xlite is the name of the extracted file on my desktop. Any advice??

You need to change directory to xten-xlite so 
```
cd xten-xlite
```
then run
```
./configure
```
then after that run 
```
make && make install
```
so basically from inside the xten-xlite file you will run configure then you will make and make the install file for yoru program.. then if you try to execute it it should work

---

### Post by CShaum on 2010-05-03
I tried ./configure but it bash it. I copied the terminal unless I didn't do something right.
carl@carl-laptop:~$ cd Desktop
carl@carl-laptop:~/Desktop$ tar -zxvf X-Lite_Install.tar.gz
xten-xlite/xtensoftphone
xten-xlite/README
carl@carl-laptop:~/Desktop$ cd xten-xlite
carl@carl-laptop:~/Desktop/xten-xlite$ ./configure
bash: ./configure: No such file or directory
carl@carl-laptop:~/Desktop/xten-xlite$ make
make: *** No targets specified and no makefile found.  Stop.
carl@carl-laptop:~/Desktop/xten-xlite$ 
How do I go from here??? Thanks

---

### Post by steveneddy on 2010-05-03
read the READ ME file to see how they recommend installing this software.

---

### Post by steveneddy on 2010-05-03
I DLed from here:

[http://linux.softpedia.com/progDownload/X-Lite-Download-5595.html](http://linux.softpedia.com/progDownload/X-Lite-Download-5595.html)

extracted to my desktop and there are only two files in there:

READ ME
xtensoftphone

That's it.

I simply double clicked the **xtensoftphone** and it launched with a GUI.

How many files are in your folder? the same as mine? Just two?

Seems cool - what does this thing do?

EDIT:

I read the above post and you have two files also.

Just double click the launcher and it will launch. Easy peasy.

---

### Post by CShaum on 2010-05-03
Wow!! what a deal. I tried I don't know how many times I double clicked on it and it never launched. When I saw your thread, I been there and tried that, but it didn't work. And so I tried again and it launched it. Lot of sweat for nothing. The way it looks it doesn't really install as a program. And that is what I was wanting to do. Thanks, for all your input!! problem solved

---

### Post by steveneddy on 2010-05-03
Glad I could help.

---

### Post by kenLinux23 on 2010-05-12
Can Find solution to make xten work in Ubuntu? Tried someone around but it does not work.


Thanks,

Ken

---

### Post by CShaum on 2010-05-12
I experience the same thing. Once I was able to launch it. Than it didn't work worth a hoot. Might have to try X-Lite forum for a solution.

---

