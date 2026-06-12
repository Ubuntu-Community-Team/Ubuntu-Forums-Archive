---
title: "partition scheme - initial install, ubuntu only"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by aBitLater on 2008-02-01
Hi, 
I'm installing from the live cd for 7.10 Gutsy

I've done a little research and decided that I'd like this partition scheme, based on information found here [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-December/002658.html]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-December/002658.html"):

I have a 93 GB Hard Drive on HP Pavillion dv8000 with 2GB ram.  I will also be installing MySQL, PostGreSQL, APACHE2, and related web software with a full development environment (C, C++, etc).  I intend to use Gnome only (at present)

/ boot         512 MB
/    (root)    18 GB
/ swap       2 GB
/var/log      4GB
/spare       10GB (for future use, testing other distro's etc)
/home       All Remaining Space 59GB

I'd like to know what you think about that, but more importantly, since I am SUCH a NEWB, can you tell me - all I have to do is use GParted to make these partitions, and label them, the install will write to them properly ???  Is there anything else I should do, for example, are there any special flags that need to be set for the boot partition? (read only)

I am not sure where all my development apps will end up, that's why I made root 18GB.  And I didn't want /home or /var/logs to bring the system to a halt in case of filling up.

Thanks in advance for all input!

---

### Post by zvacet on 2008-02-01
Ubuntu can do partitioning for you if you select manual way and then make your partitions as you wish.

---

### Post by scorp123 on 2008-02-01
> **aBitLater said:**
>  / boot         512 MB  Way too big. You rarely ever need more than 30 - 40 MB here. A partition size between 100 - 150 MB is sufficient here. Unless you are a kernel developer and plan to experiment with tons of various kernels at the same time?

> **aBitLater said:**
>  /    (root)    18 GB  I personally would take this apart (e.g. I have a separate **/usr** partition here of ~6 GB size), e.g. I always separate partitions with lots of write accesses from those with lots of read accesses. This helps to fragmentation low (as should be usual on Linux!) and performance up. But OK ... it's not too bad.

> **aBitLater said:**
>  swap       2 GB  You're using this on a laptop? Swap should always at least be the equal size of RAM or else you will run into trouble when you try to go into standby or hibernation. So if you have 2 GB RAM and your swap is pretty much exactly 2 GB too this should be OK. Make it 2.5 GB just to be safe and I am happy ;)

> **aBitLater said:**
>  /var/log      4GB  You most certainly meant **/var** ..... Having only **/var/log** on a separate partition makes little sense here. 4 GB for **/var** is enough. If you really plan on doing tons of web development I'd make it even bigger for all the web stuff ends up in **/var/www** and this too can take a lot of space then. But this is configurable ... I know people who move their web stuff to other locations so **/var** doesn't see much use except for logs. For a normal desktop system 4 GB for **/var** is more than enough. (mine is 2 GB here).

> **aBitLater said:**
>  /spare       10GB (for future use, testing other distro's etc)  Nice :)

> **aBitLater said:**
>  /home       All Remaining Space 59GB OK.

Hmmm ... this is the output from my well-used "workstation" laptop, e.g. I use this thing every day on my job to do some heavy duty work for me. Here is how my partitions look like (this is a 80 GB disk):
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             1.9G  379M  1.4G  22% /
/dev/sda1             122M   39M   77M  34% /boot
/dev/sda8              63G   29G   31G  48% /home
/dev/sda6             5.5G  3.8G  1.5G  72% /usr
/dev/sda7             1.9G  417M  1.4G  24% /var
```

Maybe this helps you and gives you some ideas?

---

### Post by aBitLater on 2008-02-01
scorp123,

thank you very much for your thorough analyses and comments.

> **scorp123 said:**
> Way too big. You rarely ever need more than 30 - 40 MB here. A partition size between 100 - 150 MB is sufficient here. Unless you are a kernel developer and plan to experiment with tons of various kernels at the same time?


on my desktop machine, which has ubuntu already installed, there are about 4 boot images - 2 are recovery boots (if memory serves me)

> **scorp123 said:**
> 
 I personally would take this apart (e.g. I have a separate **/usr** partition here of ~6 GB size), e.g. I always separate partitions with lots of write accesses from those with lots of read accesses. This helps to fragmentation low (as should be usual on Linux!) and performance up. But OK ... it's not too bad.


Thanks for that input... I'm a real newb and I don't even know what the /usr directory is for.  Been using ubuntu for a month (on desktop) and am still getting used to "where everything is".
I did notice that your workstation /usr directory is at 72% of 5.5GB.  So what is this directory for?

> **scorp123 said:**
>  You most certainly meant **/var** ..... Having only **/var/log** on a separate partition makes little sense here. 4 GB for **/var** is enough. If you really plan on doing tons of web development I'd make it even bigger for all the web stuff ends up in **/var/www** and this too can take a lot of space then. But this is configurable ... I know people who move their web stuff to other locations so **/var** doesn't see much use except for logs. For a normal desktop system 4 GB for **/var** is more than enough. (mine is 2 GB here).


The intent here was to keep runaway logs from bringing the system down.  I'll be testing different database, apache2, php, etc as I learn about these apps and programming in general.  I tend to "overinstall"... so knowing that, would you still recommend 4GB on a separate partition /var ? (and not a separate partition for /var/log)
[/quote]

> **scorp123 said:**
> 
Hmmm ... this is the output from my well-used "workstation" laptop, e.g. I use this thing every day on my job to do some heavy duty work for me. Here is how my partitions look like (this is a 80 GB disk):
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             1.9G  379M  1.4G  22% /
/dev/sda1             122M   39M   77M  34% /boot
/dev/sda8              63G   29G   31G  48% /home
/dev/sda6             5.5G  3.8G  1.5G  72% /usr
/dev/sda7             1.9G  417M  1.4G  24% /var
```


> **scorp123 said:**
> 
Maybe this helps you and gives you some ideas?
yes, very much :)

---

### Post by aBitLater on 2008-02-01
also, I wanted to add that i will be using vmware or virtual box for winxp software, MS Visual Studio and SQL Server.  i assume the virtual os will just go in my /~ directory as one big file?  Or, should I make a separate partition for just that?

---

### Post by aBitLater on 2008-02-01
uh-oh,,, the /var on my desktop ubuntu is 13.5 GB.

#:- |

I guess I need to figure out what's going on there to make it so big.

---

### Post by scorp123 on 2008-02-01
> **aBitLater said:**
>   I did notice that your workstation /usr directory is at 72% of 5.5GB.  So what is this directory for? Wikipedia has all the answers ... it's written far better and in more details than I could ever do that:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Quote from there: 
" ... **[COLOR="Blue"]/usr :** Secondary hierarchy for user data; contains the majority of (multi-)user utilities and applications ... [/COLOR]"  
Yup, that's pretty much what I'd say when I would have to explain it in one sentence. In other words: Whatever you install, if it's something "user process" related == something a human sitting in front of the computer would use (as opposed to something the system has to use) then it ends up on **/usr** .... 

- Binaries go to **/usr/bin** ....
- Libraries go to **/usr/lib** ...
- Shared stuff goes to **/usr/share** ...
- e.g. pre-installed wallpapers are in **/usr/share/wallpapers** ...
- pre-installed sound files are in **/usr/share/sounds** ..
- icons? They are in **/usr/share/icons** ...
- tons of others are in **/usr/share/pixmaps** ...
- want some documentation? **/usr/share/doc** has it all ...
- need to recompile the kernel? If the sources are installed you will find them in **/usr/src** ...

And there is tons and tons more stuff. As you can see **/usr** is a pretty busy place :)

