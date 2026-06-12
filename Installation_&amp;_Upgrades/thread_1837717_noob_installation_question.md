---
title: "noob installation question"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by teemarkconvair on 2011-09-02
11.04 dual with win7/ runs fine.. i can't find a way to install drivers for spacenavigator.. i open the tar and have the ".sh" to install, BUT it won't install.the "working" icon shows for a few seconds, i have checked properties and it is set to execute.. i am totally new to linux..   i tried package manager but it won't accept the tar or the .sh.. and am at a roadblock,,any help is appreciated.  [never done any "command line]

---

### Post by sanderd17 on 2011-09-02
a .sh is normally a shell script. You need to open a terminal (CTRL+ALT+T) and go to the directory where the .sh file is. Say the .sh file is in the dirctory Downloads/spacenavigator under your home directory, then you have to do
```

cd Downloads/spacenavigator

```

(if it gives an error, try to unsterstand the error and do not continue without fixing the error)

than, I don't know if the file is already executable. But to make it execuatable, you have to do a "chmod u+x" (CHange the MODifiers to make it eXecutable for the User) on the file. If your file is called install.sh, this gives
```

chmod u+x install.sh

```

Now you can run it:
```

./install.sh

```

**HINT:** you can use the TAB key to autocomplete filenames and commands, and you can use the up-down arrows to get commands from your history back (useful if you only have to change one letter in a long line).

---

### Post by Hakunka-Matata on 2011-09-02
try ```
sudo bash install.sh
```

---

### Post by teemarkconvair on 2011-09-02
> **sanderd17 said:**
> a .sh is normally a shell script. You need to open a terminal (CTRL+ALT+T) and go to the directory where the .sh file is. Say the .sh file is in the dirctory Downloads/spacenavigator under your home directory, then you have to do
```

cd Downloads/spacenavigator

```

(if it gives an error, try to unsterstand the error and do not continue without fixing the error)

than, I don't know if the file is already executable. But to make it execuatable, you have to do a "chmod u+x" (CHange the MODifiers to make it eXecutable for the User) on the file. If your file is called install.sh, this gives
```

chmod u+x install.sh

```

Now you can run it:
```

./install.sh

```

**HINT:** you can use the TAB key to autocomplete filenames and commands, and you can use the up-down arrows to get commands from your history back (useful if you only have to change one letter in a long line).
i keep getting no such directory..and would i put all commands in ONE terminal or is each a separate terminal in turn?  i see, in "places", thomas/desktop/ [then the spacenavigator folder] which i entered as "cd  desktop/spacenavigator",, keep in mind i AM NEW to command line AND linux!! :)  and thanks for the help,,

---

### Post by Hakunka-Matata on 2011-09-02
Afll file names, folder names, commands are case SenSiTive. 

When you open a new termianl, you are starting at your home folder.

look in places, that's your home folder, there is a folder named **Desktop **there also.  

whatever**:~$** cd [B]Desktop
[/B]and you'll have switched down one directory, to Desktop directory, folder.

enter man cd at the terminal prompt, 


I'll show you an example:
```

das@1104-32:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
das@1104-32:~$ cd Desktop
das@1104-32:~/Desktop$ ls
das@1104-32:~/Desktop$ cd ..
das@1104-32:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
das@1104-32:~$ cd Documents
das@1104-32:~/Documents$ ls
drucifer.ods
das@1104-32:~/Documents$ cd ..
das@1104-32:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
das@1104-32:~$ cd Music
das@1104-32:~/Music$ ls
vlc-record-2011-09-02-11h16m59s-Radio Paradise - DJ-mixed modern & classic rock, electronica, world & more-Radio Paradise - Commercial-Free, Listener-Supported.mp4
vlc-record-2011-09-02-11h17m22s-Radio Paradise - DJ-mixed modern & classic rock, electronica, world & more-The National - Anyone`s Ghost.mp4
vlc-record-2011-09-02-11h19m04s-Radio Paradise - DJ-mixed modern & classic rock, electronica, world & more-The National - Anyone`s Ghost.mp4
vlc-record-2011-09-02-11h39m39s-Radio Paradise - DJ-mixed modern & classic rock, electronica, world & more-Robert Palmer - Sailing Shoes _ Hey Julia _ Sneakin` Sally.mp4
vlc-record-2011-09-02-13h32m35s-Radio Paradise - DJ-mixed modern & classic rock, electronica, world & more-Depeche Mode - Policy of Truth.mp4
das@1104-32:~/Music$ 

