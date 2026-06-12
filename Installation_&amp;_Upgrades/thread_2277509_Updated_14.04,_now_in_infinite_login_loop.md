---
title: "Updated 14.04, now in infinite login loop"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2015-05-09
Just tried to update 14.04 today and all seemed to go well.  But when it rebooted, it is now in an infinite login loop, i.e. it says "guest session" and I give it the password and it repeats the login screen etc. etc. etc.

How can I recover from this problem?

Thank you for your help.

---

### Post by dino99 on 2015-05-09
which (x)(k) ubuntu is it ?
from the login dialog, you might see a cog in the right top corner, click on it to select your user instead of the guest, then your password should works (no password needed for a guest)

---

### Post by deeppow on 2015-05-09
> **dino99 said:**
> which (x)(k) ubuntu is it ?
I have no idea what (x)(k) means.  Sorry I'm too much of a newbie.

> **dino99 said:**
> from the login dialog, you might see a cog in the right top corner, click on it to select your user instead of the guest, then your password should works (no password needed for a guest)

I select me as the user with password, loops back to login.  I select guest with no pasword, loops back to login.

---

### Post by Bashing-om on 2015-05-09
deeppow; Hello;

That looping back to the login screen could be the result of a number of faults. Let's explore 2 possibilities.
At the login screen activate a console by key combo ctl+alt+F1.
Can you login here with your username and password ( there is no response to the screen when pass word is entered. enter password blindly and hit the enter key) ?

Post back the results of terminal commands:
```

ls -al .Xauthority
ls -al .ICEauthority
sudo lshw -C display

```

and let's see what story gets told

---

### Post by deeppow on 2015-05-09
ls -al .Xauthority
-rw____________

ls -al .ICEauthority
-rw____________

sudo lshw -C display
"display Unclaimed"
"display Unclaimed"

for the 2 monitors I have.

---

### Post by Bashing-om on 2015-05-09
deeppow; Hey;

Look'n more like a graphics driver issue, but ....
Those 2 files, who owns them, and who is grouped ?
```

sysop@1404mini:~$ ls -al .Xauthority
-rw------- 1 sysop sysop 209 Feb  4 15:15 .Xauthority
sysop@1404mini:~$

sysop@1404mini:~$ ls -al .ICEauthority
-rw------- 1 sysop sysop 1956 May  9 12:38 .ICEauthority
sysop@1404mini:~$

```
Where in my case I am 'sysop' .

And back to graphics, as no driver is loaded, what is the hardware and we try and match a driver:
```

lspci -vnn | grep VGA -A 12

```

[INDENT][INDENT]and the truth of the matter is ?
[/INDENT][/INDENT]

---

### Post by deeppow on 2015-05-09
-rw------- 1 ralph ralph 56 May  9 14:20 .Xauthority

-rw------- 1 ralph ralph 565 May  9 8:10 .ICEauthority
 

sudo lshw -C display

appears driver for GTX 960 is missing      ------    it was there before update
driver for 650 TI is there.

---

### Post by Bashing-om on 2015-05-09
deeppow; Yep;

> 
appears driver for  ------ it was there before update

3rd party driver built on one kernel breaks when the image gets a rebuild with a different kernel. The 3rd party driver is not a part of ubuntu.
How did you install the driver - Nvidia recommends the 346driver ?
Purge and re-install graphics driver, and all should be well.

[INDENT]presently with the 346 driver
[INDENT][INDENT][INDENT]there is no better alternative
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by deeppow on 2015-05-10
Thanks up and running.

---

### Post by Bashing-om on 2015-05-10
deeppow; Great !

