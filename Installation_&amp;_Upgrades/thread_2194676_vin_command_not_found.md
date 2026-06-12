---
title: "vin: command not found"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by Richardc0077 on 2013-12-19
Hi All

have just installed ubuntu 12.04.3 on a HP ML350 g5 server and have watching a video on the install procedure and when we got to the part to setup the network. The instructions are as follows
sudo vin /ect/network/interfaces. press enter

i get a message that vin: command not found.

what have i done wrong

Any help would be very greatfull

Many thanks

Richard C

---

### Post by tfrue on 2013-12-20
I believe the video meant to say "vim". VIM is a text editor that will allow you to change the /etc/network/interfaces config file so you can configure your network using DHCP, I believe. Just type:
```
sudo vim /etc/network/interfaces
```
Good luck!

---

### Post by Richardc0077 on 2013-12-20
Thanks for that . now editing but when i press escape then shift z twice i get** E212 can't open file for writing**
the files i am trying to write to are _sudo vim /ect/network/interfaces_ and _sudo vim /ect/init.d/networking restart_. I then get [B]command not found

start to think i have a bad download of 12.04[/B]

---

### Post by tfrue on 2013-12-20
Try giving this a read:
[http://www.linuxquestions.org/questions/linux-newbie-8/e212-cant-open-file-for-writing-i-have-root-access-4175431271/](http://www.linuxquestions.org/questions/linux-newbie-8/e212-cant-open-file-for-writing-i-have-root-access-4175431271/)

---

### Post by Richardc0077 on 2013-12-21
Hi Chris

i have read and tried the commands but it come back with no such file or directory. i tried _ls -l ect_. then _/ect_ then _sudo chmod u+w /ect/networking/interfaces_ but the system comes back with **cannot access '/ect/network/interfaces' no such file or directory.**

---

### Post by tfrue on 2013-12-21
I was re-reading over your post from earlier, and I noticed that you tried to edit a file on the /init.d/ directory. The /etc/init.d/ directory holds the services for the daemons and other services. So you shouldn't have to edit a file in there, though you may need to restart the networking service by typing.
```
sudo /etc/init.d/networking restart
```

Also, it might be important to note that if you haven't updated your server since install, you may not have the command 'vim' installed, rather, 'vi' which is basically the same thing. We won't go in to details about the differences. So copy and paste:
```
sudo vi /etc/network/interfaces
```

I would greatly appreciate if you would copy and paste these commands into your terminal session and post the output.
```
dmesg | grep eth
```
```
ifconfig -a
```
```
cat /etc/network/interfaces
```

Thanks,
Chris

---

### Post by Richardc0077 on 2013-12-21
hi all 
please disregard last post made a type

---

### Post by tfrue on 2013-12-22
Any luck so far?

---

### Post by Richardc0077 on 2013-12-23
Hi

Yep typing the commands correctly in a major component of getting things right and to run properly.

Now for the next question. How do you install software or look for a file on this system

Many thanks

Richard C

---

### Post by tfrue on 2013-12-23
Since you're using Ubuntu, the command that is genereally used to install software is 'apt-get.' Say we want to download 'vim' to replace 'vi', we need root priveleges when installing, so we type:
```
sudo apt-get install vim
```
That's it! It will try and download the repositories, and depencies from the appropriate repositories online. There are many things you can do rather than installing packages, like removing or cleaning installations.

Here is the online man page for [apt-get]("http://linux.die.net/man/8/apt-get")

There are serveral ways to find files on your hard drive. 'Find' will search for files on the hard drive, while 'Grep' will search for words, patterns really, in files. An example of each would be:
```
chris@tfrue:~$sudo find /etc -name interfaces
/etc/network/interfaces #The output of the command
chris@tfrue:~$ 
```

Here is the online man page for [find]("http://linux.die.net/man/1/find")

So what we typed was "find" to state we wanted to find something, then "/etc" to say the file will be within the folder and subfolders of /etc, the "-name" to say find the name of a file, then "interfaces" which is the name of a file we are looking for.

Now lets say you know that you want to look at the /etc/hosts file, but instead of using "cat", we can use grep to single out words or patterns that we are looking for. So we begin by typing:
```
chris@tfrue:/$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    tfrue

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

chris@tfrue:/$ grep tfrue /etc/hosts
127.0.1.1    tfrue
chris@tfrue:/$ 
```

Here is the online man page for [URL="http://linux.die.net/man/1/grep"]grep
[/URL]
I used "cat" to show you the output of the /etc/hosts file, then how to use "grep" to search for the pattern 'tfrue' within the /etc/hosts file.

I also want to introduce you into a command that will give you info about any other command. If you want more information on how to use lets say grep, you would type:
```
man grep
```

Which would bring up the MANual page for grep. Neat huh.

Chris

---

### Post by Richardc0077 on 2013-12-24
Hi All thanks for all that great stuff. I am learning a lot.

now i have a question about directories. i need to load some files in to htdoc folder but would need to setup some folders in the directory. Eg; htdoc/tickets/sp in one the other one is htdoc/ticketsmdb. and then load the files into these directories. also having read a post from opensource should i first load xampp for Linux first the get the MySQL, php, and Apache update first 
Would i right in the following command  mkdir/var/www/tickets/sp as a answer to my first question then mkdir /var/www/ticketsmdb 

many thanks

Richard C

---

