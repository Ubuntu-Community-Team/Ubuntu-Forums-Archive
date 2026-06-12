---
title: "where to start reading boot scripts"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2008-12-01
I'm an olde RedHat guy new to ubuntu-family under Hardy v8.0.4. [Glad I made the change.] I'd like to read the boot scripts and cannot find how to do that. I believe that hardy uses something called 'upstart.'

I have the upstart docs, but what I read does not seem to match what I find installed. Can someone point out the first few bricks on this yellow brick road??

~~~ Saint 0;-D

---

### Post by Diabolis on 2008-12-01
Do you mean the services that are loaded when Ubuntu boots? All of them are in **/etc/init.d/** And they are called depending on the run level that you want to use. The run levels, instead of being defined by a script, are defined by a folder **/etc/rcX.d/** where **X** is the number of the run level.

---

### Post by SaintDanBert on 2008-12-02
I know about all of those scripts. What I don't find is a description of how things get started. BIOS loads files from /boot ... X,Y,Z happen ... script xxxxx runs first ... that script loads yyyyy, and so on.

Where is the default runlevel stored? My reading talks about /etc/inittab, but that does not exists by default 
any longer.

I know that Kxx scripts run in ascending number order followed by Sxx scripts in ascending number order.

Am I correct about using the 'upstart' package? What I find on my install does not match what I read from the package docs.

I know that something runs as an initial process and that 
other things proceed from there. 

Stumpled,
~~~ Saint 0;-D

---

### Post by Diabolis on 2008-12-02
Yeah, Ubuntu uses Upstart. I would start by reading [its original specification]("http://upstart.ubuntu.com/misc/upstart.pdf").

The default runlevel in Ubuntu is the number 2. You can check it with the **runlevel** command.

To find out which scripts are loaded first and which other files they call etc, I would start with the bootloader, which is GRUB by default in Ubuntu. Maybe this will be helpful: [http://ubuntuforums.org/showthread.php?p=4723298#post4723298](http://ubuntuforums.org/showthread.php?p=4723298#post4723298)
That thread has a link to a great post in Fedora forums: [http://forums.fedoraforum.org/showthread.php?t=153679](http://forums.fedoraforum.org/showthread.php?t=153679)

I am also interested in finding a detailed "map" of how things happen when the machine boots, I just haven't spend enough time on that.

---

