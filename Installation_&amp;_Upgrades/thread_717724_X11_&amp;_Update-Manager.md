---
title: "X11 &amp; Update-Manager"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by jumping_snake on 2008-03-07
Interesting situation: I have x11 setup on my Windows XP box (using the Cygwin "startxwin.bat") and on an Ubuntu 6.06 LTS box. I can open an xterm window fine, so I know it's working. 

But, when I run:
%gksu "update-manager -c"

it actually opens to fullscreen, asking for my password. After I enter my password, it closes and I dumped back onto the Desktop of my Windows box and it appears that the connection is lost. If I open an xterm and run the command through it (instead of the Putty window), the same thing happens.

EDIT: Ok, so here's the latest news: if everything has been restarted (including the Ubuntu server) and I SSH in (with X11 through Putty) and then  open an xterm, I can then run "gksu "update-manager -c" and it will take my input. But, it then quits whether I have the correct input for the password or not. At this point, the server no longer has an idea where update-manager is (keeps saying command not found) but I can still open xterms and xcalcs. The screen even darkens when I do get update-manager going (like whenever you have to enter in an admin password).

Thanks for any ideas in advance!!

---

### Post by ssj3strife on 2008-03-08
What are you trying to accomplish? The first impression that I got was that you're trying to open a cygwin version of ubuntu's update manager, which to the best of my knowledge doesn't exist. So I'm assuming that you're trying to forward an X window over an ssh connection. Is that right?

---

### Post by jumping_snake on 2008-03-09
I'm under the impression that using the GUI version of the update-manager is the best way to upgrade the OS. I've used the command line version before and had issues.

So, yes, like you said I'm trying to open up a SSH connection and then X11 forward through. I'm using Putty to create the SSH connection and xserver (Cygwin) on my local Windows XP box. 

Is this something that can't be done? I'm able to get basic things to go through (xterm, xcalc) and if I run xterm and then run the gksu "update-manager -c" on that newly sent through xterm, I can get a full screen fade-out (like Ubuntu does when it needs an admin password) and a request for a password. I can enter in a password but it doesn't matter if it's the correct one or not, the program ends and back in the newly sent through xterm shell it dumps me back at the command line instead of showing that the application is still running. If I do a "top", the program doesn't show up in the process list either.

Basically, I'm just trying to update a server for my job and I'd like the process to be as painless as possible. I don't have direct access to the machine, hence all of the SSH and X11. If worse comes to worse, we'll just back everything up and then do a complete rebuild of the system to get it up to 7.10 and then 8.04 when it comes out next month.

---

### Post by ssj3strife on 2008-03-10
Okie doke! I think you're making the scenario a tad more complicated than it needs to be. My advice would be to use the VNC server that comes preinstalled with Ubuntu - go to System -> Preferences -> Remote desktop. As soon as you configure those options, you will be able to connect with a VNC client as if you were at the local machine, so you shouldn't have issue with gksu not launching its priviledged processes, etc. 

One caveat however, you will need to be logged into the machine locally before you can connect remotely. So if you need to update the kernel and thus reboot the machine, you will not be able to reconnect unless you set up an autologin via gdmsetup.

As far the client, I recommend UltraVNC. They have the most powerful client I have seen so far, but it is Windows only.

That is the easiest solution for you I can think of. Does it sound acceptable to you? I don't know what your specific needs are, if you're concerned about security there are other options available as well, but they are a bit more complicated.

---

### Post by jumping_snake on 2008-03-10
I debated using that method. Let me try it at work in the next day or two to see if it will work for me!

I found a paper from the place that I work at that gives me directions to setup VNC to tunnel through SSH so that there's a little encryption for the process.

I'll post on both topics as soon as I can!

---

### Post by ssj3strife on 2008-03-12
I wrote a small script that automatically connects to any of my machines at home that I'll post in hopes that you can get some use out of it. :)

