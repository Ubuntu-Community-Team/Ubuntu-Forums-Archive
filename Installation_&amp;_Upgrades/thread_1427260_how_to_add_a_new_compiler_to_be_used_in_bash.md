---
title: "how to add a new compiler to be used in bash?"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by yinas on 2010-03-11
hello community!
i would like to ask for help in this concern i need for my study:

we are using a tool to simulate a basic computer, called TOY
now this TOY has its own compiler and linker, which i will need to use in order to use *.asm files in this simulator

now to my question:

**how do i add the commands "toyasm" and "toylink" to be used in my linux bash?**

i have the files "toyasm" and "toylink" provided by the lecture's materials, and already managed to copy them into /usr/bin, where i found the "gcc" compile command already (been using that one before)
but now i get "permission denied" when i try to use the new ones

can anyone give me a short guidline on what to do when i want to add custom compilers to my system?
or maybe anyone would have a link to a guide explaining a solution to this?

thanks for your time!

-yinas

---

### Post by solar george on 2010-03-11
If you are the only one on your computer using them then create a folder called "bin" in your home directory.
Copy the "toyasm" and "toylink" binaries into it.
Then:
```
chmod +x -v ~/bin/*
```
Logout then login again and you should find they work correctly.

---

### Post by rnerwein on 2010-03-11
hi
first it's not /bin it is /usr/bin where the command was copyed to.
second never !!! use an asterik in system folders ! use --> chmod 755 /usr/bin/your_command
( also the user and the group of your command should belong to root -->                                               chown root:root /usr/bin/your_command
ciao

---

### Post by solar george on 2010-03-11
> second never !!! use an asterik in system folders ! use --> chmod 755 /usr/bin/your_command

Notice the tilde (~) before the command.

My recommendation was to copy the files to a folder in called bin in the home directory which is represented by the tilde.
i.e. for me as user george ~ == /home/george 
By placing the files into ~/bin you avoid the need to use root permissions.

---

### Post by yinas on 2010-03-15
hello and lots of thanks for your help already!
so i tried

cd /home
sudo mkdir bin
-- copied the toyasm & toylink files to this folder
sudo chmod +x -v /home/bin/toyasm
sudo chmod +x -v /home/bin/toylink
(question: what does the "+x" do here? its not in the help file)

relogged
now i get
toyasm: command not found

i even tried to enter
sudo chmod +x -v /home/bin

but still the same
did i miss something?

again, i just wanna use these commands to compile and link my assembly code files....

---

### Post by solar george on 2010-03-15
```
cd /home
sudo mkdir bin
```

You've misunderstood, you need to be in your home dir not /home.

```
cd ~
```
Will change to your home dir.
```
mkdir bin
```
No need for sudo as your in your own home dir.
Copy the files.
```
chmod +x -v ~/bin/* 
```
The +x ensures that the file is marked as an executable.

---

### Post by yinas on 2010-03-16
thanks a lot!
now i got what you meant, and it looks like it works :D

will set the thread to "solved" ;)

thx again!

---

