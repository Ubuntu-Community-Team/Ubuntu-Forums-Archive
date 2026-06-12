---
title: "Help installing TAR.GZ files (how?)"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2005-05-28
Can you helpful people in cyberspace help me to install some programs I have downloaded, both of which have the tar.gz extension. Tried al manner of ways with no luck so far. Cheers

---

### Post by Xian on 2005-05-28
Here's one to check out: [Installing Linux Software](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by Julian David Pitt on 2005-05-28
[QUOTE=Xian]Here's one to check out: [Installing Linux Software](http://www.tuxfiles.org/linuxhelp/softinstall.html)[/QUOTE]
Hi Xian
My that was a quick response indeed. I will try out the instructions you provided and see how I get on. Thanks for your help my friend.
Julian

---

### Post by Kakason on 2005-05-29
Wow, that's a really cool website.
But I have 1 Question.
I'm installing Ruby.
I got the Ruby-1.8.2.tar.gz
I do this
tar xvzf /home/username/ruby-1.8.2.tar.gz
Then a list of things came, then I do this
cd /home/username/ruby-1.8.2
then I do this
./configure
But it says I need C Compiler thing, where do I get that. Also
I can't use the Net on Ubuntu, and I know why. I want to download that
C Compiler stuff on Windows, put it in a cd or floppy, then I install it on Ubuntu. So I want the website to it, so I can download it.

Kakason

---

### Post by tread on 2005-05-29
sudo apt-get install build-essential 

will get you your c compiler.

Incidentally, why are you trying to compile ruby? Just install it using synaptic .. from the top menu:
System->Administration->Synaptic

search for ruby, and install it. If the search turns up nothing, check out how to add extra repositories at [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by Kakason on 2005-05-29
[QUOTE=tread]sudo apt-get install build-essential 

will get you your c compiler.

[/QUOTE]

Isn't that downloading from somewhere, if so, I don't have the net on Ubuntu because my Modem is a Winmodem. I wonder if Wine can make it work.

---

### Post by zxee on 2005-05-29
[QUOTE=Kakason]Wow, that's a really cool website.
But I have 1 Question.
I'm installing Ruby.
I got the Ruby-1.8.2.tar.gz
I do this
tar xvzf /home/username/ruby-1.8.2.tar.gz
Then a list of things came, then I do this
cd /home/username/ruby-1.8.2
then I do this
./configure
But it says I need C Compiler thing, where do I get that. Also
I can't use the Net on Ubuntu, and I know why. I want to download that
C Compiler stuff on Windows, put it in a cd or floppy, then I install it on Ubuntu. So I want the website to it, so I can download it.

Kakason[/QUOTE]
 The development software is on the install cd. I don't remember the exact command now but when I did apt-get install ( i think it was ) gcc  then the system asked me to insert the install cd and it installed it and I was ok then to install tar.gz packages. If you have your sources edited-look in /etc/apt/sources.list you might be able to install ruby form apt-get

---

### Post by Kakason on 2005-05-29
Thanks yous guys for helping me. Finally I understand more.

Kakason

---

### Post by Julian David Pitt on 2005-05-29
This is what I see in the root terminal when I try to install my program after having unpacked it.

[COLOR=Blue]root@ubuntu
root@ubuntu:/home/julian # cd avg7-linux
root@ubuntu:/home/julian/avg7-linux # ./configure
[COLOR=Red]bash: ./configure: No such file or directory[/COLOR]
root@ubuntu:/home/julian/avg7-linux #
root@ubuntu:/home/julian/avg7-linux #
[/COLOR]
What is happening at the red line please ?
Thanks all.

---

### Post by Julian David Pitt on 2005-05-29
just tried again but not root this time. This is what I get again:
[COLOR=Blue]
julian@ubuntu:~$ pwd
/home/julian
julian@ubuntu:~$ cd avg7-linux
julian@ubuntu:~/avg7-linux$ ./configure
bash: ./configure: No such file or directory
julian@ubuntu:~/avg7-linux$
[/COLOR]
Your thoughts would be much appreciated people  ](*,)

---

### Post by tread on 2005-05-29
Is avg7-linux the folder you unzipped your application to? Check if there is a INSTALL/README file .. that will have installation instructions. If it doesn't, post the contents of 'ls -l' in that directory here?

---

