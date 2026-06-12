---
title: "synaptic on Kubuntu 5.10"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by fractalvibes on 2005-10-20
Installed Breezy via iso, installed, mostly seems ok.  Did an apt-get install of synaptic,

When I issue the synaptic command:

root@PhiLinux:/home/fractalvibes# synaptic
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:26892): Gtk-WARNING **: cannot open display:

So.  What might be missing?

KDE seems to be fine....

thanks,

fv

---

### Post by Saarg on 2005-10-20
Try starting Synaptic from a normal user with sudo or kdesu.
The reason you get the errormessage is that there is no Xsession for root.
How you can change this I don't know. Try the search button ;)

---

### Post by fractalvibes on 2005-10-20
Ok - catch-22.  I exit out of root and run the synaptic command just as a user I get the
 
"you must run this program as root user" pop-up message.

arg.

fv

---

### Post by mlomker on 2005-10-20
Try:

```

xhost local:
synaptic

```

I have the xhost command in my ~/.bashrc file.

---

### Post by fractalvibes on 2005-10-20
ok - tried - xhost seems to be most uncooperative in all ways:

tried:
root@PhiLinux:/home/fractalvibes# xhost local:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xhost:  unable to open display ":0.0"
root@PhiLinux:/home/fractalvibes# xhost
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xhost:  unable to open display ":0.0"
root@PhiLinux:/home/fractalvibes# xhost local: synaptic
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xhost:  unable to open display ":0.0"

so xhost seems to be fried or non-configured.....
Is this a big-ass bug to be reported?

fv

---

### Post by stoeptegel on 2005-10-20
Why did you got yourself root anyway? Sudo is your friend, exit to $ and do your thing.

---

### Post by mlomker on 2005-10-20
> root@PhiLinux:/home/fractalvibes# xhost local:


You need to run xhost **before** you su to root.  Xhost is a command that grants other users permission to use your X session and it has to be granted by the user that you logged in as...

---

### Post by fractalvibes on 2005-10-20
Hmm - xhost never came into the picture before at all, On 5.04 I just sudo'd into su and then issued the synaptic command.

Resullt from just a user prompt:
fractalvibes@PhiLinux:~$ xhost
access control enabled, only authorized clients can connect
fractalvibes@PhiLinux:~$

Been using synaptic for 6 months and never even HEARD of xhost nor was it an issue...

Obviously 5.04 configured some stuff behind the scenes that 5.10 does not?

fv

---

### Post by mlomker on 2005-10-20
> Obviously 5.04 configured some stuff behind the scenes that 5.10 does not?


No idea because I don't run synaptic from the command-line.  Few programs will run from the command line as root if you don't use xhost.  Note that the command is **xhost local:** and not what you typed.  There are many command-line options but the local: allows any local user to run applications.  **xhost +** allows anybody from anywhere...it'd work but not as secure.

---

### Post by bored2k on 2005-10-20
```
sudo synaptic
``` usually did the job over hizzay..

---

### Post by fractalvibes on 2005-10-20
Ok - thanks.

I figured how to just add it to the menu and run as root, prompting for password beforehand.

Very strange - it was never an issue before, as I always ran from command line by just sudo-ing as su and giving the command.

What other "suprises" await?

fv

---

