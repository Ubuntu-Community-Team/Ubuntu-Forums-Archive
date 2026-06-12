---
title: "installing yacy has stopped update and upgrade abillity"
date: 2012-01-08
forum: Installation &amp; Upgrades
---

### Post by clearwood on 2012-01-08
Can anyone help me out here?

I started installing yacy by adding their souce repo to my list:

deb [http://debian.yacy.net](http://debian.yacy.net) ./

 and using apt-get:

apt-get update
apt-get install yacy

and since then the program doesnot function but what si worse is that I cant update or partial upgrade. the system suggests that I use:

sudo dpkg --configure -a

Then what happens is that I am stuck with a message 'setting up yacy' (translated from danish) forever.

I have tried using synaptics as well removing it but it seems that it doesnot get to activate the apply button. 

Best regards

---

### Post by jerrrys on 2012-01-10
I do not use it, but looks like to me that the tar.gz package would be a better route to go.  As for no updates; removing yacy from your sources list should fix that.

---

### Post by drawkward on 2012-01-11
I am getting this too. I started to install Yacy and it froze on a line where it said it was creating a folder, the location of which I now forget. I shut down my pc later that day and since then starting Ubuntu Software Centre hangs on 'progress'. I just ran 'dpkg --configure -a'. It replied "Setting up yacy (1.01.9104) ..." but is now hanging.  I think Synaptic also hangs.

I cannot install any other software as it just queues up the installation behind Yacy.  I also tried uninstalling Yacy through the Software Centre but it also hung.

I'm running the latest Ubuntu on Gnome Shell. Happy to give other info and I'd be really appreciated if anyone could help. It's not a problem right now but I'll need to install another program sooner or later.

Many thanks,

Jake

---

### Post by clearwood on 2012-01-11
I'm using 11.10 I've removed it from the list. Still same problem. And thanx for replies. Kind Regards

---

### Post by jerrrys on 2012-01-11
Is apt-get update giving you any hints (errors)?

---

### Post by amnesic on 2012-01-11
Just for info, I Have the same trouble here. 
No special error detected, only infinite Hanging at Setting up yacy (1.01.9139) ...

(under 10.04 LTS)

---

### Post by clearwood on 2012-01-11
Tried sudo apt-get update and got the message, translated from danish:

'couldn't unlock /var/lib/dpkg/lock - open (11: Resource temporary unavailable)'

and:

'couldn't unlock administrationsdirectory (/var/lib/dpkg/), is another process using it?'

Best regards

---

### Post by jerrrys on 2012-01-11
Found this at the yacy forum.

[ATTACH]210658[/ATTACH]

There are three of you now with yacy related problems.  I wonder if you should not search and post in that forum.

[http://www.yacy-forum.org/viewforum.php?f=2&sid=bce59a0a4d503bdf2bba1ed8b7523003](http://www.yacy-forum.org/viewforum.php?f=2&sid=bce59a0a4d503bdf2bba1ed8b7523003)

---

### Post by Nuafite on 2012-01-11
I have same or similar problem, having tried to install yacy from terminal.
Jerrys is right: the tar.gz package is the better way. I installed it without a problem, and thought all was well until I tried to install another program via terminal. It refused to install the second program and tried to complete the original yacy install but hung as before. One odd side effect is that I now can't use youtube etc. 

I tried deleting the yacy deb line from  /etc/apt/sources.list to no avail. In fact I've tried several solutions I found on the web to no avail. 

When I originally tried 

ps ax | grep dpkg

I got this

MyNotebook-PC:~$ ps ax | grep dpkg
 2614 pts/1    Ss+    0:00 /usr/bin/dpkg --status-fd 53 --configure man-db yacy compiz-plugins ubuntu-tweak-0
 2637 pts/1    S+     0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/yacy.postinst configure 
 2658 pts/1    S+     0:00 /bin/sh /var/lib/dpkg/info/yacy.postinst configure 
 2866 pts/2    S+     0:00 grep --color=auto dpkg


Now I get a single line
2419 pts/1    S+     0:00 grep --color=auto dpkg

When I originally tried 
sudo rm /var/lib/dpkg/lock

rm: cannot remove `/var/lib/dpkg/lock': No such file or directory

Notebook-PC:~$ sudo dpkg --configure -a
Setting up compiz-plugins (1:0.9.6+bzr20110929-0ubuntu6) ...
Setting up yacy (1.01.9108) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing yacy (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ubuntu-tweak-0 (0.5.15-0~20111023~oneiric1) ...
Processing triggers for python-central ...
Errors were encountered while processing:
 yacy

When I originally tried

sudo dpkg --configure -a

I got this

Notebook-PC:~$ sudo rm /var/lib/dpkg/lock
rm: cannot remove `/var/lib/dpkg/lock': No such file or directory
Notebook-PC:~$ sudo dpkg --configure -a
Setting up compiz-plugins (1:0.9.6+bzr20110929-0ubuntu6) ...
Setting up yacy (1.01.9108) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing yacy (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up ubuntu-tweak-0 (0.5.15-0~20111023~oneiric1) ...
Processing triggers for python-central ...
Errors were encountered while processing:
 yacy
Notebook-PC:~$ 

I've just tried it again and it attempted to install yacy but hangs again.

This is the output: 

Notebook-PC:~$ sudo dpkg --configure -a
[sudo] password for MyNotebook: 
Setting up yacy (1.01.9108) ...
debconf: Warning: Possible database corruption; will attempt to repair by adding back missing question yacy/peername.
debconf: Warning: Possible database corruption; will attempt to repair by adding back missing question yacy/network.
debconf: Warning: Possible database corruption; will attempt to repair by adding back missing question yacy/network-url.
debconf: Warning: Possible database corruption; will attempt to repair by adding back missing question yacy/memory-start.
debconf: Warning: Possible database corruption; will attempt to repair by adding back missing question yacy/memory-max.

I should say that in my attempts to solve it I deleted the installation from the tar.gz package

I really liked what I saw of yacy and might go back to it if this problem can be solved. 

Thanks in advance for any help. (I see smileys appearing in the preview - don't know what that's about!)

---

### Post by koanhead on 2012-01-12
Hi folks, the screenshot that jerrys posted shows my reply to this post:
[http://www.yacy-forum.org/viewtopic.php?f=2&t=625](http://www.yacy-forum.org/viewtopic.php?f=2&t=625)

Unfortunately the tarball only worked for a while and then started giving me problems. Still, the .deb has yet to install, so I guess that's progress?

I found that YaCy can't be stopped using the scripts in its install directory (I had installed it as a regular user, in /home/koanhead) and it can't be directly killed- the only way to stop it is to kill the java process. YMMV but I'm afraid it just doesn't work well with Ubuntu. I'm still bashing away at it, and if I get things working I will post here.

---

### Post by drawkward on 2012-01-12
I had a look at the yacy forum link above and it suggested running  "sudo dpkg -r yacy". This worked for me in so far as it removed yacy from my machine. 

This has solved it for me personally as I don't feel like trying to install yacy again.

Many thanks to all who took the time to reply, much appreciated.

---

### Post by clearwood on 2012-01-12
I will certainly search that other forum.  Still think that I should be able to find something here, that enables me to remove the right files so that my little experiment with yacy doesn't interfere with the rest of my 11.10 system. 

I will try to contribute myself as much as possible.

I allso strongly sympathize with the yacy-project( 'tho I need my system fixed).

As a search machine that in effect is relatively free (for instance from the two unions (us and eu) us and their patriot act and its opposing regulations from eu)

best regards

---

### Post by Nuafite on 2012-01-12
Many thanks, drawkward
> sudo dpkg -r yacy
got rid of yacy and I can now install new software via terminal. 

I'm still having problem with youtube videos - some work, most don't - but I presume that's a separate issue.
Update on youtube problem: clearing the Firefox cache of youtube cookies appears to have done the trick.

---

### Post by clearwood on 2012-01-12
yep did it for me to. thanx

---

### Post by jerrard on 2012-01-14
Hi All,

Please make me the fourth person with the same problem.

When someone more smarter than me fixes this, can you please post the answer here?

Cheers!

---

### Post by jerrard on 2012-01-21
Hi forum,

i have uninstantiated this through the command line and all is now working!

Cheers all!

---

