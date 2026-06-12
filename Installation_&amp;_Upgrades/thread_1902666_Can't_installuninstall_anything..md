---
title: "Can't install/uninstall anything."
date: 2011-12-31
forum: Installation &amp; Upgrades
---

### Post by gmsalomao2 on 2011-12-31
Hello,

I've recently installed meditomb, but I didn't like it so I tried to remove it. But the problem is that it is still running!! I've tried everything to remove it!! apt-get -f install mediatomb, apt-get --purge remove mediatomb...

But the real problem is when I try to install/uninstall other things and I get this error:

```
Processing triggers for man-db ...
Setting up mediatomb-daemon (0.12.1-0ubuntu2) ...
invoke-rc.d: unknown initscript, /etc/init.d/mediatomb not found.
dpkg: error processing mediatomb-daemon (--configure):
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 mediatomb-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by saneearth on 2011-12-31
Not positive, but it may be just the issue of not being able to uniinstall a running process. Open system monitor and kill the process first. Then try the uninstall. Hope this works for you. Just a thought.

---

### Post by Rex Bouwense on 2011-12-31
Did you uninstall mediatomb with Synaptic?  Complete removal should have erased all vestiges of it.

---

### Post by gmsalomao2 on 2011-12-31
I've tried killing the process and to uninstall it with with Synaptic. Didn't work.

Synaptic returns:
```
E: mediatomb-daemon: subprocess installed pre-removal script returned error exit status 100
```

---

### Post by gmsalomao2 on 2012-01-02
Is there any way of manually remove all the files?
I mean.. of course there's, but how to know what files to remove?

---

### Post by Old_Grey_Wolf on 2012-01-02
I tried searching for an answer to your problem. What I have found so far are a lot of bug reports about not being able to completely remove/uninstall MediaTomb. Some of these reports are several years old, and none provide a solution. Maybe you should contact the MediaTomb developers at the email they provide on their website ([http://mediatomb.cc/](http://mediatomb.cc/)), "To contact us via email, write to: contact at mediatomb dot cc".

Although you can get MediaTomb from the Ubuntu Software Center, Canonical doesn't provide support or updates for MediaTomb.

You could try to get you system installing other things again with these commands```
sudo apt-get clean all

sudo apt-get update

sudo apt-get -f install

```

---

### Post by gmsalomao2 on 2012-01-03
> **Old_Gray_Wolf said:**
> 

You could try to get you system installing other things again with these commands```
sudo apt-get clean all

sudo apt-get update

sudo apt-get -f install

```

Well, it didn't work =/
Same error.
About contacting MediaTomb, that's the last thing I wanna do, but maybe I'll have to.

Do you know any way of removing it manually?
Or maybe run Ubuntu only in shell? Without graphical interface?

---

### Post by fdrake on 2012-01-03
```

sudo dpgk --purge -a
sudo dpgk --configure -a 

```

---

### Post by spacecheck on 2012-01-03
Apparently mediatomb daemon starts running with your login. To try to prevent this launch the Sessions Preferences program (System&#8594;Preferences&#8594;Sessions ) and remove it. If lucky, it will not start with the next login and you can uninstall it.

If not, try this, in terminal run
ps aux
to see which is the earliest running mediatomb-related process.
Then run
killall -g -9 processname
which is intended to kill the entire process group
then run
sudo apt-get purge mediatomb

Hopefully, that will kill any running mediatomb process and child processes and let you completely uninstall the program. After that, you could try to run
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
to see if it no longer appears for upgrade.

Good luck!

---

### Post by gmsalomao2 on 2012-01-03
> **spacecheck said:**
> Apparently mediatomb daemon starts running with your login. To try to prevent this launch the Sessions Preferences program (System&#8594;Preferences&#8594;Sessions ) and remove it. If lucky, it will not start with the next login and you can uninstall it.

If not, try this, in terminal run
ps aux
to see which is the earliest running mediatomb-related process.
Then run
killall -g -9 processname
which is intended to kill the entire process group
then run
sudo apt-get purge mediatomb

Hopefully, that will kill any running mediatomb process and child processes and let you completely uninstall the program. After that, you could try to run
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
to see if it no longer appears for upgrade.

Good luck!

MediaTomb is not listed on the Startup Manager (Sessions in older versions).
So I tried to find any mediatomb related process with the *ps aux* command, but I couldn't. What the hell is happening with this mediatomb?!! It's driving me crazy!

Is there any way of starting up Ubuntu into a 'secure' mode? Just like Window$ when you don't want any process to startup?

---

### Post by gmsalomao2 on 2012-01-03
> **fdrake said:**
> ```

sudo dpgk --purge -a
sudo dpgk --configure -a 

