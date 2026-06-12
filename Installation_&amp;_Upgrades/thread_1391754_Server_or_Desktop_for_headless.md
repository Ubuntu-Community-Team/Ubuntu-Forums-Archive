---
title: "Server or Desktop for headless"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by mbro0 on 2010-01-27
Hi all,

I am a total noob with regards Linux so will undoubtedly frequent this board asking some lame questions in the coming weeks.

At present I am trying to setup a LAMP Server on an old desktop machine I have lying about, however there is not going to be a keyboard, monitor or mouse attached beyond the installation process.

My question simply is am I best installing the server or desktop version of Ubuntu for this requirement?

I have been playing with Desktop 9.04 and found it tough to use headlessly, however understand that Server 9.04 fully supports headless access.

Being a newbie I do prefer to use the GUI to make changes and generally play around, so a UI such as GNOME would be essential.  Having read about I understand the best way to access remotely is to install SSHServer and VNCServer and then login over SSH and VNC into the box.

My remote machine I will use to connect to Ubuntu is a Windoze 7/XP machine.

I appreciate any help.

Thanks

---

### Post by bullgr on 2010-01-27
ubuntu server is the only way you need to go...

yes, yes, i know, it is difficult... but if you master ubuntu server you'l be the hapiest man in the world!!!

and you can do anything you want...

of course there are many different arguments... the point is that anyone is free to work as he like... for me, the command line is better for servers than gui... for others, they prefer to use gui (like redhat users). choose that you make you more comfort... either command line of gui, whe only that matters is to do your job.

note: you can use command line and manage many things (almost all) from the web based webmin ([http://www.webmin.com/](http://www.webmin.com/)) that is also in the ubuntu repos ready to install.

---

### Post by mbro0 on 2010-01-27
Thanks for the reply.

I just had a quick look at webmin - like you mentioned it does seem to do all the things I need it to and has a compromise between GUI and Command line.

I will delve further into this now...... thanks

---

### Post by mbro0 on 2010-01-27
OK - rather than start a new thread, I posted in here again.

I installed the server version OK, however when I tried to run anything at the prompt it always came back saying command unknown or similar.

i.e. auto eth0 - came back as bash auto command unknown (or similar)

I have resorted to installing the ubuntu desktop - however I want to know if i will still be able to headlessly connect to this in future or if I have screwed this up?!

Thanks

---

### Post by bullgr on 2010-01-27
like i said above, either command line or gui, the point is to do the job...
of course you can connect anytime you like in the ubuntu desktop...

note that the services are runing when you are in the login screen... this means that you do not need to login everytime you use the server. you just need to push the power button to open or close the server. so no monitor and keyboard are needed.

as i see, you must realy study the server concepts... it's not easy...
you can start from this great tutorial: [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

note: as you can see, the tutorial uses the last lts version of ubuntu (8.04)... it is important for servers to use the last lts (long term support) version, because it's more stable than the ordinary versions and has 5 years support of updates...

---

### Post by ZooDirt on 2010-01-27
You haven't screwed up anything by installing ubuntu-desktop

I've been running a headless Ubuntu server for years.  All I have connected to this is a power cord and an ethernet cable.  I do as much as I can from the CLI, but have the desktop installed and waiting for when I need a crutch.   

Here's what I do each time I rebuild:

1.Start with a LAMP.  (Just like you did)
2.Make sure you have an sshd (secure shell) installed.
3.Install ubuntu-desktop while your at it.  (sudo apt-get install ubuntu-desktop)
4.While you have your monitor, keyboard, and mouse connected you can enable remote desktop sharing, which will allow you to connect to your server via vncviewer (or something other) running on your laptop or other computer to get to the GUI on your headless server.  

With this set up you have the best of both worlds.  Sure, it kind of defeats the purpose of a LAMP server, but it's your server right?   You can do what you want!!!  Do as much as you can via ssh and the CLI, but connect through VNC when you get stuck.

---

### Post by mbro0 on 2010-01-28
Thanks guys

Good suggestion about using 8.04LTS there, as I am using 9.04 at present which I guess isnt as stable.

My other major problem though is to do with the fact that my network card is a USB wireless dongle.  I can hear laughter and sighs already, but its all thats available to me to use.

They are recognised OK using the GUI but networking isnt available without the GUI - I have looked around for using wpa_supplicant etc but cant find anything comprehensive for 9.04.

---

