---
title: "X11VNC on 11.10 (was working with 11.04)"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by nergaldicuthah on 2011-10-14
[SIZE=3]**EDITED THREAD**[/SIZE]: Jump to reply [#20]("http://ubuntuforums.org/showpost.php?p=11379631&postcount=20") for the final outcome, and how to have X11VNC start with your computer and continue listening for a new connection after user logout. 

_________________________________________________________________________
Ok I did more than my due dilligance and have spent the better part of today searching both this site and the web as a whole

quick rundown: running 11.10 server 32bit with an x desktop (Gnome3).   Previous to today was running 11.04 on it.  I was able (with NN) to SSH into my box then run VNC with localhost:1 (ssh forwarding 5901 to 5900). Upgraded to OO and can no longer use x11vnc to connect and log in. (or even connect once logged in)
Am connecting via putty with a key on a Windows box
have tried UltraVNC and SSVNC with neither doing anything

more detail:
have tried to manually placing
```
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /var/log/x11vnc.log -forever -bg -rfbport 5900 -nomodtweak
```in both /etc/gdm/Init/Default (where it was and worked in NN) and /etc/rc.local (removing the previous one before I did so as not to have it called twice)
I have uninstalled and reinstalled x11vnc and x11vnc data
I have removed vino (share desktops) to see if perhaps the two were fighting
I have tried to manually run x11vnc from SSH command line and from terminal on the box. (EDIT: about 10% of the time I can get the server started this way with the command sudo x11vnc -localhost -display :0.  But on VNC connection I get the end of stream "maybe another user is listening" error).

None of which have allowed a VNC connection

kinda banging my head against the wall.  Server is meant to be a keyboardless and mouseless (and monitorless) box.  don't need GUI often but when I do, it is often after a reboot, I don't want to have to go into my server room plug a bunch of stuff and log in just so I can reach it via vino every reboot)

not sure what other information I need to provide.

I really hope this doesn't end up being an unanswered question as I'm sure many upgraders are going to encounter this issue.

---

### Post by alexcode on 2011-10-15
Not sure how to fix it yet, but the problem is that 11.10 doesn't use gdm anymore, it uses lightdm.

---

### Post by gregb49 on 2011-10-15
> **alexcode said:**
> Not sure how to fix it yet, but the problem is that 11.10 doesn't use gdm anymore, it uses lightdm.Is that why AVIDEMUX is missing?

---

