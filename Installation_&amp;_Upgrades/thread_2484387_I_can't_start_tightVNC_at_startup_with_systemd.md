---
title: "I can't start tightVNC at startup with systemd"
date: 2023-02-24
forum: Installation &amp; Upgrades
---

### Post by zenvice on 2023-02-24
[COLOR=#141414][FONT=&quot]Hello ![/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]My system : Ubuntu 22.04.2 LTS (GNU/Linux 5.19.0-32-generic x86_64)[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]After installing Tightvnc, I scrupulously followed the instructions to fill in a service file so that my vnc server restarts every time ubuntu starts (Recommendation from this site, and many other tests: [/FONT][/COLOR][https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)[COLOR=#141414][FONT=&quot]):[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot][Unit][/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Description=Start TightVNC server at startup[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]After=syslog.target network.target[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot][Service][/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Type=forking[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]User=mysusername[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Group=mysusername[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]WorkingDirectory=/home/mysusername[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]PIDFile=/home/mysusername/.vnc/%H:%i.pid[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 -localhost :%i[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]ExecStop=/usr/bin/vncserver -kill :%i[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot][Install][/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]WantedBy=multi-user.target[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]The service starts and port 5901 is busy, but I can't access my system through a vnc viewer.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]The service is running and port 5901 is busy, but I can't access my system through a vnc viewer, but when I run a simple command line via ssh "vncserver:1" it works. Can you help me?[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Good day to you[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-02-24
Please post the results of
```

echo $USER

```\...becuase in your post, the user name 'myusername' is probably not a valid user of your system...

---

### Post by zenvice on 2023-02-25
In fact, but i had just replace my real username with "myusername" for this post :P

---

### Post by MAFoElffen on 2023-02-25
Oh, okay. Then please show the output of
```

sudo systemctl status vncserver@1.service

```
Then any errors on
```

ssh -L 59000:localhost:5901 -C -N -l myusername your_server_ip

```
And while the tunnel is established
```

sudo lsof -i -n | grep '\<ssh\>\|\<sshd\>'

```

---

### Post by zenvice on 2023-02-26
Hello, 

Thank you for you answer MAFo, however i can start my service now, i must change exectstart= command line with : [COLOR=#141414]ExecStart=/usr/bin/vncserver :%i

And it's ok. But the service is launch without sudo rights.

I had try to change the line exectstart with [/COLOR][COLOR=var(--black-800)][FONT=var(--ff-mono)]ExecStart=/usr/bin/sudo [/FONT][/COLOR][COLOR=#141414]/usr/bin/vncserver :%i

But nothing... Though the service doesn't start, maybe because de sudo command ask my passwd ?

Zenvice[/COLOR]

---

### Post by ActionParsnip on 2023-02-26
What are you wanting to do on the remote system? There may be a sleeker solution to what you want to do

---

### Post by zenvice on 2023-02-26
I m looking for manage my serveur altought gui for my downloads, and soft on wine for exemple.

So, automating server startup in sudo would be great !

---

### Post by ActionParsnip on 2023-02-26
What do you mean "GUI for downloads"? There are download managers with Web interfaces. Torrent apps also have Web interfaces too....?

---

### Post by zenvice on 2023-02-26
yes torrents with qtorrent and browser or metatrader 4 with wine

---

### Post by ActionParsnip on 2023-02-26
> **zenvice said:**
> yes torrents with qtorrent and browser or metatrader 4 with wine


Qbittorrent has.a.web UI
You can manage your torrents easily with a Web browser and changing "localhost" in the usual browser access to the IP of the remote system. No need for VNC there.

---

### Post by ActionParsnip on 2023-02-26
[https://www.metatrader4.com/en/trading-platform/help/userguide/install_linux](https://www.metatrader4.com/en/trading-platform/help/userguide/install_linux)

Metatrader seems to have a native client.... Why use WINE?

---

### Post by zenvice on 2023-02-26
Ok thank you, but for the time spent installing the vnc server, so close to the goal I would have liked to know just for my own culture why the service doesn't want to start with sudo rights on startup, when it has the rights when I simply activate it from the command line with "vncserver".

---

### Post by ActionParsnip on 2023-02-26
If you connect to the remote system via SSH and use the "-X" option, then you can run the application on a system with an X server (Linux client systems and Mac OS have this by default) then the application will be running on the remote system but display on the local PC. Very handy

---

### Post by zenvice on 2023-02-26
Remote SSH with -X option ? Tell me more...

---

### Post by MAFoElffen on 2023-02-27
You know that when a service file starts, that systemd starts it as 'root' right? You are confusing me why you would want to use 'sudo' in your exec as root(???)

Also, in Linux, there are hundreds of ways to do the same thing. 

OpenSSH server with X forwarding... You just use
```

ssh -X myusername@machine_IP commmand_of_app
# for example, for a test
ssh -X mafoelffen@10.0.0.3 xeyes
# See attachment

```
I use xrdp server allot. It is actively listening all the time. You can only a a user logged in once, so I setup an xrdp user, that way if I am logged in, that I don't have to go to that machine just to log myself out. 

Most of the time, honestly, I just use ssh. Unless I am connecting to a VM, with a desktop. Then there is a variety of things I use.

---

### Post by zenvice on 2023-02-27
Ok, i have an exemple for explain my trouble :

When i try to stop an important setting as my wired connection with "vncserver" command in terminal, it's possible in exchange for a password : [https://zupimages.net/viewer.php?id=23/09/2p96.png](https://zupimages.net/viewer.php?id=23/09/2p96.png)

In constrast, when it's automatically launch with systemd with the command [COLOR=#666666][FONT=&amp]ExecStart=/usr/bin/vncserver my privilege seem not be the same, because i can't change settings, even in exchange of passaword. 
However it's the same user :   [/FONT][/COLOR]https://zupimages.net/viewer.php?id=23/09/o6vy.png[IMG]https://zupimages.net/viewer.php?id=23/09/o6vy.png[/IMG][COLOR=#666666][FONT=&amp]
[/FONT][/COLOR][IMG]https://zupimages.net/viewer.php?id=23/09/o6vy.png[/IMG][IMG]https://zupimages.net/viewer.php?id=23/09/o6vy.png[/IMG]

---

### Post by MAFoElffen on 2023-02-27
So, what you are saying (if I understand correctly) is that the problem is that without logging in your user, that your wireless connection is not made?

And you know that, because you are trying to connect remotely, that your IP should be configured as static, correct?

---

### Post by zenvice on 2023-02-28
My connection isn't the trouble, the trouble is : i can change setup as admin in the first case, in contrast i can't change it when i open vnc automatically (difference of privilege between these two ways and i don't know why).

---

### Post by MAFoElffen on 2023-02-28
"change privilege"... Do you mean lie 
```

sudo -i
#or 
sudo su

```
I guess i don't quite understand you yet. Please explain so we are on the same understanding.

---

### Post by zenvice on 2023-02-28
Hello MAFo !

Ok so, in the first case, the command in terminal "vncserver" open a place on vnc server where i can connect with administrator privilege.
 
When the place on vnc server is open automatically with the file system create (see my first message in this post), the server log me as an viewer privilege, and not administrator. However it's the same command "vncserver" yet it is the same command that is written automatically...

Write the command /usr/bin/sudo can't work because i must enter the system pass in clear in this file in clear to make it work i guess, but i won't write in clear my password for security reason.

Is it clearer ?

---

### Post by MAFoElffen on 2023-02-28
I still do not understand what "you are saying." That may be due to a language difference barrier.

I guess I'm going to have to spin up a VM , install tightVNC for myself, to see if there is any difference like you seem to be explaining, so we can talk together, with the same understanding.

This should not be as difficult as you seem to be explaining.

---

### Post by zenvice on 2023-03-01
Okay, so I'll explain as simply as possible, with the translator this time. 


When I run the vncserver command in the terminal, I can access this vnc server with my client and disconnect or connect the vpn without any problem in exchange of a password, which must mean that I have administrator privileges.


But when I run this vncserver command automatically with my system script that I created here: /etc/systemd/system/vncserver@.service


and that I have filled in as follows: 


[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target


[Service]
Type=forking
User=jeremy
Group=jeremy
WorkingDirectory=/home/jeremy


PIDFile=/home/jeremy/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver :%i
ExecStop=/usr/bin/vncserver -kill :%i


[Install]
WantedBy=multi-user.target


The server starts but in this case, unfortunately, I can't change any connection or other parameters. So my question is the following: How to launch automatically a session or I could have the administrator privileges automatically?


See the tutorial I followed: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)

---

### Post by MAFoElffen on 2023-03-01
I am following that tutorial and seeing for myself.

You should have those permissions associated with your userid, that you log in with, as it is a member of the sudo group. But when I finish going through this, I will test that for sure.

EDIT: Using "translate", that was a lot easier for me to understand what you were trying to say. Thank you very much.

---

### Post by ActionParsnip on 2023-03-01
Can you run your apps OK with X forwarding?

---

### Post by zenvice on 2023-03-01
I agree with your diagnosis, yet the same login does not give me the same rights in this case. Tt is my turn to say thank you ! ;)

So far I've tried launching the default browser and firefox, it doesn't launch, but qttorrent does, but I'll deal with those other issues later, unless there's a link?

---

### Post by MAFoElffen on 2023-03-01
I was in the middle of an install on a VM, when my wife popped the circuit breaker with her hair dryer. LOL.

Reinstalling it now.

---

### Post by zenvice on 2023-03-03
ok, thanks! A tip for the next one, turn off the lights before using the hair dryer. hahaha

---

### Post by zenvice on 2023-03-07
Hi,

No one left in the room?

---

### Post by ActionParsnip on 2023-03-07
What is the current status?

---

### Post by zenvice on 2023-03-07
I'm waiting for the return of the tests that Mafoelfen must be doing, on my side I still haven't found anything that works.

---

### Post by MAFoElffen on 2023-03-09
Installed and running as a service:
```

mafoelffen@lunar-server-01:~$ sudo systemctl status vncserver@1.service
&#9679; vncserver@1.service - Start TightVNC server at startup
     Loaded: loaded (/etc/systemd/system/vncserver@.service; enabled; preset: e>
     Active: active (running) since Thu 2023-03-09 06:49:27 UTC; 9s ago
    Process: 10199 ExecStartPre=/usr/bin/vncserver -kill :1 > /dev/null 2>&1 (c>
    Process: 10203 ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 -l>
   Main PID: 10214 (Xtightvnc)
      Tasks: 3 (limit: 4555)
     Memory: 12.7M
        CPU: 103ms
     CGroup: /system.slice/system-vncserver.slice/vncserver@1.service
             &#9500;&#9472;10214 Xtightvnc :1 -desktop X -auth /home/mafoelffen/.Xauthority>
             &#9492;&#9472;10222 xfce4-session

Mar 09 06:49:26 lunar-server-01 systemd[1]: Starting Start TightVNC server at s>
Mar 09 06:49:26 lunar-server-01 vncserver[10199]: Can't find file /home/mafoelf>
Mar 09 06:49:26 lunar-server-01 vncserver[10199]: You'll have to kill the Xtigh>
Mar 09 06:49:27 lunar-server-01 vncserver[10203]: New 'X' desktop is lunar-serv>
Mar 09 06:49:27 lunar-server-01 vncserver[10203]: Starting applications specifi>
Mar 09 06:49:27 lunar-server-01 vncserver[10203]: Log file is /home/mafoelffen/>
Mar 09 06:49:27 lunar-server-01 systemd[1]: Started Start TightVNC server at st>
lines 1-20/20 (END)

```
On connect it frags out for me... See screenshot in the attachment... That was with Remmina: localhost:59000. 

Thing is I can connect via xrdp ans ssh -X. I don't understand why, but TightVNC was tweaky for me. Could be that I was doing it on Lunar 23.04.

I should say that I followed the tutorial, but couldn't really agree with the use case. That tutorial is to setup a vncviewer/vncserver on the same machine. Most use-cases are to connect to a remote computer, not to the same computer. That use case is confusing for me, on why someone would need to do that.

On doing ssh -X forwarding to start the desktop apps an a remote computer- It worked for me if you wanted to open a Grahical Terminal session on from the remote on the local desktop. There were possibilities there, but not any more than if you were doing straight ssh to it. I could not remotely start a file manager remotely through X Forwarding. I don't know what else to try with that... Just to say it was limited.

That same VM connected fine doing xrdp and x2go...

---

### Post by zenvice on 2023-03-09
I think the procedure I followed shows the installation of a viewer and a server, but of course in practice it is not on the same machine. I'm interested in the server because the viewer works well from a distance. I am on my side on ubuntu 22.04 and start in Xorg/ubuntu. So much the worse, thank you for your time anyway, I hope that the fuses do not blow anymore in your home hehe. I'll look for other solutions and will share them here if I find them.

---

### Post by zenvice on 2023-03-12
For my mental health, I finally opted for the rdp, as explained in this link for an Ubuntu 22.04 system: [https://www.digitalocean.com/community/tutorials/how-to-enable-remote-desktop-protocol-using-xrdp-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-enable-remote-desktop-protocol-using-xrdp-on-ubuntu-22-04)


Goodbye to you

---

