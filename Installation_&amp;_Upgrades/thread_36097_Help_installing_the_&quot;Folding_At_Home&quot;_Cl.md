---
title: "Help installing the &quot;Folding At Home&quot; Client"
date: 2005-05-21
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2005-05-21
As a total novice concerning Ubuntu and Linux in general could you good people help me install the executable file I have downloaded for the client for the above. I take it I need to use the apt-get command but I have no real idea so all help will be well received. Thanks in advance.
Cheers
Pompeyrodney

---

### Post by bored2k on 2005-05-21
What is the file extension of your "FAH" application ?

---

### Post by Julian David Pitt on 2005-05-21
It comes in the form of an exe file to install the linux client and I am using the Hoary Hedgehog release. Your help is appreciated.

---

### Post by brickbat on 2005-05-21
From the Folding at Home website

We provide a console mode version of the client, exactly equivalent to the console version for Windows. There are no fancy graphics -- it simply sits in the background running at lowest priority and making use of the CPU cycles not being used by other processes. The latest Linux version can be found at [http://www.folding.org/download.html](http://www.folding.org/download.html).

To launch: To use this program, make sure that you can execute it (chmod +x FAH5-Linux.exe) and then run it ./FAH5-Linux.exe

More information: [http://vspx27.stanford.edu/console-userguide.txt](http://vspx27.stanford.edu/console-userguide.txt) provides details on the various command line flags supported.

ciao
bb

---

### Post by Julian David Pitt on 2005-05-21
Thanks Brickbat but I already have that info, it is just the actual install I do not understand how to perform, ie the line below:

"To launch: To use this program, make sure that you can execute it (chmod +x FAH5-Linux.exe) and then run it ./FAH5-Linux.exe"

Is the "chmod +x FAH5-Linux.exe" the command to put into the terminal ?

---

### Post by bored2k on 2005-05-21
[QUOTE=Julian David Pitt]Thanks Brickbat but I already have that info, it is just the actual install I do not understand how to perform, ie the line below:

"To launch: To use this program, make sure that you can execute it (chmod +x FAH5-Linux.exe) and then run it ./FAH5-Linux.exe"

Is the "chmod +x FAH5-Linux.exe" the command to put into the terminal ?[/QUOTE]
 Yes. chmod +x will make the file executable. Then you will "./FAH5-Linux.exe" for the program to execute (copy/pasting is allowed ;)).

---

### Post by brickbat on 2005-05-21
You don't have to install it.  You just download it wherever you want and then you open a shell.  You go to the download directory and then you follow the instructions from the previous post.

ciao
bb

---

### Post by Julian David Pitt on 2005-05-22
This is what I am getting logged on as root and normal, root first:

root@ubuntu:/home/julian # chmod +x FAH502-Linux.exe
root@ubuntu:/home/julian # ./fah502-Linux.exe
bash: ./fah502-Linux.exe: No such file or directory
root@ubuntu:/home/julian # ./FAH502-linux.exe
bash: ./FAH502-linux.exe: No such file or directory
root@ubuntu:/home/julian #

julian@ubuntu:~$ chmod +x FAH502-Linux.exe
julian@ubuntu:~$ ./FAH502-LInux.exe
bash: ./FAH502-LInux.exe: No such file or directory
julian@ubuntu:~$

I should point out that I have copied the exe file onto the desktop as well as the /home/julian directory
Thanks for any help in advance.
Cheers JDP

---

### Post by brickbat on 2005-05-22
Could you please do an "ls -l" of the julian directory and copy it into a reply to this post.

ciao
bb

---

### Post by Julian David Pitt on 2005-05-22
Hi Brickbat

logged on as root

"root@ubuntu:/home/julian # 1s -1
bash: 1s: command not found
root@ubuntu:/home/julian #"

normal terminal 

"julian@ubuntu:~$ 1s -1
bash: 1s: command not found
julian@ubuntu:~$"

Cheers

---

### Post by brickbat on 2005-05-22
I think you are type the wrong command.  Please cut and paste it from my post.  In bash paste is ctrl-shift-V

ciao
bb

---

### Post by Julian David Pitt on 2005-05-22
Hi BB
Seems you supposed correctly mate !

root@ubuntu:/home/julian # ls -l
total 252
drwxr-xr-x  2 julian julian   4096 2005-05-22 16:24 Desktop
-rwxr-xr-x  1 julian julian 249236 2005-05-20 21:48 FAH502-Linux.exe
root@ubuntu:/home/julian #

Cheers

---

### Post by brickbat on 2005-05-22
ok. Once again, go to the julian dir and cut and paste:

./FAH502-Linux.exe

if it doesn't work please post the result.

ciao
bb

---

### Post by Julian David Pitt on 2005-05-22
Hi Brickbat
You are a star sir and no mistake, it worked. What was I doing wrong then ? Was it just a typo on my part. Can I set the program to run at every boot up and how do I ascertain whether it will do that without rebooting to find out ? Cheers for your help BB.

---

### Post by krusbjorn on 2005-05-22
Go to the System menu -> preferences -> Sessions -> Startup Programs.

Edit: by the way, you missed the uppercase letters when you tried to run the exe-file. 

root@ubuntu:/home/julian # ./fah502-Linux.exe 
("FAH" were supposed to be uppercase)

root@ubuntu:/home/julian # ./FAH502-linux.exe 
(the L in Linux were supposed to be uppercase)

julian@ubuntu:~$ ./FAH502-LInux.exe 
(the I in Linux were supposed to be lowercase)

root@ubuntu:/home/julian # 1s -1 
(it's ls -l, not 1s -1. lowercase L's, not the digit 1.)

Good luck in the future ;)