You do good work.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Sebastian_Kindler on 2015-05-24
As I encountered the login loop two days ago, I thought I should share. (This is a repost, as this thread's title is more fitting than the other.)

Searching for a solution in other threads, you will find there is one dominant solution: access privileges for both of the files, .Xauthority and .IDEauthority.

Bashing-om's solution is spot-on. However, it might not solve the issue for everybody. (Sorry, if the rest of this post seems unnecessarily detailed but I had to look for this information in so many places that I thought, someone might appreciate to have it all in one place.)


How to find whether or not you "own" those .*authority files?


Login as Guest, which you have probably done anyway to use the internet.


Open a login terminal with Ctrl + Alt + F2, or alternatively, + F3, + F4, and so on until F6. (You should be able to do that without logging in as Guest as well.)


Ctrl + Alt + F7 brings you back to your "Desktop", so you can switch back and forth to continue reading.


(I will use ASUS-S400CA as an example.)


```

Ubuntu 14.04.2 ASUS-S400CA tty2


ASUS-S400CA login:



```


Type in your username. (Your username is the nickname you chose at installation, not your full name you may see on your actual login screen.)


Then type in your password.


```



Ubuntu 14.04.2 ASUS-S400CA tty2


ASUS-S400CA login: yourusername


Password:



```


You should now see:


```



yourusername@ASUS-S400CA:~$



```


If your login loop is caused by missing access privileges for the files mentioned earlier, this code should do:


```



ls  -ld  ~/.*authority



```


If you then get


```



-rw------- 1 root root 2015 May  24 12:38 .ICEauthority


-rw------- 1 root root 2015 May  24 12:38 .Xauthority



```


instead of


```





-rw------- 1 yourusername yourusername 2015 May  24 12:38 .ICEauthority


-rw------- 1 yourusername yourusername 2015 May  24 12:38 .Xauthority



```


you have to use the chown command to get back your access privileges:


```



sudo  chown  yourusername:yourusername  ~/.Xauthority



```


and if necessary the same for .IDEauthority. Note that you will have to verify the result again with the ls command. No error message is a good sign, though.




Your shell does not recognize any of the commands you type in?


This could be the main cause for the login loop as login itself is just a command.



How to use commands under these circumstances?


The shell gives you two pieces of information: First, the command is not accessible. Second, it is found in, e.g.


```



/usr/bin



```


In this case the above mentioned code looks - depending on where "the executable" of the command is located in your system - something like this:


```



/usr/bin/ls   -ld   ~/.*authority


/usr/bin/sudo  /bin/chown   yourusername:yourusername   ~/.Xauthority


/usr/bin/sudo  /bin/chown   yourusername:yourusername   ~/.IDEauthority



```




The reason why your command prompt (shell, Terminal, command line) recognizes and executes commands - including the login command - is, because the paths to their directories - like /usr/bin, /bin, /sbin and so on - are all saved in a file. There they are given as the value to a variable called PATH. (For easy to understand explanations on Linux terms check out linfo.org. In this case [linfo.org/path_env_var.html]("http://linfo.org/path_env_var.html"))




To check, which paths are saved in PATH, type


```



echo $PATH



```


or its equivalent command with directory structure.


It will probably give you something like


```



/usr/local



```


However it should look like:


```



/usr/bin:/usr/sbin:/bin:/sbin:/usr/local/:/usr/local/bin:/usr/local/sbin



```


The different directories between the colons can be arranged in any order.




To save those temporarily, and be able to use commands, type


```



export PATH=$PATH:/usr/bin:/usr/sbin:/bin:/sbin:/usr/local/:/usr/local/bin:/usr/local/sbin



```




To make those changes permanently, you have to save it in the respective file, where your PATH variable is defined.


Depending on your type of shell (bash etc.), this could be a different file, and there are certain (new) conventions about in which (configuration) file to exactly save those paths to your commands. ([unix.stackexchange.com/questions/88201/whats-the-best-distro-shell-agnostic-way-to-set-environment-variables]("http://unix.stackexchange.com/questions/88201/whats-the-best-distro-shell-agnostic-way-to-set-environment-variables"))


In your home directory ~ , which is equivalent to /home/yourusername, there should be a file called .profile. If you temporarily saved your directories to your commands you can open that file by typing


```



sudo gedit ~/.profile



```


This opens the file with the respective text editor gedit. (Just in case you do not have gedit for some reason, use the aptitude or apt-get command in combination with sudo and install gedit or any text editor you prefer: sudo apt-get install gedit .)


At the end of that file you probably find something like:


# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi


PATH=usr/local




However, PATH should be defined just as described above. Simply, add the other directories:


PATH=/usr/local:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin


save the file, reboot your system, and you should (hopefully) be good to go.

---

