---
title: "where is ubuntu rc.local"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by si_sol on 2005-06-09
Hi All,

I have used linux (redhat, suse) for 1 year, but new to ubuntu. I want to execute something on startup. In redhat, i put it in the rc.local file (in windows i put it in autoexec.bat) . Is there any file in ubuntu with similar function with those rc.local ?.
What is the name and the location of the file ?.

thanks in advance
regards,

si sol

---

### Post by Njall on 2005-06-10
[QUOTE=si_sol]
I have used linux (redhat, suse) for 1 year, but new to ubuntu. I want to execute something on startup. In redhat, i put it in the rc.local file (in windows i put it in autoexec.bat) . Is there any file in ubuntu with similar function with those rc.local ?.
What is the name and the location of the file ?.
[/QUOTE]

   To be honest I don't know if there is a file which would exactly mimic rc.local.  I think what you need to do is read the man page for boot(7), i.e. $ man 7 boot.  That tells you quite a bit about the boot sequence.  From that I suspect you could figure out how to create and activate a script rather like rc.local. 

   You might check out this answer at [LinuxQuestions.org](http://www.linuxquestions.org/questions/archive/26/2004/01/3/136542) 

- Nelson...

---

### Post by Joeb on 2005-06-10
[QUOTE=si_sol]Hi All,

I have used linux (redhat, suse) for 1 year, but new to ubuntu. I want to execute something on startup. In redhat, i put it in the rc.local file (in windows i put it in autoexec.bat) . Is there any file in ubuntu with similar function with those rc.local ?.
What is the name and the location of the file ?.

thanks in advance
regards,

si sol[/QUOTE]

You could put your startup script in /etc/init.d and then put a symlink to it in /etc/rc3.d and in /etc/rc5.d  (rc3 is when you boot to text mode, rc5 is graphic mode).  If you look at the symlinks in those directories, you will notice they begin with Sxx where xx is a number.  The symlinks are executed in the xx order, in case something needs to be loaded before something else.

---

### Post by si_sol on 2005-06-10
Thanks joeb,

But is it posible to put a script without start, stop, restart mechanism those way ?. 
I just want to have a script like this :

#!/bin/bash
export http_proxy=http://192.168.1.1:8080 

Honestly i've tried it, but the result is not as I expected (put myproxy.sh which contain those script int /etc/init.d/, make a symlinks to it in /etc/rc5.d, restart, and check the environment --> I didn't get the desired result). Am I missing something here ?.

---

### Post by ltmon on 2005-06-10
[QUOTE=Joeb]You could put your startup script in /etc/init.d and then put a symlink to it in /etc/rc3.d and in /etc/rc5.d  (rc3 is when you boot to text mode, rc5 is graphic mode).  If you look at the symlinks in those directories, you will notice they begin with Sxx where xx is a number.  The symlinks are executed in the xx order, in case something needs to be loaded before something else.[/QUOTE]

In Debian based systems (e.g. Ubuntu) runlevel 1 is text mode and 2 is graphical mode.  3-5 are generally not used, or reserved for custom user defined levels.

L.

---

### Post by ltmon on 2005-06-10
[QUOTE=si_sol]Thanks joeb,

But is it posible to put a script without start, stop, restart mechanism those way ?. 
I just want to have a script like this :

#!/bin/bash
export http_proxy=http://192.168.1.1:8080 

Honestly i've tried it, but the result is not as I expected (put myproxy.sh which contain those script int /etc/init.d/, make a symlinks to it in /etc/rc5.d, restart, and check the environment --> I didn't get the desired result). Am I missing something here ?.[/QUOTE]

A simpler method that may work just as well is to put this in your ~/.bashrc.  It gets executed every time bash starts.

L.

---

### Post by si_sol on 2005-06-10
[QUOTE=ltmon]In Debian based systems (e.g. Ubuntu) runlevel 1 is text mode and 2 is graphical mode.  3-5 are generally not used, or reserved for custom user defined levels.

L.[/QUOTE]
 I finally put it in .bashrc and it work.
thanks.

---

### Post by dsmarty on 2005-06-10
This is what I found in the Ubuntu-archives:

```

cd /etc/init.d/
touch rc.local
chmod +x rc.local
ln -s rc.local ../rcS.d/80rc.local

```

Works fine for me  :)

---

### Post by wylfing on 2005-06-10
I would not recommend putting things into /etc/init.d unless they are required for system-wide usage. If it's just your preference to have something run, such as an export command, you should first try running it as a "startup program" for your session. Off the main menu: System > Preferences > Sessions. Click Startup Programs, Add, type your line, and click OK.

Only if this level of functionality fails you should you escalate to something "bigger." Running convenience commands from /etc/init.d is overkill.

Now, if you really find you need to put a script in /etc/init.d, the proper way to make the symlinks is with the 'update-rc.d' command. If you are afraid of the start, stop, restart mechanism just copy one of the other scripts in init.d and edit it. (In the case of running an export command, you just want to ignore everything except start.) Then, for example, to "install" a script named 'foo' that you've put in /etc/init.d:
```
sudo update-rc.d foo defaults 80
```
All the correct links will be made for you. Later, if you wish to "uninstall" this script you would run:
```
sudo update-rc.d foo remove
```
HTH

---

### Post by dsmarty on 2005-06-10
He asked about rc.local, that is the script redhat-like distros use to start some extra application at boot.

A way to do that is to insert something like rc.local.

You're right about starting things for a session or other user-stuff. But that's not the use of rc.local in redhat-like distros either :)

Personally, I use it to start certain applications on my server.

---

### Post by wylfing on 2005-06-10
Yeah, I was both a Mandrake and Fedora user at one point. I'm just saying if all you want to do is make sure a convenient variable is exported, it's a lot of overkill to create an init.d script for it.

---

### Post by si_sol on 2005-06-10
Thanks everyone for your reply.

Actually, my first motivation to put those variable in startup is to eliminate the following error message :

synchronizing clock time with ntp.ubuntulinux.org......[failed].

I knew that it caused by the absent of the proxy setting in early stage of startup process. And yes, I want the scope of those export variable to be system wide.

---

