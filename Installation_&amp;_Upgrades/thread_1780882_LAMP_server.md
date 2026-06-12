---
title: "LAMP server"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by RickLabelle on 2011-06-12
Hello, I am new to linux/ubuntu. I have installed lamp server on my ubuntu 10.04 desktop computer, and now I just get the terminal prompt. I typed "sudo apt-get install ubuntu-desktop", and I get some errors. After researching online, I did an apt-get update, but that failed as well. I added lamp to my desktop because I need an online calendar setup.

---

### Post by sanderd17 on 2011-06-12
> **RickLabelle said:**
> Hello, I am new to linux/ubuntu. I have installed lamp server on my ubuntu 10.04 desktop computer, and now I just get the terminal prompt. I typed "sudo apt-get install ubuntu-desktop", and I get some errors. After researching online, I did an apt-get update, but that failed as well. I added lamp to my desktop because I need an online calendar setup.

can you give the output of apt-get update? Output is important for troubleshooting.

Just in case your desktop is still installed, try running 
```

startx

```
from the terminal.

---

### Post by RickLabelle on 2011-06-12
Hi Sanerd17, thanks for your reply. I tried the startx but it responded with "apt-get install initx" because startx was not installed. I did that apt-get and it failed. Also, how do I post the output? the screen scrolls for quite a bit before stopping on the prompt. How would I back it up to post it on this thread which I am using a windows laptop.

---

### Post by sanderd17 on 2011-06-12
I think I could do something with the last lines, take a picture of it.

---

### Post by RickLabelle on 2011-06-12
Sanderd17 Attached is the picture of the display after the apt-get update

 [IMG]file:///C:/Users/Tech/Desktop/photo%283%29.JPG[/IMG][IMG]file:///C:/Users/Tech/Desktop/photo%283%29.JPG[/IMG][IMG]http://ubuntuforums.org/showthread.php?p=10932237#post10932237[/IMG]

---

### Post by sanderd17 on 2011-06-12
I'm not able to view it, you used the online pictures tool, you need to add the picture as attachment (the bottom of the new reply form)

---

### Post by RickLabelle on 2011-06-12
Sandred17 Here is the pic

---

### Post by MAFoElffen on 2011-06-12
> **RickLabelle said:**
> Hello, I am new to linux/ubuntu. I have installed lamp server on my ubuntu 10.04 desktop computer, and now I just get the terminal prompt. I typed "sudo apt-get install ubuntu-desktop", and I get some errors. After researching online, I did an apt-get update, but that failed as well. I added lamp to my desktop because I need an online calendar setup.
Please, slow down and take a breath.  I have experience with both desktop edition, server edition, server services installed and running on both platforms.

Before going on:
You said started out with Ubuntu 10.04 Desktop...
  Question- **32bit or 64bit and are you still on 10.04 Desktop Edition?**
You said "I have installed lamp server "
  Question: **How did you install the LAMP package?**  **Via your synaptic package manager?  Command line via apt-get or aptitude?**

...**Or did you do something else?**

The reason I asked those question is that just the process of installing LAMP on any version of Ubunut should not have had anything to do with Xorg, which is the graphical X-session... 

I have LAMP services on 2 of my Desktops here (11.04 and 11.10)  and two of my servers here (11.04 and 11.10) that are running LAMP Services, that are both also running several desktops (xubuntu-desktop, kubuntu-desktop and ubuntu-desktop)...    (All four have gone from 9.04 through 11.10 - some a few times)

Unless what you did was to install a version of Ubuntu Server Edition "over" a Desktop Edition, which would be something a "little" different.  But from what you mentioned on what it's purpose was, that's not what you want to end up with.

A short sidenote on this-
If you want to install a desktop on a server edition, then yes, you would 
```

sudo apt-get install ubuntu-desktop

```Which would install the desktop (with it's application) to your server edition.  It would then updates the initramfs, so that when it starts, it would start in a graphical mode instead of text.... Where the commands to start the Gnome graphical session for the past few versions are now:
```

sudo service gdm start

```But what you end up with is a Server configure kernel that has it's kernel optimized for server services and not for graphics.  Trying to run graphics and end-user app's on a server kernel-- and your performance drags.   Yes I have done the benchmarks. 

If you just want to run a server app in a small private network environment or to run as a local-host app, then you won;t notice any pull of a service service app running on a desktop. in the background.

But from what you described in your first post-  I'm a little confused what you did..  Something went wrong.  And from what you said, something is still wrong and the direction you seem to be heading in not where you said you wanted to be.

Before adding to your problems (and any additional frustrations), please answer the 4 questions in bold above.

Then we could go on... If it was an install or update problem that caused a broken package in that process, then we;ll have a clearer idea of where that might be from those answers.

---

### Post by RickLabelle on 2011-06-12
I had 32bit 10.04 LTS desktop. I installed the LAMP server via the command line. First, I typed sudo apt-get lamp server^ and that did not work, so I typed sudo apt-get tasksel. It brought up a blue menu screen so I selected the LAMP and Samba. I selected samba because of the online calendar that I want to setup. I need windows user to have access.

---

### Post by sanderd17 on 2011-06-13
From what I see on the pic is that you
a) have no internet connection, please make sure it is connected via a wire
you can check your connection with
```

ping google.be

```
if it responds, than your connection is not the problem

the problem might be
b) the server you selected to get packages from is down 

If the last one is the problem, I will have to search out on how to find a good server and put it in the sources.list.

---

### Post by RickLabelle on 2011-06-13
Sanderd17, I tried to ping google.be and the response was unknown host. The internet connection did work prior to the lamp install. Furthermore, I have a link light on my router. I am using a wired connection.

---

### Post by sanderd17 on 2011-06-13
Then I fear that you have problems with your DNS. Ping google from another machine and then ping the ip address of google on your broken machine. If that works, then your DNS is not setup correctly (or at all) and I'm sorry, but I don't know how to fix it, maybe google has some tips.

---

### Post by earlf on 2011-07-08
RickLabelle, have you discovered a solution to your problem? 

I recently experienced something similar and was able to restore my desktop (the graphical interface and standard installed programs) with ```
sudo apt-get install ubuntu-desktop
```

I am running a recent install of Lucid 10.04 32bit Desktop Edition. I launched taskel and navigated through to select the LAMP server option. I then hit enter. 

This began installing the LAMP stack, but uninstalling the desktop, and a few other programs I had installed. 

I was quite surprised and dismayed but it is related to discussions here:
[LIST=1]
[*][http://ubuntuforums.org/archive/index.php/t-1369551.html]("http://ubuntuforums.org/archive/index.php/t-1369551.html")
[*][https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/150252]("https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/150252")
[*][http://ubuntuforums.org/showthread.php?t=1585015&page=3]("http://ubuntuforums.org/showthread.php?t=1585015&page=3")
[/LIST]

Strange issue, and thought I'd add my experience to this thread as it is a recent example of a bad encounter with taskel and configuring a LAMP stack. 

I guess I'll try installing the packages independently or by using ```
sudo apt-get install lamp-server^
```

---

### Post by Blasphemist on 2011-07-08
For the reason of just what happened here, unintended actions taken, I do not recommend using tasksel on a desktop environment.

> This function is similar to that of meta-packages, and, in fact, most of the tasks available from tasksel are also available as meta-packages from the Ubuntu package managers (such as Synaptic Package Manager or KPackageKit).

---

