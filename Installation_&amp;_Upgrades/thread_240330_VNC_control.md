---
title: "VNC control"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by YigalB on 2006-08-20
I managed to install the LiveCD, and also to set fixed IP. Now I want to add VNC so I could control this PC from my main PC (so far my main PC is WIndows, sorry guys).
I use RealVNC.
- DO I need to install Real VNC server on my Ubuntu machine or can I install other VNC flavor?
- what do you recommend me to use?
- And most of all - how do I install it?

---

### Post by cavalier on 2006-08-20
I could be wrong, but I don't think you need to install anything. Just got to System->Preferences->Remote Desktop (may be different for you, I'm looking at the menus on a Hoary 5.04 install) and turn on remote desktop sharing.

---

### Post by scxtt on 2006-08-20
cavalier is right, to a degree - but vino only allows you to share your :0 connection, which means you have to already be logged in ... i'd install **vncserver** so that you don't have to always be logged in - you can just kick off a vnc server anytime you want to use it ...

---

### Post by YigalB on 2006-08-21
Thanks, but I dont know how to install VNC server.

---

### Post by scxtt on 2006-08-21
**sudo aptitude install vncserver**

---

### Post by Ek0nomik on 2006-08-22
Thanks scxtt.

Following that, I typed vncserver, it asked me for a password, and I put it in.

I downloaded the viewer for my other computer (which runs Windows), I typed in my IP, and tried to connect, and my connection got refused.  I typed in my internal IP.

I'm new to Linux as well.  I know in windows you can do an ipconfig, is there any such thing in Linux?  I want to do that strictly so I can double check my internal IP.

Otherwise, what am I doing wrong?

---

### Post by scxtt on 2006-08-22
did you type in **<IP-address>:1**?  when you start the server it will tell you what session you should connect to ...

you should get something like this:
```
:> vncserver

New 'X' desktop is madiera-kubuntu:1

Starting applications specified in /etc/X11/Xsession
Log file is /home/scxtt/.vnc/madiera-kubuntu:1.log
```and you should probably use your IP, not the hostname - unless you have it stored on your Windows box too ...

are you using realVNC for Windows?

---

### Post by Ek0nomik on 2006-08-22
> **scxtt said:**
> did you type in **<IP-address>:1**?  when you start the server it will tell you what session you should connect to ...

you should get something like this:
```
:> vncserver

New 'X' desktop is madiera-kubuntu:1

Starting applications specified in /etc/X11/Xsession
Log file is /home/scxtt/.vnc/madiera-kubuntu:1.log
```and you should probably use your IP, not the hostname - unless you have it stored on your Windows box too ...

are you using realVNC for Windows?

I did get all of that.  I am using realVNC for Windows.

I didn't type the :1.  I did that this time, but all that comes up is a very staticy like screen.  I have used UltraVNC, and other remote connections before.  The screen looks as if you have a scrambled television screen.  Any ideas?  I can print screen it if you need.

---

### Post by Ek0nomik on 2006-08-22
Nevermind.  It won't let me print screen while I have VNC open.  Makes partial sense, I guess I wouldn't know how to explain it really.  Just like you can't print screen something that's playing on your DVD player I suppose.

It's basically just a staticy screen.  I was able to login, it took my password fine.  Basically it just isn't displaying my other box at all.

---

### Post by scxtt on 2006-08-22
that's very odd, all i have to do is install the package, start the server and i get my normal KDE session, same w/ Gnome ...

---

### Post by Ek0nomik on 2006-08-22
192.168.1.102:1

That's what I put into RealVNC (E4.2.6).  It asks for a password, I put it in.  Than a black, almost checkered like screen appears.  My mouse becomes a rather larger black X too, not sure if that's normal or not.

I'm trying to run some searches on google, but no luck so far.

---

### Post by Ek0nomik on 2006-08-22
[IMG]http://webpages.charter.net/muznic/vnc.jpg[/IMG]

Maybe that will help someone.

---

### Post by nquinnathome1 on 2006-08-28
If you're just getting the X Server screen (black/white/grey) with an X on it, then you should be able to correct this by logging onto the machine directly (i.e. sitting in front of it) and doing the following:

System > Administration > Login Window
Remote tab
Make sure that the chosen style is 'Same as local'
Press "Configure XDMCP" button
Uncheck "Honor Indirect Request"
Close both windows and restart the Ubuntu box.

Once it has restarted, you should be able to see the screen via VNC.

---

### Post by drake18746 on 2006-09-06
Hi.  I'm getting the exact same issue regarding VNC.  I've taken every step you've dictated in this, and I'm still getting the same result; the X server screen.

---

### Post by phersotty on 2006-09-06
have you tried connecting the opposite way?  See if you can bring up the XP screen remotely in Ubuntu.  If it works then maybe you just need to tweek the screen configuration in the XP viewer.  Also another thing you could try is using a different VNC viewer in Windows and see if you get the same problem.  I use UltraVNC in XP. It has an option that allows you to connect through an Internet browser using a Java plugin.

---

### Post by drake18746 on 2006-09-06
Well, VNC viwer works from the Linix tower to my laptop just fine.  In fact, I'm typing through it right now, so there are no issues.  I'm going to try getting a different viewer client like you suggested and check back in a few minutes one way or another.

---

### Post by drake18746 on 2006-09-06
Alright, I downloaded UltraVNC.  I don't like it very much, but that's only becuase I've been using RealVNC for so long that I'm totally accustomed to it.

At any rate, I ended up with the same problem.  And I don't know how to connect to the desktop through a java console in Firefox with UltraVNC.

---

### Post by phersotty on 2006-09-06
Have you tried nquinnathome1's instructions in post 13?  Since you are getting the same problem no matter which viewer you use it has to be on the Ubuntu system.  Try setting to display same as host like nquinnathome1 mentions above.

---

### Post by drake18746 on 2006-09-06
That was one of the things I did, yes.  Just to be on the safe side I'll double check the settings and reboot.  It obviously can't hurt.  I don't have high hopes for it though.  *frown*

---

### Post by drake18746 on 2006-09-06
Yeah, like I thought, it didn't work.  I'm totally stuck for ideas.  Then again, I never had any to begin with.

---

### Post by phersotty on 2006-09-06
I found this in RealVNC's faq.  [http://www.realvnc.com/faq.html#grey](http://www.realvnc.com/faq.html#grey)

It might help :confused:

---

### Post by motin on 2006-10-08
Either you use Remote Desktop (vino) that comes with Ubuntu, or you use VNC OR FreeNX. There is a HOWTO on this matter here:

HOWTO: Set up VNC server with resumable sessions (already done in this thread mostly) - [http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

OR 

HOWTO: FreeNX on Dapper LTS 6.06 - [http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto](http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto)

FreeNX is faster than VNC.

---

