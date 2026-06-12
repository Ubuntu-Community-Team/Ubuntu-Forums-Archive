---
title: "Upgrade 6.06 server to 8.04 server"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by wxman on 2008-06-14
I hope this hasn't already been posted, but I've tried all the advice I've found so far.

I have a server, no GUI, that I want to upgrade to 8.04. 
I've now done the following from my terminal connection:
aptitude update
aptitude upgrade
aptitude dist-upgrade
aptitude install update-manager-core
do-release-upgrade

It upgrades to 6.06.2 but not 8.04.

Here's my /etc/apt/sources.list

# Ubuntu supported packages
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb [http://volatile.debian.org/debian-volatile](http://volatile.debian.org/debian-volatile) etch/volatile main contrib non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-proposed main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

Every time I get to do-release-upgrade, it says there are no new releases. Any help? Thanks.

---

### Post by avtolle on 2008-06-14
[http://www.ubuntu.com/getubuntu/upgrading#head-e059d5452a24b50d09c64df48058ef2d834eb197-2](http://www.ubuntu.com/getubuntu/upgrading#head-e059d5452a24b50d09c64df48058ef2d834eb197-2) is the "official word" on how to do the upgrade from 6.06 server to 8.04 server.

From looking at it, you need to enable another repository (dapper-updates, from memory) and install the update manager core with its dependencies, then try the upgrade command it gives from the terminal. HTH.

---

### Post by Pumalite on 2008-06-14
You might want to try this:
sudo sed -i 's/dapper/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

(Make sure you have removed all third parties from your sources.list)

---

### Post by wxman on 2008-06-14
> **Pumalite said:**
> You might want to try this:
sudo sed -i 's/dapper/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

(Make sure you have removed all third parties from your sources.list)

That seems to have done the trick. It's updating right now. I'll let you know if it works.
Thanks much!

---

### Post by Pumalite on 2008-06-14
You are welcome. Good luck.

---

### Post by wxman on 2008-06-14
I guess I spoke too soon. It seemed to be done installing as it dropped to a command prompt. Then the connection seemed to break, and now I have nothing. I just tried to reconnect my SSH terminal, but there's nothing there. I guess I'm going to have to wait till I can be physically in front of the server again on Monday to see if it can be salvaged. I have no ideal what went wrong. It gave no indication of a problem, and now I can't check anything. I guess I should have left it alone.

---

### Post by avtolle on 2008-06-14
What you have encountered can be a by-product of upgrading by changing the sources.list file to reflect the newest version. Doesn't always happen, but when it does..... and, at present, we cannot be sure that is the problem.

I wonder if the SSH "upgrades" done post-release of 8.04 are contributing to your problem. This is just a semi-hypothesis of mine. 

Otherwise, I'm thinking you may well need to d/l an iso of 8.04 server and do a "clean" install of the O/S.

---

### Post by Pumalite on 2008-06-14
The break in the connection was probably the killer.

---

### Post by wxman on 2008-06-14
> **Pumalite said:**
> The break in the connection was probably the killer.

I don't think the connection broke while it was doing the update. it seemed to me like it was done, and dropped to the prompt. Only when I tried to input a command it went dead.



> Otherwise, I'm thinking you may well need to d/l an iso of 8.04 server and do a "clean" install of the O/S. 

I actually have the disk already downloaded and burned. I'm just not near the actual server right now. I hope I can salvage some of the web/DB files if I have to do a reinstall. If not, I do have an fairly recent backup.

---

### Post by avtolle on 2008-06-14
> **wxman said:**
> I don't think the connection broke while it was doing the update. it seemed to me like it was done, and dropped to the prompt. Only when I tried to input a command it went dead.



 

I actually have the disk already downloaded and burned. I'm just not near the actual server right now. I hope I can salvage some of the web/DB files if I have to do a reinstall. If not, I do have an fairly recent backup.
Good luck to you. My semi-hypothesis about SSH in an earlier post was based on my understanding that you believed the update was done, and that you had tried to enter a command via SSH which broke the connection, which you have confirmed. I've no thoughts on how you might work around that, if that was indeed the cause of your problem, but no matter right now; it looks like you're prepared for a clean install, which at this point will likely be the most time-efficient.

---

### Post by wxman on 2008-06-14
I've never had to do a clean install of the server software, after having things running before. Not trying to sound like a complete idiot, but will any of the old installation be saved? I was using ISPConfig, for example, and had a few test sites running. Luckily I wasn't ready to make this my main server yet.

---

### Post by avtolle on 2008-06-14
Don't know the answer to your question. How do you have the server HDD partitioned?

---

### Post by avtolle on 2008-06-14
The last question needs further explication, and I'm going to use my desktop set up as an analogy. I've partitioned my desktop HDD to include, *inter alia*, /, /swap, and /home, to keep my home folder settings and data in a separate partition. When I do a clean install, then, I merely format my / (root) partition, and install the O/S to it, not touching the /home partition. If I didn't have a /home partition, then installing to the /partition would overwrite everything there, data, etc., as is obvious.

Thus, if you have separate partitions for various functions on the server HDD, there is a chance that by merely installing the new O/S to the / partition and not touching the others would not affect the personal settings, etc. If everything on the server HDD is in the / partition, then you would need to try to backup the folders, directories, etc., to external media, reformat and install the O/S, then copy these things back to the HDD. Long winded way to suggest a possible way to do what you want, sorry about that.

---

### Post by wxman on 2008-06-14
I wish I had thought about that kind of a plan for partitioning. I just have the one main partition though, so I don't hold out a lot of hope. This is why it's just a test server for now. I wanted to work out all the bugs, get the best setup, etc. before I did something more permanent.

It will probably be better if I just start from scratch with the server software, and just do a reinstall of all of it. I wouldn't even know where to begin on what directories to backup that could be put back safely. It's going to be a pain getting the Bind name server configuration files back the way I had them. I guess I could try and back them up first. Like I said, this is the first time I have had to do this procedure, so I'm a little lost.

---

### Post by avtolle on 2008-06-14
Since I'm relatively ignorant about server installation, etc., pardon this question if it is particularly naive: Do you have a hard copy of your configuration file information to which you could refer for purposes of the installation? Otherwise, I agree; try to back them up first for use in configuring the new installation.

---

### Post by Pumalite on 2008-06-14
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

---

### Post by wxman on 2008-06-14
> **avtolle said:**
> Since I'm relatively ignorant about server installation, etc., pardon this question if it is particularly naive: Do you have a hard copy of your configuration file information to which you could refer for purposes of the installation? Otherwise, I agree; try to back them up first for use in configuring the new installation.

I actually have a bunch of notes saved. I'm going crazy right now looking for my backed up files. All I can find are ones from months ago, and I know I made one just a little while ago. 

Is it possibly that simple, and is Linux that easy, that I could copy the current directories containing the web, and MySql data files back onto a clean server installation? That would be at least half of my work saved. 

I'm also searching around for a good article on recommended partition setups for Linux servers. i think that does make a lot of sense doing it that way.

---

### Post by avtolle on 2008-06-14
I don't know, but given that Linux "kind of" derives from Unix, which was always and still is a server-type set up, it might be that easy. Don't know if the links Pumallite provided are of any assistance, but you might want to do a bit of reading there as well. Good luck; I've a pending engagement with my spouse that I need to get going to, so will be out of here shortly.

---

### Post by wxman on 2008-06-14
Thanks to you both for your help. It will be a fun Monday.

---

### Post by wxman on 2008-06-16
Well, I got to see the server today by plugging in the monitor, and keyboard. It seems that the new system did install. I turned it on, it booted to command line, and allowed me to log in as root.
It says that the mysql database, Apache server, etc. is all working, but I can't connect to anything from the Internet.
Now I'm faced with the question of reinstalling everything from scratch, doing it correctly this time with partitions. I have one site on the server I was working on that I really wish I could get all back. My problem is I don't have a current backup of the database, and I can't connect to the server to make one. 

It would be great if I could figure out why I lost the ability to connect to the server from the outside.

---

### Post by Pumalite on 2008-06-16
Any specific error message?

---

### Post by wxman on 2008-06-16
As it was booting up I didn't notice anything unusual. Do you mean a certain log file?

It's almost like it changed the IP address on me so it wouldn't let me connect over the Internet.

---

### Post by Pumalite on 2008-06-16
I found this. It might be of help:
[http://ubuntuforums.org/archive/index.php/t-99171.html](http://ubuntuforums.org/archive/index.php/t-99171.html)

---

### Post by avtolle on 2008-06-16
Wondering if this is related to the updates to ssh, about which I posted much earlier. The updates were the result of a major vulnerability, as I recall, and really caused a lot of folks some problems until new keys were generated, etc. Sorry, I don't have any links, but there were a number of threads on the Fora which discussed the problems and proposed solutions. Best I can hope for is that someone who has a link can toss it to you, or that a search of the various forums will pop up useful threads.

EDIT: If this is the cause, there should have been some error messages which appeared, as I recall reading the various threads. If I've misunderstood the problem or misled you, sorry, but the above popped into my mind when reading your latest posts.

---

### Post by avtolle on 2008-06-16
Again, a bit more of an explanation might be warranted, IIRC, about 3 weeks ago or so, there was a problem with the keys being generated under the Debian generator. This affected Ubuntu. There were a bunch of updates during this period (which, given how you upgraded, you likely got the latest ones) which created new blacklists of various keys, etc., given the vulnerability discovered. I noted that you couldn't get to your server via SSH from home, this fact caused me to suggest the vuldnerability problem and the updates that followed. I don't know how you were accessing the internet from the server itself, so for now, I've no further ideas on it. Anyway, you might want to look at the blacklisted keys, etc., to see if this might be a part of your problem. To access from home, I'm certain you will need to generate a new key to do so, as I'm just as certain your old key was blacklisted. HTH.

---

### Post by Pumalite on 2008-06-16
Go to /home>Show Hidden Files>Check .ssh
Edit known_hosts and erase all its contents.

---

### Post by wxman on 2008-06-16
To avtolle:
My server is connected to the Internet from a hardware firewall/router that's connected to a DSL line. I'm using the same DSL line right now on my laptop. The SSH connection was just one I tried. I have three test sites that were running that can't be found. I access my server utilities (ISPConfig) by an HTTPS connection that's not working either. I'm afraid I have never had to deal with blacklisted keys, so i have no idea what to do with them. I'll have to do some searching to learn about them.

To Pumalite:
Right now I'm sitting in front of the server waiting for it to reboot. It's running a "forced check" of the drive because it's been mounted 30 times. As soon as it's done I'll try and find that file and remove it.

---

### Post by avtolle on 2008-06-16
Pumalite's command will remove ssh hosts, so while it will be useful to do so, it doesn't clear up your particular problem as I understand it.  Wish I had something more to offer, other than a general Forum search. Speaking of which, have you looked in the forum Networking and Wireless to see if there might be something there of some use?

EDIT: There is also a forum "Server Platforms" which might (hopefully) have something on point as well.

---

### Post by wxman on 2008-06-16
> **avtolle said:**
> Pumalite's command will remove ssh hosts, so while it will be useful to do so, it doesn't clear up your particular problem as I understand it.  Wish I had something more to offer, other than a general Forum search. Speaking of which, have you looked in the forum Networking and Wireless to see if there might be something there of some use?

EDIT: There is also a forum "Server Platforms" which might (hopefully) have something on point as well.

I'm fairly certain it can't be something wrong with the network before the server. I did nothing to it while I was trying to upgrade the server software. 
The keys could be the problem because that would affect both the SSH terminal and the HTTPS connections. It still doesn't answer what happened to regular HTTP web sites that were there. 
I still wish I could figure a way to backup the mysql database files for the one site I want to salvage. If I could do that, I think it would be worth it to start the whole thing over with the proper partitioning so this won't happen again. I tried to connect a USB external hard drive, but being the doof I am, I forgot that my backup drive is NTFS. It wouldn't mount it.

---

