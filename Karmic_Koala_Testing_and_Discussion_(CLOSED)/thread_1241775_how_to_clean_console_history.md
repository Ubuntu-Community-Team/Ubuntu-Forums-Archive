---
title: "how to clean console history ?"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dino99 on 2009-08-16
hi,

since a long time now i'm searching a script or something that can make room in the console history. I don't know if it exist, but all the duplicates in this history is a bad mode operating. 

well, if someone knows where this history is logged, i'll try to clean it.

---

### Post by wayne_cat on 2009-08-16
history -c

---

### Post by dino99 on 2009-08-16
thanks man

---

### Post by ajgreeny on 2009-08-16
Or if you want to do it entry by entry you can find the hidden plain text file **.bash_history** in your home folder (Ctrl+H to see hidden files), and can edit out the things you want to remove using gedit or your chosen text editor.

---

### Post by dino99 on 2009-08-16
i'm ok

but, in fact, my question is about all the duplicates in that file.
As i've read in bashrc, that duplicates should not exist (the doc says: consecutives duplicates are not saved, maybe but the non consecutives seem to be saved & there is no way about that)

---

### Post by wayne_cat on 2009-08-16
> **dino99 said:**
> i'm ok

but, in fact, my question is about all the duplicates in that file.
As i've read in bashrc, that duplicates should not exist (the doc says: consecutives duplicates are not saved, maybe but the non consecutives seem to be saved & there is no way about that)

add this line to the .bashrc file:

```
export HISTCONTROL=ignoredups:erasedups
```to prevent duplicates in the bash history

---

### Post by ajgreeny on 2009-08-16
> **wayne_cat said:**
> add this line to the .bashrc file:

```
export HISTCONTROL=ignoredups:erasedups
```to prevent duplicates in the bash history
Does this only work after a restart or logout and in again?  I've just added the line to my .bashrc to try it, as duplicates annoy me as well, and see that duplicates still appear, and I don't mean old ones which I assume will remain, but newly entered commands, after the change to .bashrc.

---

### Post by taavikko on 2009-08-16
> **ajgreeny said:**
> Does this only work after a restart or logout and in again?  I've just added the line to my .bashrc to try it, as duplicates annoy me as well, and see that duplicates still appear, and I don't mean old ones which I assume will remain, but newly entered commands, after the change to .bashrc.

```
source ~/.bashrc
```

---

### Post by ajgreeny on 2009-08-16
> **taavikko said:**
> ```
source ~/.bashrc
```
What does that do?  I can find little info on that command, other than adding it to .bash_profile, which does not exist.  Should I add it to .profile instead, which seems to have similar but slightly different lines in its text?

---

### Post by scaine on 2009-08-16
> **ajgreeny said:**
> What does that do?  I can find little info on that command, other than adding it to .bash_profile, which does not exist.  Should I add it to .profile instead, which seems to have similar but slightly different lines in its text?

There's no man entry for source.  New one on me too...

---

### Post by wayne_cat on 2009-08-16
> **scaine said:**
> There's no man entry for source.  New one on me too...

the source command is a bash function ... you can find information about it in the bash man page
```

source filename [arguments]
Read  and  execute commands from filename in the current shell environment and return 
the exit status of the last command executed from filename.  If filename does not
contain a slash, file names  in  PATH  are used to find the directory containing
filename.  The file searched for in PATH need not be executable.  When bash is  
not  in  posix  mode,  the  current  directory  is searched  if  no file is found in
PATH.  If the sourcepath option to the shopt builtin command is turned off, the
PATH is not searched.  If any arguments are supplied, they become the posi-
tional  parameters  when  filename  is  executed.   Otherwise  the  positional
parameters are unchanged.  The return status is the status of the last command
exited within the script (0 if no commands are executed), and false if filename is
not found or cannot be read.
```you can use the "source" function on two ways (both do the same)

```
source <filename>
```or 

```
. <filename>
```

---

### Post by ajgreeny on 2009-08-17
```
source filename [arguments]
Read  and  execute commands from filename in the current shell environment and return 
the exit status of the last command executed from filename.  If filename does not
contain a slash, file names  in  PATH  are used to find the directory containing
filename.  The file searched for in PATH need not be executable.  When bash is  
not  in  posix  mode,  the  current  directory  is searched  if  no file is found in
PATH.  If the sourcepath option to the shopt builtin command is turned off, the
PATH is not searched.  If any arguments are supplied, they become the posi-
tional  parameters  when  filename  is  executed.   Otherwise  the  positional
parameters are unchanged.  The return status is the status of the last command
exited within the script (0 if no commands are executed), and false if filename is
not found or cannot be read.
```That could be really useful, except that I don't actually understand most of what it says.

Does this mean that the command (argument) has to be run each time I boot up, or even each time I start the terminal.  I have not so far managed to get the duplicates to stop appearing in .bash_history, and though it is not terribly important, I do like to understand as much as possible about Ubuntu and linux.

---

### Post by meborc on 2009-08-17
if you save your .bashrc file, you don't need to do the changes every boot... it is saved in the config file

running "source" will just make the saved configuration file work _atthismoment_ :) meaning you dont need to login/logout to see the effect you made by changing the configuration file working

---

### Post by dino99 on 2009-08-17
hi all,
seems that bash is so powerfull that it's not so easy to use by the end-user.
I have made changes in my .bashrc file like Wayne says above and wait to see if duplicates stop to be saved.

I've search how this file is created and some others too missing in my folder like bash_profile, but can't find the process. So, if .bashrc is deleted, how to recreate it ?

---

### Post by taavikko on 2009-08-17
> **dino99 said:**
> So, if .bashrc is deleted, how to recreate it ?

When user is added, the contents of /etc/skel is then copied to 
~/

Or if deleted accidentally, just copy the one from /etc/skel/.bashrc to $HOME

---

### Post by dino99 on 2009-08-17
many thanks Taavikko, thats help to know when things are hidden.
yes, i've read docs & digg on google

---

### Post by dino99 on 2009-08-18
Now my .bash_history file is thiner with the solution proposed by Wayne.
No more duplicates.

Thanks man.:P

---

