---
title: "tty1-6 using .bashrc in /home"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-07-28
I just added a custom .bashrc to my /home folder the same as I've had in Jaunty. But I discover that switching to a console (tty1-6) uses the .bashrc. I'm sure it didn't do this before. A bug or intentional?

---

### Post by mattduckman on 2009-07-28
I'm not sure if I'm understanding correctly.

But anytime you start bash (login) it's going to use .bashrc unless you tell it not to.  That's the way it's always been.

---

### Post by wayne_cat on 2009-07-28
> **mattduckman said:**
> I'm not sure if I'm understanding correctly.

But anytime you start bash (login) it's going to use .bashrc unless you tell it not to.  That's the way it's always been.

this is how it should be:

.bashrc = every time you open a termial ( i.e. gnome-terminal)

.bash_profile = only when you login (i.e. tty or ssh)

---

### Post by phenest on 2009-07-29
I don't mean Gnome Terminal. I'm talking about the console (tty1-6). If I press Ctrl-Alt-F1 and login, I can use all the stuff in my ~/.bashrc. That never happened before.

---

### Post by taavikko on 2009-07-29
> **phenest said:**
> I don't mean Gnome Terminal. I'm talking about the console (tty1-6). If I press Ctrl-Alt-F1 and login, I can use all the stuff in my ~/.bashrc. That never happened before.

then you've had something really b0rked on your installations :)
It's always worked on me...

---

### Post by Gourgi on 2009-07-29
> **wayne_cat said:**
> this is how it should be:

.bashrc = every time you open a termial ( i.e. gnome-terminal)

.bash_profile = only when you login (i.e. tty or ssh)

i also think that the above is the desired usage so probably it is a bug.

---

### Post by phenest on 2009-07-29
Bug reported: [406275]("https://bugs.launchpad.net/ubuntu/+bug/406275")

---

### Post by phenest on 2009-07-29
Can someone help me out here. My bug report has been marked as invalid! :confused:

---

### Post by Gourgi on 2009-07-29
ok , i'm in jaunty now to test this.
i've added in the end of my .bashrc :
```
echo "test"  
```

1) if there is no ~/.bash_profile then ~/.bashrc is included and "echo" is executed using Ctrl+Alt+F1 
(albeit your experience from jaunty is that .bashrc is not executed)
2) but if there is ~/.bash_profile then the echo is not executed ;)

so i believe you just have to create a .bash_profile :
```
touch ~/.bash_profile
```

probably you'll have to add $PATH and/or aliases there too

i hope this helps


edit: 
i'm not fully convinced that comment #1 from your bug report is 100% correct.
further reading:
[http://www.debianadmin.com/difference-between-bash_profile-and-bashrc-files.html](http://www.debianadmin.com/difference-between-bash_profile-and-bashrc-files.html)
[http://digg.com/linux_unix/Difference_between_bashrc_and_bash_profile](http://digg.com/linux_unix/Difference_between_bashrc_and_bash_profile)
[http://joshstaiger.org/archives/2005/07/bash_profile_vs.html](http://joshstaiger.org/archives/2005/07/bash_profile_vs.html)
[http://hacktux.com/bash/bashrc/bash_profile](http://hacktux.com/bash/bashrc/bash_profile)
[http://www.linuxforums.org/forum/linux-newbie/1182-difference-between-bashrc-bash_profile.html](http://www.linuxforums.org/forum/linux-newbie/1182-difference-between-bashrc-bash_profile.html)

---

### Post by phenest on 2009-07-29
I have no ~/.bash_profile in Jaunty or Karmic.

---

### Post by phenest on 2009-08-24
> **taavikko said:**
> then you've had something really b0rked on your installations :)
It's always worked on me...

On which one: Jaunty or Karmic? Karmic is the first time I've seen this.

> **Gourgi said:**
> i also think that the above is the desired usage so probably it is a bug.

The current behaviour in Karmic, altough perhaps handy, is undesired.

> **phenest said:**
> Can someone help me out here. My bug report has been marked as invalid! :confused:

And again!

> **Gourgi said:**
> i'm not fully convinced that comment #1 from your bug report is 100% correct.

You're not the first to say this.

I had the opposite issue in Jaunty. Some one explained that the .bashrc is not for tty's.

So which is supposed to be?

---