> **aBitLater said:**
>  The intent here was to keep runaway logs from bringing the system down.  **/var** doesn't only contain logs ... e.g. **/var/cache** contains all the various cache directories certain applications need to keep in order to function properly. And **/var/spool** has all the various queues and spool directories other programs need to keep on the system. e.g. the printing system "CUPS" uses **/var/spool/cups** to store its print jobs .... **/var/www** would be where Apache keeps its web pages per default. Depending on how you configure this and what stuff you put on your web server there could be tons of stuff too all of a sudden.

Trust me ... you don't want *any* of the stuff in **/var** to bring your system down, so you need not just worry about the logs, you will have to worry about all the other stuff in there as well. Logs are not such a big issue. Just remember to do some clean-up from time to time, e.g.
```
cd /var/log
sudo rm -i *.gz

```
Explanation: Old logs get automagically packed into GNU-zip archives from time to time. So the above command jumps into the right directory and will delete them. The "-i" switch will ask you every time for a confirmation before actually deleting anything.

> **aBitLater said:**
>   I'll be testing different database, apache2, php, etc as I learn about these apps and programming in general.  I tend to "overinstall"... so knowing that, would you still recommend 4GB on a separate partition /var ?  OK, make it 15 GB or even more, just to be on the really really safe side ...

> **aBitLater said:**
>  I will be using vmware ...  VMware Server? That one per default also tries to install its virtual machines into **/var** - more precisely: 
**/var/lib/vmware-server/Virtual Machines/**

... But it's relatively easy to tell it to use your **/home** directory instead, just point the file dialogues to your **/home** directory when you create a new virtual machine. For the virtual machine it's not so important, it won't know where it physically resides on your PC :)

---

### Post by scorp123 on 2008-02-01
> **aBitLater said:**
>  I guess I need to figure out what's going on there to make it so big. **Applications > Accessories > Disk Usage Analyzer** ... Open that one and then have it analyse **/var** for you. You will soon find out what's eating all that disk space.

---

### Post by aBitLater on 2008-02-03
hehe, that turned out to be mythtv recordings

---

### Post by scorp123 on 2008-02-03
> **aBitLater said:**
> hehe, that turned out to be mythtv recordings It puts that stuff into **/var** ??? :confused:  I am shocked. Such stuff should belong into the /home folder ...

---

