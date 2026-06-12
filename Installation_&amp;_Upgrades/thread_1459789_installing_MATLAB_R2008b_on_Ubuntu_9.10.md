---
title: "installing MATLAB R2008b on Ubuntu 9.10"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by economath on 2010-04-21
Hi, I have a Dell Studio 1749 and am having problems installing MATLAB on Ubuntu 9.10 Karmic Koala. After putting in the DVD, I start the installation script:

```
/media/cdrom/install_unix.sh
```and I get the message:

```
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /media/cdrom0/unix/update/install/main.sh: 178: /media/cdrom0/unix/update/bin/glnxa64/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .

``` Any suggestions?

---

### Post by nmaster on 2010-04-21
two suggestions:

1. try the same command with 'sudo'.  
```

sudo /media/cdrom/install_unix.sh 

```
2. try the suggestion that the error message gives you.

---

### Post by economath on 2010-04-22
Thanks, neal.m.master. Unfortunately, the same command with `sudo' produced the same results. 

Regarding the error message, I'm not fully sure what it means when it says, "Attempt to fix the problem and try again." I assume it has something to do with getting a file called /media/cdrom0/unix/update/bin/glnxa64/xsetup but I don't know what to do here. So, I tried to use the code:

 ```
install -t /media/cdrom/install_unix.sh
```but get the following:

```
install: target `/media/cdrom0/unix/update/install/main.sh' is not a directory
```Anyone know how to solve the issue I raised in the first post in this thread I started?

---

### Post by nmaster on 2010-05-02
sorry for not getting back to you sooner, the last week of the semester is always hell! 

have you tried to use these instructions?: [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

i installed MATLAB almost a year ago and so i don't completely remember what I did or if i ran into this error that you've found. sorry :(

---

### Post by economath on 2010-05-05
Success! Ok, here is what I did. Firstly, I followed neal.m.master's advice and went to [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) which helped me to install MATLAB...except for an activation issue. For that, I had to download license.dat and put it into the licenses folder at /usr/local/MATLAB/R2008b_student/licenses To get that file, I had to log in to Matlab's website and search for a code - ring up Matlab's technical helpline to get that code because it is dependent on your version of MATLAB. Then I had to go through the activation process - I stayed on the phone so that I knew I would have no troubles.

In fact, after installing MATLAB using the points on the page that neal.m.master mentioned [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) the technical team are excellent - just log into MATLAB website, look for contacts in your local area and then when you ring up, choose technical support --> installation. There were many different things I was told to try and I can't remember all of them or which worked, but essentially the problem was that my version of MATLAB was a 32 bit program, running on a 64 bit laptop. So, I have to go into /usr/local/MATLAB/R2008b_student/bin to run it by typing:

```
./matlab -glnx86
```

---

### Post by ashokranade on 2010-05-06
[LEFT][FONT=Arial][SIZE=2]i have installed matlab 2009 on Ubuntu  9.10 - the Karmic Koala according to [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) rules given. As i try to launch it from Application<<Programming<<MatlabR2009a it gives " Could not launch 'MATLAB R2009a' and Failed to execute child process "matlab" (No such file or directory). If i try to launch matlab by right click opening a .m file matlab screen flashes but donot go ahead.
Please give some solution to this problem[/SIZE][/FONT]
[/LEFT]

---

### Post by nmaster on 2010-05-06
where did you install matlab to? if you followed the suggestion, then you need to do this from a terminal (Alt+F2 and type in gnome-terminal)

```

sh /usr/local/matlabR2010a/bin/matlab

```

if that isn't the correct path, then look around in the directory where you installed matlab.  find the bin directory and there should be a file there that you can execute.

---

### Post by ashokranade on 2010-05-08
Thank you i was struggling for last few days. It is working from terminal. Any way to run from application launcher ?

---

### Post by nmaster on 2010-05-08
you can right click on the applications menu and go to "Edit Menus"  You can then create a new launcher by clicking "New Item"

for the command, just use the command that you used in the terminal.

google images will help with finding an icon: [http://www.google.com/images?hl=en&q=matlab%20icon#q=matlab+icon&hl=en&safe=off&tbs=isch:1,isz:i&source=lnt&ei=SqDlS6CfB5y2tAO_ysnRCw&sa=X&oi=tool&resnum=3&ct=tlink](http://www.google.com/images?hl=en&q=matlab%20icon#q=matlab+icon&hl=en&safe=off&tbs=isch:1,isz:i&source=lnt&ei=SqDlS6CfB5y2tAO_ysnRCw&sa=X&oi=tool&resnum=3&ct=tlink)

if you want an application launcher on the panel, the process is very similar: [https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)




just so you know, you should start new threads to ask questions.  the original poster marked this thread as solved.  you're quite lucky that i even checked this thread at all. :)

---

