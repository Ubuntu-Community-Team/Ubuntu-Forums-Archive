---
title: "Problem with Snakebite bittorrent software"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by dabsan on 2006-08-31
I have installed the Snakebite bittorrent software but when I try to start the software from from the Terminal I get this error :-

darren@darren-desktop:~$ sudo /etc/init.d/snakebite start
 * Starting Snakebite...                                                 [ ok ]
darren@darren-desktop:~$ Traceback (most recent call last):
  File "/usr/bin/snakebite", line 16, in ?
    from BitTorrent.defaultargs import get_defaults
ImportError: No module named BitTorrent.defaultargs

Really hope someone can give me some advice on how to solve this problem. Many Thanks :confused:

---

### Post by skymt on 2006-08-31
Looks like it shares code with the official Bittorrent client. Install that (sudo apt-get install bittorrent) and it should work.

---

### Post by dabsan on 2006-08-31
Thanks for your quick reply and advice, I tried installing the bttorrent but it says latest version is already there and the same error is appearing when I try to start Snakebite. 
I even tried re-installing both bittorrent and Snakebite but the same error appears again. Any other ideas? :confused:

---

### Post by skymt on 2006-08-31
[COLOR="Silver"]Let's check your path:

* Run 'python' in a terminal.
* When you get the prompt (>>> ), enter this:
```

import sys
print sys.path

```
* Post the output.[/COLOR]

---

### Post by skymt on 2006-08-31
Never mind that. I just downloaded snakebite for myself and took a peek at the source. Here's what to do:

* Enter 'gksudo gedit /usr/bin/snakebite' in a terminal.
* On the first line, replace 'python2.3' with 'python2.4'.

That should fix it for real.

---

### Post by dabsan on 2006-08-31
Hi,I have replaced python2.3 with python2.4 on the first line but I still get the error when starting snakebite.

darren@darren-desktop:~$ sudo /etc/init.d/snakebite start
 * Starting Snakebite...                                                 [ ok ]
darren@darren-desktop:~$ Traceback (most recent call last):
  File "/usr/bin/snakebite", line 16, in ?
    from BitTorrent.defaultargs import get_defaults
ImportError: No module named defaultargs

---

### Post by skymt on 2006-08-31
Do you have the folder /usr/lib/python2.4/site-packages/BitTorrent? If so, does it have the file defaultargs.py?

---

### Post by dabsan on 2006-08-31
I have the folder /usr/lib/python2.4/site-packages/BitTorrent but I don't have the defaultargs.py file. How do I install it? 
Thanks

---

### Post by skymt on 2006-08-31
A bit of research reveals that it is not, in fact, in the version of Bittorrent (3.x) that Ubuntu provides. It is, however, in the most recent version (4.x). You can download a .deb for that [here](http://download.bittorrent.com/dl/bittorrent_4.20.9_python2.4.deb).

---

### Post by dabsan on 2006-08-31
I installed the most recent version (4.x) of Bittorrent and it has solved that error but now I am getting an error on line 25 

darren@darren-desktop:~$ sudo /etc/init.d/snakebite start
 * Starting Snakebite...                                                 [ ok ]
darren@darren-desktop:~$ Traceback (most recent call last):
  File "/usr/bin/snakebite", line 25, in ?
    from snakebite.track import track
ImportError: No module named snakebite.track

Any ideas to solve this? :confused:

---

### Post by skymt on 2006-08-31
Try this in a terminal: 'sudo ln -s /usr/lib/python2.3/site-packages/snakebite/ /usr/lib/python2.4/site-packages/snakebite/'

---

### Post by dabsan on 2006-08-31
ok I tried that but I got this error :- 

darren@darren-desktop:~$ sudo ln -s /usr/lib/python2.3/site-packages/snakebite/ /usr/lib/python2.4/site-packages/snakebite/
ln: target `/usr/lib/python2.4/site-packages/snakebite/' is not a directory: No such file or directory

---

### Post by skymt on 2006-08-31
Oops! Sorry, copy/paste error. Take off the last slashes:

```

sudo ln -s /usr/lib/python2.3/site-packages/snakebite /usr/lib/python2.4/site-packages/snakebite

```

---

### Post by dabsan on 2006-08-31
Ok .... it is working now :D 
:cool: Many Thanks :cool:

---

### Post by skymt on 2006-08-31
You're very welcome.

You may want to contact the Snakebite developers. The problems you had are mostly due to the fact that Bittorrent uses Python 2.4, while Snakebite uses 2.3 by default. Point them to this thread and say, "fix it!"

---

### Post by dabsan on 2006-08-31
Yes I will do. ;)

---

### Post by dabsan on 2006-09-01
I thought everything was working fine but when I started snakebite today I got this error :-

darren@darren-desktop:~$ sudo /etc/init.d/snakebite start
 * Starting Snakebite...                                                 [ ok ]
darren@darren-desktop:~$ Traceback (most recent call last):
  File "/usr/bin/snakebite", line 145, in ?
    sb.webServer()
  File "/usr/bin/snakebite", line 86, in webServer
    ws = WebServer(self.conpar.dir_torrents, self.conpar.dir_web, self.conpar.dir_temp, self.conpar.username, self.r)
  File "/usr/lib/python2.4/site-packages/snakebite/server.py", line 21, in __init__
    s = self.r.create_serversocket(6060, '', True)
  File "/usr/lib/python2.4/site-packages/BitTorrent/RawServer_twisted.py", line 762, in create_serversocket
    raise e.socketError
error: (98, 'Address already in use')

Any ideas how to get this working? :confused:

---

### Post by skymt on 2006-09-02
It looks like you already have a Snakebite process running. That error message, decoded, means "I tried to listen on this port, but there's already something else on the same port!" Try a 'ps -e' and see if you can find it.

I apologize for the delayed answer, but my power was out all yesterday due to a tropical storm. Moderate flooding, massive power losses, branch down in the driveway, etc.

---

### Post by dabsan on 2006-09-02
Hi, thank you for the reply, yes I did a 'ps -e' and yes snakebite is already running. I am very greatful for your help.

Seems you are having some terrible weather there, hope everything returns to normal soon.

---

