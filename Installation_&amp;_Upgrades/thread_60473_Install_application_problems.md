---
title: "Install application problems"
date: 2005-08-27
forum: Installation &amp; Upgrades
---

### Post by kb7ypf on 2005-08-27
Hi-
I have installed ubuntu without problems and have everythign working.  My problem is how in the H*ll do I install program.

I have downloaded a program, lets say I put it in: 
/home/dick/Download

In a terminal progarm I go to the download directory.
1.  I type ./config    and that seems to work
2.  I type make  and all I get is something about "target something" not specified or words to that effect.

Being totally new to Linux, I know not what that is all about other that I can't install a program for whatever reason.  

Can someone please help me out with a simple 1-2-3 approach to installation.  You can even tell me where to download a program and walk through it.  

I really need to understand this process.  Thanks much for your assistance.


Dick  ](*,)

---

### Post by dbcoder on 2005-08-28
Well, welcome to linux.


Well, you are jumping head first into linux compiling your own programs, being new to linux and all.

Well, chances are you do not have the tools necessary to complete compilation.


Make sure you have the basic compilers by running

apt-get install build-essentials

If you have that then I would suggest looking at the ./configure output for any hints on to what you don't have or what has gone wrong.  Then you can use apt-get install to get what you are missing...

Some tips on anticipating what software would be named in the apt-get repositories.


Say you need gtk2.  You would get gtk2-dev since these are the tools used to develope gtk2 applications, and is used in compiling it.

For xlibs you would get xlibs-dev.  

So on and so forth, I hope that this helps.


EDIT: Well, I say well too much.

---

### Post by kb7ypf on 2005-08-28
Thanks for the response.

I seem to have apt-get.

I think I understand that part of it.  

But what do I do with a file called kstars.-1.01-pl-tar.bz2 that I have downloaded?  It seems that after I have downloaded the file, I am stuck as what to do next.  

Can you shed some light and assist a Linux Not-So-Smart-Dude.    Thanks again.


Dick

---

### Post by dbcoder on 2005-08-28
Meh, it's not that you aren't smart, it's just you haven't learned it yet :P.


Well, .tar.bz2, tar.gz, etc are like window's .zip files.  You can extract them easily by opening them in file-roller.  Make sure you are root when you extract the files if you want to extract them anywhere outside of your home (/home/yourusernamehere).

Say the filename is file.tar.bz2

I would just type file-roller file.tar.bz2 in the console (of course, in that directory).

Then you would extract it just like in winzip, but if you have a folder selected it will extract it into that folder.  It's not like windows where you have to open the folder to extract it there, simply selecting it will extract it in that folder.

---

### Post by kb7ypf on 2005-08-28
Hi Again-

Well, .tar.bz2, tar.gz, etc are like window's .zip files. You can extract them easily by opening them in file-roller. Make sure you are root when you extract the files if you want to extract them anywhere outside of your home (/home/yourusernamehere).

ok, If I understand you right, I need to extract them outside my /home directory.  

Can I make another directory under /root, say "programs" and extract them there?

Then after I extract them to /root/programs....what do I do next?

Yes, the learning curve.

Thanks again.


Dick

---

