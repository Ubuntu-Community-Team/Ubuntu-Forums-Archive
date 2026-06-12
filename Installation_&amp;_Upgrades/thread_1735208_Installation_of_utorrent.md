---
title: "Installation of utorrent"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by sandy0594 on 2011-04-21
Hey all,i am new to Ubuntu,i have Ubuntu 10.10 installed..I wanted to install utorrent..so,i downloaded it from [http://www.utorrent.com/downloads/complete?os=linux](http://www.utorrent.com/downloads/complete?os=linux)
I installed wine..but,i am unable to know what to do next..

here is what i did

```

sandy@ubuntu:~$ cd '/home/sandy/Downloads' 
sandy@ubuntu:~/Downloads$ tar -xvf utorrent-server-3.0-25053.tar.gz
utorrent-server-v3_0/
utorrent-server-v3_0/docs/
utorrent-server-v3_0/docs/Server_Changes.html
utorrent-server-v3_0/docs/license.txt
utorrent-server-v3_0/docs/uTorrent_Server.txt
utorrent-server-v3_0/docs/Server_Changes.txt
utorrent-server-v3_0/docs/uTorrent_Server.pdf
utorrent-server-v3_0/docs/footer_ut_address.gif
utorrent-server-v3_0/docs/Server_Changes.pdf
utorrent-server-v3_0/docs/Changes.txt
utorrent-server-v3_0/docs/uTorrent_Server.html
utorrent-server-v3_0/docs/ut-logo.gif
utorrent-server-v3_0/docs/style.css
utorrent-server-v3_0/utserver
utorrent-server-v3_0/webui.zip


```

Can anyone say me what  to do next

---

### Post by DanneStrat on 2011-04-22
> **sandy0594 said:**
> Hey all,i am new to Ubuntu,i have Ubuntu 10.10 installed..I wanted to install utorrent..so,i downloaded it from [http://www.utorrent.com/downloads/complete?os=linux](http://www.utorrent.com/downloads/complete?os=linux)
I installed wine..but,i am unable to know what to do next..

here is what i did

```

sandy@ubuntu:~$ cd '/home/sandy/Downloads' 
sandy@ubuntu:~/Downloads$ tar -xvf utorrent-server-3.0-25053.tar.gz
utorrent-server-v3_0/
utorrent-server-v3_0/docs/
utorrent-server-v3_0/docs/Server_Changes.html
utorrent-server-v3_0/docs/license.txt
utorrent-server-v3_0/docs/uTorrent_Server.txt
utorrent-server-v3_0/docs/Server_Changes.txt
utorrent-server-v3_0/docs/uTorrent_Server.pdf
utorrent-server-v3_0/docs/footer_ut_address.gif
utorrent-server-v3_0/docs/Server_Changes.pdf
utorrent-server-v3_0/docs/Changes.txt
utorrent-server-v3_0/docs/uTorrent_Server.html
utorrent-server-v3_0/docs/ut-logo.gif
utorrent-server-v3_0/docs/style.css
utorrent-server-v3_0/utserver
utorrent-server-v3_0/webui.zip


```

Can anyone say me what  to do next

Hi.

Since you got the native linux version, you don't

need to use "wine". Try this:

```
cd ~/Downloads/utorrent-server-v3_0
```

Then do:

```
./utserver
```

And utorrent will start.

---

### Post by sandy0594 on 2011-04-22
There is nothing happening mate....

```

sandy@ubuntu:~$ cd '/home/sandy/Downloads/utorrent-server-v3_0' 
sandy@ubuntu:~/Downloads/utorrent-server-v3_0$ ./utserver
server started - using locale en_US.UTF-8
Using locale en_US.UTF-8
total physical memory -1 max disk cache 33554432
IPv6 is installed


```

The cursor is blinking

---

### Post by DanneStrat on 2011-04-22
> **sandy0594 said:**
> There is nothing happening mate....

```

sandy@ubuntu:~$ cd '/home/sandy/Downloads/utorrent-server-v3_0' 
sandy@ubuntu:~/Downloads/utorrent-server-v3_0$ ./utserver
server started - using locale en_US.UTF-8
Using locale en_US.UTF-8
total physical memory -1 max disk cache 33554432
IPv6 is installed


```

The cursor is blinking

I think you got the wrong utorrent

version. "utorrent server" is the "non-graphical"

version and it is supposed to be like that.

If you were planning to use the windows version of utorrent,

get the windows version from here:

[http://www.utorrent.com/downloads/complete?os=win](http://www.utorrent.com/downloads/complete?os=win)

Then you can right-click the .exe and "run with wine launcher".

---

### Post by sandy0594 on 2011-04-22
> utorrent-server-3.0-25053.tar.gz
This is what I downloaded

---

### Post by DanneStrat on 2011-04-22
> **sandy0594 said:**
> This is what I downloaded

Yes, but if you want the graphical version(not the command line 

version), try following my instructions above.

---

### Post by sandy0594 on 2011-04-22
Yeah..i prefer graphical version,i just wanted to know how the Linux version works that's it.

---

### Post by Bucky Ball on 2011-04-22
[http://www.utorrent.com/downloads/complete?os=linux](http://www.utorrent.com/downloads/complete?os=linux)

That's the Linux GUI version. Just install it. ;) 

Wine is nigh on impossible to get rid of completely if you ever want to uninstall that, incidentally.

---

### Post by sandy0594 on 2011-04-22
I have that downloaded..but,i am unable to use it..

```

sandy@ubuntu:~/Downloads/utorrent-server-v3_0$ cd '/home/sandy/Downloads' 
sandy@ubuntu:~/Downloads$ tar -xvf utorrent-server-3.0-25053.tar.gz
utorrent-server-v3_0/
utorrent-server-v3_0/docs/
utorrent-server-v3_0/docs/Server_Changes.html
utorrent-server-v3_0/docs/license.txt
utorrent-server-v3_0/docs/uTorrent_Server.txt
utorrent-server-v3_0/docs/Server_Changes.txt
utorrent-server-v3_0/docs/uTorrent_Server.pdf
utorrent-server-v3_0/docs/footer_ut_address.gif
utorrent-server-v3_0/docs/Server_Changes.pdf
utorrent-server-v3_0/docs/Changes.txt
utorrent-server-v3_0/docs/uTorrent_Server.html
utorrent-server-v3_0/docs/ut-logo.gif
utorrent-server-v3_0/docs/style.css
utorrent-server-v3_0/utserver
utorrent-server-v3_0/webui.zip
sandy@ubuntu:~/Downloads$ cd ~/Downloads/utorrent-server-v3_0
sandy@ubuntu:~/Downloads/utorrent-server-v3_0$ ./utserver
server started - using locale en_US.UTF-8
Using locale en_US.UTF-8
File not found during integrity check: ./settings.dat
File not found during integrity check: ./settings.dat.new
File not found during integrity check: ./settings.dat.old
File not found during integrity check: ./settings.dat
File not found during integrity check: ./settings.dat.new
File not found during integrity check: ./settings.dat.old
total physical memory -1 max disk cache 33554432
File not found during integrity check: ./dht.dat
File not found during integrity check: ./dht.dat.new
File not found during integrity check: ./dht.dat.old
File not found during integrity check: ./rss.dat
File not found during integrity check: ./rss.dat.new
File not found during integrity check: ./rss.dat.old
File not found during integrity check: ./resume.dat
File not found during integrity check: ./resume.dat.new
File not found during integrity check: ./resume.dat.old
IPv6 is installed


```

---

### Post by trailoryo on 2011-04-29
> **Bucky Ball said:**
> [http://www.utorrent.com/downloads/complete?os=linux](http://www.utorrent.com/downloads/complete?os=linux)

That's the Linux GUI version. Just install it. ;) 

Wine is nigh on impossible to get rid of completely if you ever want to uninstall that, incidentally.


I got that version, but how do you install it? I just "unpacked" it and theres nothing else i can do with it. theres nothing GUIy about it afaics
=(

---

### Post by DanneStrat on 2011-04-29
> **trailoryo said:**
> I got that version, but how do you install it? I just "unpacked" it and theres nothing else i can do with it. theres nothing GUIy about it afaics
=(

No, it's just the daemon that runs in the backgrond(no GUI).

You can still use the webui to connect to the daemon remotely.

Have a look here:

[http://www.utorrent.com/help/faq](http://www.utorrent.com/help/faq)

"Linux users can run µTorrent Server, a command-line version of our client. A GUI version is coming later this year."

Little more info about the linux port of utorrent server:

[http://forum.utorrent.com/viewtopic.php?id=83506](http://forum.utorrent.com/viewtopic.php?id=83506)

---

### Post by doctor82 on 2011-07-27
Download the utorrent linux version to your home directory and rename it to utorrent.tar.gz

Open up a terminal and type:

tar xzf utorrent.tar.gz

To change directory type:

cd utorrent-server-v3_0

Change permissions:

chmod +x utserver

To run type

./utserver

or just click on the file named utserver.

GUI available at [http://yourip:8080/gui](http://yourip:8080/gui) or [http://localhost:8080/gui](http://localhost:8080/gui) from your browser.

Login admin
Password empty

Please mark this thread solved if this solves your problem.

---

### Post by sandy0594 on 2011-07-27
for now i am using utorrent using wine..I will follow your suggestions and post back if there are any queries

---