```

---

### Post by sanderd17 on 2011-09-03
The commands should go in the same terminal, and as Hakuna Matata said, watch out for capital letters. The directory is called **D**esktop and not **d**esktop.

If you want to learn the terminal (because it's a powerful tool), you can take a look at this: [http://linuxcommand.org]("http://linuxcommand.org"). It's a very short tutorial which explains you all the basic commands and the pitfalls.  You don't need to learn about shell scripting, the part about the terminal is enough.

---

### Post by teemarkconvair on 2011-09-03
well i got this.. :~$ cd home/thomas/spacenavigator./install.3dxunix.sh
bash: cd: home/thomas/spacenavigator./install.3dxunix.sh: No such file or directory
"

---

### Post by sanderd17 on 2011-09-03
> **teemarkconvair said:**
> well i got this.. :~$ cd home/thomas/spacenavigator./install.3dxunix.sh
bash: cd: home/thomas/spacenavigator./install.3dxunix.sh: No such file or directory
"

First: after each command, you need to execute it by pressing ENTER. So "cd home/thomas/spacenavigator" and "./install.3dxunix.sh" should not be on one line.

Second"

If you do a cd (change directory), than you can give a relative path or an absolute path.

An absolute path always starts with / (the root directory), so in this case, the absolute path will be **/**home/thomas/spacenavigator. (if that is the right directory).

A relative path starts from where you are now. If you don't know where you are, you can use the command "pwd" (print working directory) to see it. When you start a terminal, you always start inside your own home directory. So a relative path to the spacenavigator directory would be just "spacenavigator" (since it's directly under your home directory).

So for the CD command, you can choose to use

```

cd spacenavigator

```
or
```

cd /home/thomas/spacenavigator

```

If you do
```

cd home/thomas/spacenavigator

```
than it will not work, since you don't have a "home" directory under your current one. There is no directory /home/thomas/home.

---

### Post by teemarkconvair on 2011-09-03
i wonder if this may help? see attachment.. it says from root..and i am leery of "root" if i goof up..and, thanks again for all the help..!!

---

### Post by Hakunka-Matata on 2011-09-03
> **teemarkconvair said:**
> well i got this.. :~$ cd home/thomas/spacenavigator./install.3dxunix.sh
bash: cd: home/thomas/spacenavigator./install.3dxunix.sh: No such file or directory
"

Open a Terminal:
> das@das-System-Product-Name:~$ pwd
/home/das
das@das-System-Product-Name:~$ cd spacenavigator
das@das-System-Product-Name:~/spacenavigator$ pwd
/home/das/spacenavigator
das@das-System-Product-Name:~/spacenavigator$ ls **          # the 'ls' command produces nothing, because the directory is empty**
das@das-System-Product-Name:~/spacenavigator$ chmod u+x install.sh
chmod: cannot access `install.sh': No such file or directory
das@das-System-Product-Name:~/spacenavigator$ ./install.sh
bash: ./install.sh: No such file or directory
das@das-System-Product-Name:~/spacenavigator$ sudo bash install.sh
bash: install.sh: No such file or directory
das@das-System-Product-Name:~/spacenavigator$ pwd
/home/das/spacenavigator
das@das-System-Product-Name:~/spacenavigator$ cd ..
das@das-System-Product-Name:~$ pwd
/home/das
das@das-System-Product-Name:~$ cd ..
das@das-System-Product-Name:/home$ pwd
/home
das@das-System-Product-Name:/home$ cd ..
das@das-System-Product-Name:/$ pwd
/
das@das-System-Product-Name:/$ cd /home/das/
das@das-System-Product-Name:~$ 
That's what it should look like, except you have files inside the spacenavigator directory, yes.  The directory should contain the file "**install.sh**", 
use the 'ls' command to display directory contents

---

### Post by Hakunka-Matata on 2011-09-03
post# 2: has the commands that should work, (unless your install.sh needs the "sudo bash install.sh" command).

of course the file install.sh must be located in that directory to start with, if it isn't there, you can copy it to that directory to start with.

---

### Post by teemarkconvair on 2011-09-03
sorry.. i am totally lost in all that..theres no SIMPLE "RUN" command? REALLY?? hmm,,

---

### Post by teemarkconvair on 2011-09-03
well,, to my surprise i finally got the terminal to seem to install. of course the spacenavigator doesnt work!! lol  i guess its back to WIN7  thanks guys

---

### Post by teemarkconvair on 2011-09-04
i have found the problem,, and it is ME!!   helps to ENABLE in Second Life,, thanks for all the assistance..  appreciate it!!

---

### Post by Hakunka-Matata on 2011-09-04
```
 Quote: teemarkconvair:: i have found the problem,, and it is ME!!
```


what does that mean?  Have you installed your install.sh file?

---

### Post by teemarkconvair on 2011-09-05
i was expecting to see something like a windows application "install"..turns out all i needed to do was to "enable" it in second life.. thanks for the help  T

---