```
#!/bin/bash

read -p 'Remote host (default: thefallenangels)? ' rhost ;
read -p 'Local port (default: 3389)? ' lport ;
read -p 'Use (v)nc or (r)desktop (default vnc)? ' vr ;

if [[ $rhost == '' ]] ;
then rhost=thefallenangels ;
fi ;

if [[ $lport == '' ]] ;
then lport=3389 ;
fi ;

if [[ $vr == '' ]] ;
then vr=v ;
fi ;

if [[ $vr == 'v' ]] ;
then read -p 'Remote port (default 5900)? ' rport ;
if [[ $rport == '' ]] ;
then rport=5900 ;
fi ;
ssh -f -C -L $lport:$rhost:$rport strife.ath.cx -p 7328 -l tunnel sleep 10 ;
vncviewer -PreferredEncoding ZRLE localhost:$lport -passwd ~/.vnc/passwd ;
fi ;

if [[ $vr == 'r' ]] ;
then ssh -f -C -L $lport:$rhost:3389 strife.ath.cx -p 7328 -l tunnel sleep 10 ;
rdesktop localhost:$lport -g 1280x960 -E -a 16 -z -x b -r sound:off ;
fi ;

unset rhost ;
unset lport ;
unset vr ;
unset rport ;

```

If you want to connect to the same machine that you're SSH-ing to, the remote host would be localhost. Any other machine would be the hostname of the machine. Also, this doesn't require any special configuration of the server, which is always a bonus in my book!

Here's what you'd need to change if you wanted to use this for yourself:
[LIST]
[*]Address of server (currently strife.ath.cx)
[*]User to log in to server with (currently tunnel)
[*]Default machine name (currently thefallenangels, you might want localhost)
[*]Ports (My SSH port is 7328, standard is 22)
[/LIST]

Hope that helps! Maybe you'll pull out just the couple lines you need (the ssh and vncviewer pair), but the script handles connecting to Windows machines too using rdesktop so I thought I'd give you the whole thing, maybe it'll come in handy.

---

### Post by jumping_snake on 2008-03-13
Sorry it took me so long to respond. I haven't tried your script yet, but that'll be next! The only thing that's stood in my path from using this link's info:
[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)
is the infamous "VNC server paths issue". Here's the error that pops up:

Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.
Couldn't start Xtightvnc process.

Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
MAXSOCKS=1000

I've looked this up and it's been an issue for a long time, and after using the site it just mentioned above's fixes for it, I found I could get everything to work on a 7.10 Desktop machine, but still not my amd64 6.06 machine :(

My guess is that we'll end up biting the bullet by backing everything of importance up and rebuilding the server with 7.10 (until 8.04 comes out). But, I have setup a similar machine at home and I'd like to see this thing out, so I'll keep you updated on my progress!!

---

### Post by ssj3strife on 2008-03-13
Just for giggles, I checked out that path (/usr/X11R6/lib/X11/rgb) on my own machine, and... it doesn't exist! I'm not sure what the significance of that is, but I thought you'd want to know.

Just out of curiosity, why aren't you using the vnc server that comes with Ubuntu (vino)? I guess you haven't actually mentioned what version of Ubuntu is running on your server, so is it because your version doesn't have vino installed?

Your approach of installing TightVNC's server ought to work as well, but that seems a bit more complicated, and if all you're looking to do is remote updating then I think simple is good. :)

(Oh, I forgot to mention that even though I don't have that rgb path, I can run 'vncviewer localhost' and it works just fine, I guess that's a tightvnc-specific thing?)

---

### Post by ssj3strife on 2008-03-13
I tried following that guide you linked to in a virtual machine to see if maybe I could see where you were having troubles. Unfortunately, it worked like a charm. :( (I imagine people usually aren't bothered when things work right the first time, go figure!)

I did discover though that my virtual machine also does *not* have the rgb path, and when I started the server, I got no complaints about it.

My only guess is that you might have forgotten to edit the /etc/vnc.conf file like the guide suggested?

---

