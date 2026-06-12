---
title: "Can't install/run Cacaoweb.linux"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by shadowofblood on 2010-11-19
Running Ubuntu 10.10

I set the permissions on cacaoweb.linux to allow executing as a program.

When I use the command:
```
/home/user/cacaoweb.linux &
```I get an error saying:
> [1] 3478
user@ubuntu:~$ bash: /home/user/cacaoweb.linux: No such file or directory

[1]+  Exit 127                /home/user/cacaoweb.linux
However, the file is there and the name is correct.  Any ideas?

UPDATE: When running the command with "Sudo", I get the following:
> sudo /home/user/cacaoweb.linux &
[1] 6308What does that mean?

---

### Post by Alan McNea on 2010-12-14
Make sure you downloaded the right version.  If you have a 64 bit OS download cacaoweb.linux64

---

### Post by lostsoul2001 on 2011-01-13
hi can you explain to a noob how to install because i just get choose app to launch

---

### Post by Cheezespread on 2011-01-13
> sudo /home/user/cacaoweb.linux &
[1] 6308 

That means that the process is running in the background ( due to the & )and pid for the process is 6308 .

To run cacaoweb in linux , make it an executable by change the permissions on the file.

Assuming you are in the directory where you have saved the file.

Fire up the terminal.

Make the saved file an executable
```
chmod +x cacaoweb.linux
```

Run it 
```
./cacaoweb.linux
```

Type in  [http://127.0.0.1:4001/index.html](http://127.0.0.1:4001/index.html) in your browser and you should see th cacaoweb interface.

---