```
Doesn't work.

---

### Post by spacecheck on 2012-01-03
WHen you boot the system, Grub may list an additional recovery version, which you can scroll down to to stop the timer from running the default system.

---

### Post by gmsalomao2 on 2012-01-04
> **spacecheck said:**
> WHen you boot the system, Grub may list an additional recovery version, which you can scroll down to to stop the timer from running the default system.
Yeah, but what can I do from the recovery version?
It just loads the system normally.

---

### Post by spacecheck on 2012-01-04
Ah, good question. I was thinking  you would probably end up at a terminal prompt, before the offending daemon had been started. If that isn't the case, then perhaps you could examine which processes are started and at which run level, then rename the process as instructed in the related readme for the respective runlevel.

As sysad, you will probably be familiar with run levels an init processes. If not, a general tutorial is here:

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

If you find the offending mediatomb-daemon process is started at runlevel 5, for example, you could sudo to init 3, (network without GUI and any runlevel 5 processes) and try to sudo apt-get purge mediatomb from there, so mediatomb couldn't defend itself, having not been started.

IF that were not successful, or if mediatomb is started at an earlier level, then you could follow the instructions to rename the process and  "run 'update-rc.d script defaults'", after which the process should no longer be run on system start. Then you could again try the apt-get commands to eradicate mediatomb, without getting the error message you posted earlier.

Good Luck!

---

### Post by Old_Grey_Wolf on 2012-01-04
Try removing the directory opt/mediatomb if it exists. You will need to use the "rm [OPTION]... FILE..." command with the appropriate "/path/to/directory".

Then try the other clean, purge, etc., commands in previous posts.

If you succeed in removing MediaTomb this way, write down exactly what you did and post it.

Good luck!

---

### Post by gmsalomao2 on 2012-01-04
> **Old_Gray_Wolf said:**
> Try removing the directory opt/mediatomb if it exists. You will need to use the "rm [OPTION]... FILE..." command with the appropriate "/path/to/directory".

Then try the other clean, purge, etc., commands in previous posts.

If you succeed in removing MediaTomb this way, write down exactly what you did and post it.

Good luck!

There was no opt/mediatomb. So I removed  EVERY file with meditomb on the name.
I've looked into every folder of my computer. EVERYONE.

Restarted the computer, ran *apt-get autoclean, dpkg --configure -a* and guess what?
DIDN'T WORK x.x

---

### Post by ottosykora on 2012-01-05
just some try:

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

scroll in the presented table with up down arrow keys and look of the program is listed there. If yes, then remove any x with the space bar.

Reboot and see now if you can remove all.

---

### Post by Old_Grey_Wolf on 2012-01-05
You have tried for 5 days to solve this. I refer back to my previous post #6 [http://ubuntuforums.org/showpost.php?p=11582119&postcount=6](http://ubuntuforums.org/showpost.php?p=11582119&postcount=6).

If the remnants of MediaTomb are not preventing you from updating or installing other software then ignore the errors. 

If it is preventing you from updating or installing other software then contact the MediaTomb developers, or re-install your OS.

---

### Post by gmsalomao2 on 2012-01-08
PROBLEM SOLVED!!!

Here's exactly what I did:

```
~$ sudo nautilus ../../../../
```
Which means I opened nautilus in the root of the HD.

-Then I did a search for ''mediatomb" and deleted ALL the files in the result. ALL of them.

-Restarted the computer.
```

~$ sudo apt-get update
~$ sudo dpkg --configure -a
~$ sudo apt-get autoclean
~$ sudo apt-get autoremove
~$ sudo apt-get update
```Done! =D

---

### Post by gmsalomao2 on 2012-01-08
Thanks for all the help guys!

---

### Post by jeff_ro on 2012-01-20
I had a very similar problem and have been searching for this thread for ages. Was pulling my hair out. Cheers!

---

### Post by bwinfrey on 2012-08-14
I had this problem trying to remove mediatomb as well.  I saw the line ```
Removing mediatomb-daemon ...
invoke-rc.d: unknown initscript, /etc/init.d/mediatomb not found.
dpkg: error processing mediatomb-daemon (--remove):
 subprocess installed pre-removal script returned error exit status 100

``` in the output, so I tryed this ```
sudo touch /etc/init.d/mediatomb
``` and the removal completed successfully.

---

### Post by alkobottle on 2012-10-16
> **bwinfrey said:**
> I had this problem trying to remove mediatomb as well.  I saw the line ```
Removing mediatomb-daemon ...
invoke-rc.d: unknown initscript, /etc/init.d/mediatomb not found.
dpkg: error processing mediatomb-daemon (--remove):
 subprocess installed pre-removal script returned error exit status 100

``` in the output, so I tried this ```
sudo touch /etc/init.d/mediatomb
``` and the removal completed successfully.

thank you so much! I have been searching a while for a solution!
I think it was my fault that the init script was removed, didn't think a simple, empty file would do the trick.
Is it intended behaviour of apt-get that it stops the remove / purge process, just because one file is missing? this is quite irritating...

---