### Post by Zeklei on 2011-10-15
I think (correct me if I'm wrong) it's because x11vnc require authorization (MIT-MAGIC-COOKIE) to connect to the xserver that lightdm is using.

When trying to start x11vnc with sudo add the following to your cmd line..

-auth /var/run/lightdm/root/:0

This should allow you to log in using lightdm.

(note in my experience the -forever arg doesn't seem to keep the vnc server running like it should maybe I'm doing something wrong)

---

### Post by nergaldicuthah on 2011-10-17
okay so we're on our way

if I ps I get 
```
pstar@computer:~$ ps wwwwaux | grep auth
root     13745  0.3  0.7  19652  7340 tty7     Ss+  11:18   0:01 /usr/bin/X :0  auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
pstar    13857  0.0  0.0   4184   796 pts/0    S+   11:23   0:00 grep --color=auto auth

```which does seem to show a similar cookie
/var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch


(note that "sudo x11vnc -auth /var/run/lightdm/root/:0" by itself error'd out as did a few different permutations of my above code plus that)

-forever (pre 11.10) would keep the session until reboot Placing the code in post 1 into GDM (and then trying to add it to LDM) would start the VNC server at boot.

I'm having issue even using VINO in this darn 11.10 upgrade.

is there a way to have to GUI clients (Gnome and LDXE) without having to blow the entire box away, and then to have VNC boot LDXE?

EDIT hmm either I'm not using findauth correct or I may have found part of the issue
(findauth by itself does nothing)
but
```
sudo x11vnc -findauth /var/run/lightdm/root:0
[: 381: -a: unexpected operator
[: 381: -a: unexpected operator
[: 381: -a: unexpected operator

```

---

### Post by alfonso78 on 2011-10-18
Hi,

Are you trying to run x11vnc AT ALL or run it at startup?

The /etc/gdm/Init/Default trick doesn't work anymore cause as alexcode said gdm is no more there.
I'm trying myself to figure out how to start it at startup.

/etc/rc.local is way too early and it fact I get error:

```
18/10/2011 18:55:16 *** XOpenDisplay failed (:0)
```

But if you want to run x11vnc, this works ***(ONLY if you are logged in manually already)***:

```
sudo apt-get install x11vnc
sudo x11vnc -storepasswd /etc/x11vnc.pass
sudo chmod 644 /etc/x11vnc.pass
/usr/bin/x11vnc -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /tmp/x11vnc.log
```

I'm trying to figure out where to place this line to start it at each startup!

Right now I'm looking at:

/etc/X11/xinit/xinitrc
/etc/X11/xinit/xserverrc

but I don't have any positive result yet.

so does it work for you if you're logged in? So that we can be all on the same page...

---

### Post by nergaldicuthah on 2011-10-18
> **alfonso78 said:**
> Hi,
 
Are you trying to run x11vnc AT ALL or run it at startup?

at startup (though AT ALL isn't even consistently working yet (previous to your suggestion which will have to wait til I get to work tomorrow :( )
 
 
> **alfonso78 said:**
> The /etc/gdm/Init/Default trick doesn't work anymore cause as alexcode said gdm is no more there.

Yes.
> **alfonso78 said:**
> 
I'm trying myself to figure out how to start it at startup.
 
/etc/rc.local is way too early and it fact I get error:

I have also tried placing it in rc.local
per [http://satisfy123.blog.com/2011/08/22/x11vnc-ubuntu/](http://satisfy123.blog.com/2011/08/22/x11vnc-ubuntu/) (I placed mine at the very bottom before the exit command (probably not the right place :P )
> if you are using lightdm, put this in /etc/rc.local
to no avail; I did not get that error, that I saw at least, do you get that during boot? (where'd you pull that error out of and I'll look at work to see if I have similar ones?).
> **alfonso78 said:**
> 
But if you want to run x11vnc, this works ***(ONLY if you are logged in manually already)***:
 
```
sudo apt-get install x11vnc
sudo x11vnc -storepasswd /etc/x11vnc.pass
sudo chmod 644 /etc/x11vnc.pass
/usr/bin/x11vnc -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /tmp/x11vnc.log
```
 
I'm trying to figure out where to place this line to start it at each startup!
 
Right now I'm looking at:
 
/etc/X11/xinit/xinitrc
/etc/X11/xinit/xserverrc
 
but I don't have any positive result yet.
 
so does it work for you if you're logged in? So that we can be all on the same page...
I will also try these out as soon as I get back to work. I'm lucky this is a squid server and not an everyday PC (or my home media server, that I really need to VNC into) ;)

---

### Post by alfonso78 on 2011-10-19
Hi,

I'm still working on this...

I asked support in the lightDM mailing list and I got a tiny bit forward: now I can start a VNC from lightDM, but not x11vnc:

[http://lists.freedesktop.org/archives/lightdm/2011-October/000163.html](http://lists.freedesktop.org/archives/lightdm/2011-October/000163.html)

The big problem, I think, it's that I can run x11vnc AFTER I login into my box, but not when the lightDM login screen is shown, so it doesn't matter where I try to launch x11vnc in the various scripts, since it won't work until I login into the box!!!!

Now I hope to get more support from the nice guys at lightDM mailing list.

---

### Post by alfonso78 on 2011-10-19
Ok, I found 80% of the solution.

now I can run x11vnc correctly (i.e. I can connect to the login prompt).

I only had to read the log file really... :(

when you try to run x11vnc before logging in, the log file will tell you (among other things):

```
** If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
              -auth /var/lib/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
              -auth /var/run/xauth/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Sometimes the command "ps wwwwaux | grep auth" can reveal the file location.

```

Which brings me to the right command to start x11vnc:

```
sudo /usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /tmp/x11vnc.log
```

it works for me and it's great! :)

now only last step is where to add this so that is runs automatically at startup. But I can run this from ssh so I'm already quite happy!
:popcorn:

---

### Post by nergaldicuthah on 2011-10-19
```
sudo /usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /tmp/x11vnc.log
```:(
when I run that I just immediatly get a new cmd prompt (no scrolling X11VNC log) and still no connect 

Although with this I do get the another user is listening error with localhost:5901 (with putty redirecting localhost 5901 to {IPWITHELD} 5900

should I modify to match my 
ps wwwwaux | grep auth
_____________________________________________________________________________________________________________________________________________
If I run
```
 /usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -localhost  
```

> PuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attempted19/10/2011 15:19:17 XOpenDisplay("localhost:10.0") failed.
19/10/2011 15:19:17 Trying again with XAUTHLOCALHOSTNAME=localhost ...
PuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong authorisation protocol attempted


---

### Post by alfonso78 on 2011-10-19
ok,

can you post /tmp/x11vnc.log after you run the command?

it is correct that it doesn't say anything on command line.

---

### Post by alfonso78 on 2011-10-19
also please post the output of the command:

```
ps wwwwaux | grep auth
```

in which state is the computer when you try to run the command I suggested? I mean: is lightDM login screen shown on the screen?

are you doing it over ssh from a remote machine or in front of the machine itself? This command only works remotely, via ssh. If you login in front of the computer to run this command, it cannot work.

In this situation, the command consistently works for me.

---

### Post by nergaldicuthah on 2011-10-19
> **alfonso78 said:**
> please post the output of the command:
 
```
ps wwwwaux | grep auth
```

See Post #5 ;-)
 
> **alfonso78 said:**
> 
I mean: is lightDM login screen shown on the screen?

Yes (on local screen not on VNC which won't even connect)
 
> **alfonso78 said:**
>  
are you doing it over ssh from a remote machine 
Yes (see post #1 ;-) )
 
> **alfonso78 said:**
> 
it is correct that it doesn't say anything on command line.
Well, that put's my mind at ease, I assume I'd get an error then if it weren't taking the command. 
 
> **alfonso78 said:**
> ok,
 
can you post /tmp/x11vnc.log after you run the command?

Exact Log (entire file cleaned out before running the command exactly as you had it)
 
```
19/10/2011 18:54:50 passing arg to libvncserver: -rfbauth
19/10/2011 18:54:50 passing arg to libvncserver: /etc/x11vnc.pass
19/10/2011 18:54:50 passing arg to libvncserver: -rfbport
19/10/2011 18:54:50 passing arg to libvncserver: 5900
19/10/2011 18:54:50 x11vnc version: 0.9.12 lastmod: 2010-09-09 pid: 2172
19/10/2011 18:54:50
19/10/2011 18:54:50 WARNING: DISPLAY starts with localhost: 'localhost:10.0'
19/10/2011 18:54:50 WARNING: Is this an SSH X11 port forwarding? You most
19/10/2011 18:54:50 WARNING: likely don't want x11vnc to use that DISPLAY.
19/10/2011 18:54:50 WARNING: You probably should supply something
19/10/2011 18:54:50 WARNING: like: -display :0 to access the physical
19/10/2011 18:54:50 WARNING: X display on the machine where x11vnc is running.
19/10/2011 18:54:50
PuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong a$
19/10/2011 18:54:50 Trying again with XAUTHLOCALHOSTNAME=localhost ...
PuTTY X11 proxy: wrong authorisation protocol attemptedPuTTY X11 proxy: wrong a$
19/10/2011 18:54:50 ***************************************
19/10/2011 18:54:50 *** XOpenDisplay failed (localhost:10.0)

```
 
_______________________________________________________________________
GOT IT!!!!
needed to add -display :0 to your command (per line 10 above)
when the command works it'll spit out the words "Port 5900" before bouncing to the new prompt
 
I also added -localhost (after a reboot) which was approved (same "Port 5900") but stopped me from being able to connect.
 
Rebooted again, placed your command with only -display :0 added and was able to localhost:1 
_______________________________________________________________________
 
While at startup would be nice, at least now I can reboot the computer ssh into it past the command (or maybe we can make a .sh (I've never done that am a linux Ubern00b, so I'd need your aid in crafting it :P ) which I could type "go.sh" have it run
```
 sudo /usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /tmp/x11vnc.log -display :0
```
 
and I'd be good to go
 
_____________________________________________________________________________________________________________________________________________
EDIT3
Ok so once you log out of GUI, it closes the vnc and  you have to run the command again so -forever is looking like it is not functional.
Running the command again lets you in

---

### Post by alfonso78 on 2011-10-19
cheers!

it's the first time I help an other user. I guess I graduated. ;-)

And let's keep trying to find the way to start it automatically, even if I admit it's not a priority.

---

### Post by nergaldicuthah on 2011-10-20
> **alfonso78 said:**
> cheers!

it's the first time I help an other user. I guess I graduated. ;-)

And let's keep trying to find the way to start it automatically, even if I admit it's not a priority.

Congrats and Yes I agree

(I currently have keypass (for windows) 1.x typing the command in :P)

---

### Post by jimbudler on 2011-10-20
Here is what I do:

I have xinetd super server installed.
In the file /etc/xinetd.d/x11vnc:
```
service x11vnc
{
      disable       = no
      type          = UNLISTED
      port          = 5900
      socket_type   = stream
      protocol      = tcp
      wait          = no
      user          = root
      only_from     = 127.0.0.1
      server        = /usr/bin/x11vnc
      server_args   = -inetd -o /var/log/x11vnc.log -xkb -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -rfbauth /home/jim/.vnc/passwd -localhost
}
```

Restart or reload xinetd after creating this file.

I access it via an ssh tunnel and it works whether already logged in on the console or waiting at the login window.

Command from a linux system is like:
```
vncviewer -via host.example.com localhost:0

```

jim

---

### Post by nergaldicuthah on 2011-10-20
> **jimbudler said:**
> Here is what I do:

I have xinetd super server installed.

What is the package name so I can APT-GET

Others in the vino thread have gotten tightVNC working via /etc/lightdm/lightdm but I don't know if that is a pre login like Alfonso and myself are looking for.

Jim's solution seems pretty good, but I'm unclear on if that's allowing x11vnc to start at boot or if we'd still have to initiate xinetd?  if the former it's exactly what we're looking for, I assume root doesn't have to be "user" is that correct, If I wanted the user to be PStar could I use
```
service x11vnc
{
      disable       = no
      type          = UNLISTED
      port          = 5900
      socket_type   = stream
      protocol      = tcp
      wait          = no
      user          = pstar
      only_from     = 127.0.0.1
      server        = /usr/bin/x11vnc
      server_args   = -inetd -o /var/log/x11vnc.log -xkb -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -rfbauth /etc/x11vnc.pass  -localhost
}
```or is user=root replacing the SUDO in alfonso's command?

---

### Post by alfonso78 on 2011-10-21
> **nergaldicuthah said:**
> Others in the vino thread have gotten tightVNC working via /etc/lightdm/lightdm but I don't know if that is a pre login like Alfonso and myself are looking for.

Hi,

tightVNC is not so hard to start with lightDM (I managed during my tests) and I'm sure it would work pre-login.

The problem (in my case) is that I need vnc to SHARE the same desktop with the machine, not to have an other virtual desktop. I mean, when I connect, I can see the pointer of my screen moving. I use this as a kind of remote control.

if it's enough for you to connect and you don't need desktop sharing, I really suggest you look into lightDM support for tightVNC rather then adding xinetd.

I'm not really happy installing that myself. It's an additional server running on the box and I try to install the least possible number of servers for security reasons.

I'm trying to remember by heart, so please allow for some mistake, but to test tightvnc it's quite simple:

```
sudo apt-get install tightvncserver
```

then add this section at the end of /etc/lightdm/lightdm.conf:

```
[VNCServer]
enabled=true
port=5900
```

and then 

```
sudo service lightdm restart
```

to check if it works.

be careful to NOT have x11vnc running otherwise they will both try to listen to port 5900.

Or maybe change the port during your experiments (also remeber to change it in the windows client when you try to connect, they have to match)

normally, you need a good configuration file for tightvnc to work properly, but I didn't get to that stage cause it wasn't my need. Without a nice config file you'll just test that it works and you can login.

hope it helps!

---

### Post by nergaldicuthah on 2011-10-21
lol I think you misunderstood me I also have needs specific to x11vnc
I was more wondering if we could leverage /etc/lightdm/lightdm.conf

as well (note my last post seems to have removed the .conf I apologize to anyone who reads that incorrectly) for ease this is the post to which I refer [http://ubuntuforums.org/showpost.php?p=11370136&postcount=12](http://ubuntuforums.org/showpost.php?p=11370136&postcount=12)

---

### Post by Mlepicki on 2011-10-22
Instead of using xinetd you can start x11vnc right after lightdm using upstart events. Just create  /etc/init/x11vnc.conf file with content: 
start on login-session-start
script
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log
end script

see my [blog post]("http://mlepicki.com/?p=10") for details!

---

### Post by alfonso78 on 2011-10-22
> **Mlepicki said:**
> Instead of using xinetd you can start x11vnc right after lightdm using upstart events. Just create  /etc/init/x11vnc.conf file with content: 
start on login-session-start
script
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log
end script

see my [blog post]("http://mlepicki.com/?p=10") for details!

You're golden!!! that's a great team work! :)

Thank you! :) :)

---

### Post by nergaldicuthah on 2011-10-25
Adding file and rebooting as as I type. Toes Crossed.

EDIT
Oh wow that works better than i'd hoped.
AWesome your blog page is now in my "confirmed works" bookmark collection

---

### Post by emk2203 on 2011-10-27
> **Mlepicki said:**
> Instead of using xinetd you can start x11vnc right after lightdm using upstart events. Just create  /etc/init/x11vnc.conf file with content: 
start on login-session-start
script
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log
end script

see my [blog post]("http://mlepicki.com/?p=10") for details!Just for completeness, I want to chime in with the report that I also got it to work (after a lengthy struggle because I omitted the space in "-display :0"). :)

Just my 2 cents: I have now

```
start on login-session-start

script
    x11vnc -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900
end script
```

as the script in /etc/init/x11vnc.conf, after storing the password with 

```
x11vnc -storepasswd in /etc/x11vnc.pass
``` File attributes are OK from the start, and it works almost like a local window because the overly conservative options are gone.

It works on two systems with Intel graphics and one with Nvidia graphics. The Nvidia system has some artefacts on screen while moving / dragging something, but it's absolutely OK to work with (artefacts are sporadic and temporary).

On the other side, I'm using Windows 7 and UltraVNC. Now my question: Could someone help with getting the -ssl option working?

Ideally, I attach -ssl at the end of the option string, and after login with password, I have an encrypted connection end-to-end. That would effectively give protection against password sniffing (I think we all use sudo when logged in via remote), except for man-in-the-middle attacks which I think are unlikely.

I know that I could use SSH, but I'm looking for something with "one-click", preferably from UltraVNC with one of its encryption modules.

If that's not possible, other VNC viewers are also an option. I tried very briefly ssvnc from Karl Runge, the author of x11vnc, but after using UltraVNC, I am really spoiled by UltraVNC's ease-of-use...

---

### Post by Audiosears on 2011-10-28
emk2203,

After trying SEVERAL different methods of fixing VNC, your solution is by far the best.  I removed all VNC-related packages, and reinstalled vino / vinagre and the associated packages.  Then installed x11vnc, set the default password, and set up the script as you have it there.

The only step I did that you don't have in your post was simply to copy the password file created as ~/vnc/passwd to /etc/x11vnc.pass.  I was then able to take over session 0 w/o having to generate new displays!

---

### Post by emk2203 on 2011-10-29
> **Audiosears said:**
> emk2203,

After trying SEVERAL different methods of fixing VNC, your solution is by far the best.  I removed all VNC-related packages, and reinstalled vino / vinagre and the associated packages.  Then installed x11vnc, set the default password, and set up the script as you have it there.

The only step I did that you don't have in your post was simply to copy the password file created as ~/vnc/passwd to /etc/x11vnc.pass.  I was then able to take over session 0 w/o having to generate new displays!Sorry, my post was misleading because I put the last CODE tags in.

You are right, either copy it over or use
```
x11vnc -storepasswd PaSsWoRd /etc/x11vnc.pass
```(assuming PaSsWoRd is your password) to store it directly (that was what I wanted to show in the first post).

---

### Post by biv on 2011-10-31
This worked almost for me. 

11.10 I reboot, I can vnc successfully to the box (no ssh,no password, its a lab setting)

I see the login screen, I enter my password and click login. 

I am then disconnected. I can see I successfully login on the local side, and x11vnc is not running on login. I cannot reestablish the connection because x11vnc is not running after login.

How do I keep this connection up? I see past versions used the quoted text below which I believe is my symptom. But this is a deprecated solution as this folder structure/gdm is not used anymore. Is there a .config file to enable this parameter? Anyone else had this issue after logging in? Thanks.

> 5. If you restart your PC at this stage you’ll only be able to login, then the GDM will kill your session. To avoid this we must change another file:

sudo gedit /etc/gdm/gdm.conf

now search for this line :

#KillInitClients=true

And change it to this:

KillInitClients=false

---

### Post by biv on 2011-10-31
Okay so I ended up reading through the lightdm.conf and /usr/share/doc/lightdm/lightdm.conf doc. 

I set xserver-allow-tcp=true and it worked. But then removed it and rebooted and it still works.....

Not sure if this achieved actually anything but its working after  several days of being a PITA!

This is by far the most straightforward solution on 11.10

---

### Post by emk2203 on 2011-10-31
> **biv said:**
> This worked almost for me. 

11.10 I reboot, I can vnc successfully to the box (no ssh,no password, its a lab setting)

I see the login screen, I enter my password and click login. 

I am then disconnected. I can see I successfully login on the local side, and x11vnc is not running on login. I cannot reestablish the connection because x11vnc is not running after login.

How do I keep this connection up? I see past versions used the quoted text below which I believe is my symptom. But this is a deprecated solution as this folder structure/gdm is not used anymore. Is there a .config file to enable this parameter? Anyone else had this issue after logging in? Thanks."This" being what? It would help to exactly copy your x11vnc options here.

For example, I made a mistake while copying from this forum, and I had a hard time finding the cause... Did you perhaps forget the -forever option? What does the logfile say?

---

### Post by nergaldicuthah on 2011-11-01
.

---

### Post by GlxyDs on 2011-11-17
I'm able to login remotely but all I can see is a black screen. Can anyone help me with this?

---

