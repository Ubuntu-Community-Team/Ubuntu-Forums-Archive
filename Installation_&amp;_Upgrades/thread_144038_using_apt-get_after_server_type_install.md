---
title: "using apt-get after server type install"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by tzuriel on 2006-03-13
Hi,

I see that this is a very helpful forum.  I hope you can help me.

I followed the instructions at 
[https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28install%29](https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28install%29)

but when I ran

```
sudo apt-get install gdm x-window-system-core xterm icewm menu mozilla-firefox abiword synaptic
```


from the command-line, I got all sorts of errors about "unable to stat source package xxxxx" with many urls.  I then ran 

```
sudo apt-get install gdm x-window-system-core xterm
```

and was able to get an X session but it's painfully slow and the desktop never comes up.

Does apt-get connect to the web to get these packages?  i thought they would all be on the hdd or the install CD.  I don't seem to actually have a connection to the internet from this command-line only display.

This is a Pentium 2 450 with 384 MB of RAM.  It previously ran a fully loaded X server with KDE Red Hat 9 install without any problems.  Any suggestions for a newbie?

Thanks,

Tzuriel

---

### Post by aysiu on 2006-03-13
What does your /etc/apt/sources.list look like?

---

### Post by Zelut on 2006-03-13
Well the first problem I see with your command is you haven't 'updated' the sources list yet.  I would suggest doing the following:

sudo apt-get update
sudo apt-get install <your-long-list-of-packages>

That should clear up your 'unable to stat' issue, also give you any available updates.

Let me know if that helps out.  If not we'll look deeper.
(yes, packages are installed from the web so you do need a connection)

---

### Post by tzuriel on 2006-03-13
[QUOTE=kuyaedz]Well the first problem I see with your command is you haven't 'updated' the sources list yet.  I would suggest doing the following:

sudo apt-get update
sudo apt-get install <your-long-list-of-packages>

That should clear up your 'unable to stat' issue, also give you any available updates.

Let me know if that helps out.  If not we'll look deeper.
(yes, packages are installed from the web so you do need a connection)[/QUOTE]
I had tried sudo apt-get update prior to my post.  Sorry for not mentioning it.  It resulted in the same unable to stat errors, looking for urls.  

How can I check to see if I am connected to the internet from the command line?  I tried to ping [www.google.com](www.google.com) but got unknown host errors.

---

### Post by tzuriel on 2006-03-13
[QUOTE=aysiu]What does your /etc/apt/sources.list look like?[/QUOTE]

I'll will get back to you with this information.  Might be a couple days though.  Thanks for reply!

---

### Post by megabyte405 on 2006-04-19
Any luck?  All of those packages should be in main, which is to say, enabled by default in the sources.list file.  Make sure you're connected to the internet, and that your network card is listed and working when you type "sudo ifconfig" (should be eth0 or something else if it's wireless - dialup needs configuration)

---

