---
title: "Environment variables not recognized"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by jcgp on 2010-03-16
Hi,
I have some environment variables that I define in .bashrc, such as this:
BROWSER=firefox; export BROWSER

Then I have a C app that reads these variables using getenv. When I start the app from a Gnome terminal (running bash) or a xterm, it works fine. When I start the app clicking on a panel icon, where I defined exactly the same command that I use at the command line, the environment variables are not recognized. I did not have this problem before with older distributions.

What is happenning? How can I solve this?

This is Ubuntu 9.10 on a 32 bits laptop, running Gnome, loging as administrator (the first account created)

Thanks,
Carlos

---

### Post by jcgp on 2010-03-17
Problem solved: instead of setting the environment variables in .bashrc, I just added them in .profile. Now the environment variables are recognized when I launch the app: 1) from the command line; 2) after clicking on the icon.

---

### Post by tom4everitt on 2010-03-17
The reason is that the export command only exports the command to _supprocesses_ of the process it is set in. So when launching from a terminal, your C program will be a subprocess of your terminal (shell). If launching from gnome it will be a subprocess of gnome, and gnome does not read .bashrc. (But apparently it does read .profile, good to know!)

You could also launch the program with:

env BROWSER=firefox /path/of/C/program

---

### Post by jcgp on 2010-03-18
The problem is: .bashrc does not work in Ubuntu for Gnome desktop panel icons but it does work in the other systems I tested with Gnome Desktop as well: Fedora and Suse. On the other hand, .profile works in Ubuntu for Gnome panel icons but not in Suse and presumably not in Fedora as well...

So it is rather unfortunate that we do not have a standard way to set environment variables in Linux (and this is only for bash... I am not even talking about csh, etc. ...)

Regards,
Carlos

---

### Post by apollo74 on 2010-03-26
Hi guys,

I think you are the right people to ask the following. I've just installed Ubuntu 9.10 32bits and need to work with Intel C++ Compiler which asks me to run a script that will load a bunch of environment variables for proper function. The line is:
source /path/to/iccvars.sh ia32
If I run that line in a shell, it works well and I can see the new variables with 'printenv' and use Intel's compiler and be happy. If I add that line to my ~/.bashrc, everything works well as before.
My problems started when I realized that I need to work with programs outside the shell, those programs do NOT see the environment variables from Intel's script.
So I tried to follow this thread and erased that line from ~/.bashrc and put it in ~/.profile instead and what I found out when logging out and back in into my gnome account was that those variables can NOT be seen from a shell or detected by my other programs. However, when opening a text-console (CTRL+ALT+Fx) I can see the Intel variables loaded properly.

What's wrong in this picture? hope you can help me.

PS: I've also tried with creating a ~/.pam_environment file and adding that line there... no luck there either.

---

### Post by tom4everitt on 2010-03-26
What happens if you put the intel script in /etc/profile.d

That's the most system wide place to put them that I know of (I wouldn't call myself a guru though, so its quite possible there are other options). 

From what I can tell the script /etc/profile will be launched at some point, reading all files in the /etc/profile.d directory.




Would launching your program from a shell script be possible? You could just wrap it in something like:

```

#!/bin/bash

source <your-variable-file>

command-to-launch-program



```

---

### Post by beartham on 2010-04-03
What about the standard Unix case of:

[INDENT]VARIABLE=value program_name [arguments] :confused:
[/INDENT]

where the program accesses via getenv("VARIABLE"). This does not work in Kubuntu 9.04 but it does work in Kubuntu 8.04. 

Putting "env" in front of the variable name doesn't work either.

Isn't this a bug?

---