---

### Post by Julian David Pitt on 2005-05-23
Hi Krusbjorn
Many thanks for your help, I have done as you said and all appears to be fine now thanks. How long have you been using Ubuntu, I would like to hear what you think of it my friend.
Regards
Julian

---

### Post by krusbjorn on 2005-05-23
[QUOTE=Julian David Pitt]Hi Krusbjorn
Many thanks for your help, I have done as you said and all appears to be fine now thanks. How long have you been using Ubuntu, I would like to hear what you think of it my friend.
Regards
Julian[/QUOTE]

I've only been using it since february. Before that, i was on WinXP, so i cant really compare it to other distros. But it works great for me, and with this awsome community, there is always help nearby if something breaks :)

Good luck!

---

### Post by poyner on 2005-06-15
Hi guys.... I've got a question about FAH and thought I'd post in here instead of starting a new thread. 

My question is... should FAH show up in the System Monitor somewhere? 
I ask this because the terminal where I started the program shows '[12:54:06] Completed 0 out of 7500000 steps  (0%)' and this doesn't seem to change. When I go to the system monitor the resources tab shows the CPU is at 100% but when I go to the Processes tab I can't seem to see which process is using the 100%. It's all very weird. 

Basically I want to find out if FAH is working OK on my computer.

---

### Post by jpkotta on 2005-10-09
Open a terminal and type `top` withwout the quotes.  It's the "Table of Processes" and it shows what processes are running and how much CPU time they're using.  Type 'Shift-M' in top to sort by memory usage.  Type 'q' to quit.

I have written an install script for Folding@Home.  Please get it in the [Wiki]("https://wiki.ubuntu.com/FoldingAtHome").  It is based off of the Gentoo FAH install.  It installs the executable to /opt/foldingathome, and creates a client for every CPU.  It installs a startup script to /etc/init.d, and adds it to runlevel 2.

---

### Post by HotFoot on 2007-01-18
Hello,

Since the problem Julian was having seems similar to mine, I thought I would post my problem on this thread.  I've recently changed my Ubuntu installation (fresh install including reformatting all my Ubuntu partitions) to 64-bit in the hopes of getting the SMP FAH core working.  I've downloaded and unpacked the .tgz file from the FAH website, as instructed, and I'm attempting to run the console.  However, I get a problem.  Below you can see what the output of a "ls -l" and "./fah5" are for me.

Thanks for any help.

scott@Scott-Desktop:~/FAH_SMP$ ls -l
total 320
-rwxr-xr-x 1 scott scott 249556 2007-01-15 01:22 fah5
-rwx------ 1 scott scott  68492 2006-11-21 11:12 mpiexec
scott@Scott-Desktop:~/FAH_SMP$ ./fah5
bash: ./fah5: No such file or directory

===================================
EDIT

I found the solution to my problem browsing through some other forums on the web.  What's needed to run the 64-bit FAH core is actually some 32-bit libraries.  You can install these by typing:
"sudo apt-get install ia32-libs".    Since doing this, my FAH client has started working, and the console is engaging both of my cores.

Next I'll be doing some benchmarking!

---

