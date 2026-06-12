---
title: "How do I make my install generic so it boots..."
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by ericnord on 2007-06-29
Hey everyone,

I have Ubuntu 7.04 installed on an external USB drive. Grub is installed on the external drive as well so it only asks me to boot Ubuntu when I have it connected to the computer. If I want to make this a truly portable OS I need to have some generic config files. For example, I plugged the external drive into another laptop and it errors out because of the different graphics card. Can someone give me some advice on how to make a generic version and of which files I would need to edit. I'm assuming there is something I can copy from the Live CD since it is computer agnostic.

I've read about portable OSes being sold on thumbdrives, so I know it is possible, I'm just a noob.

Thanks

---

### Post by kidders on 2007-06-30
Hi there,

My approach would be to make your Linux reasonably hardware-specific, rather than too generic. After all, portable OS installs are inevitably slow, so you might as well make *some* attempt to optimise yours to the hardware it's running on.

Taking graphics cards as an example (since you mentioned them), it shouldn't be too tricky to find an Nvidia-specific xorg.conf that works reasonably well with all Nvidia cards. The same should apply to ATI, or any other card manufacturers you have to deal with. The alternative (ie using completely generic display drivers) would probably prove intolerably laggy, and very CPU-intensive. There are basically two approaches...

[B]I - Complicated
[/B]You want to try to set up an OS that will work on any arbitrary machine, on the fly, with minimal configuration.

[B]II - Easy
[/B]You have a number of computers, all of which you'd like to run your Ubuntu on ... but you could make a list of them, if you needed to.

The idea would be to try to find ways of distinguishing one computer from another. Doing things the "Easy" way makes this very straightforward. You could, for instance, decide that the Ethernet address of a computer's primary NIC will be used to determine what sorts of hardware configurations to load. Once you'd taught your OS how to work a computer once, it would be able to recognise it the next time around. The "Complicated" way would involve performing lots of individual hardware detection operations (rather than just one), and configuring everything appropriately.

Anyhow, I suppose the question is which approach would you prefer?[LIST=1]
[*]Totally generic.
[*]Capable of recognising computers your OS has seen before.
[*]Able to arbitrarily reconfigure itself on the fly.[/LIST]I'd be happy to offer you advice on _any_ approach, but I wanted to mention some additional choices, rather than simply going ahead and describing generic configurations.

---

### Post by ericnord on 2007-07-01
Thanks Kidders for the reply,

I agree that your 'easy' approach would be a preferred method since there are only a few systems I will be using my external drive with. How do I 'train' my OS which hardware to boot depending which computer it is booting from?

thanks for any help w/ this

---

### Post by ericnord on 2007-07-02
Also, I was thinking that the LiveCD must have some sort of generic config files, so could I do something similar for when I'm not on my usual machine? I understand the graphics will not be 100% w/ the generic version, but I will still be able to surf web, watch movies, etc....at least I think.

Let me know any thoughts you have,
Thanks

---

### Post by kidders on 2007-07-02
Hey again,

Here's roughly what I was thinking about ... hopefully you'll like the idea ...

**I - Identify your boxes**

Try to come up with a command (or a sequence of commands) that can uniquely identify each of your boxes ... or at least identify them uniquely *enough *for your purposes. For instance, the name of the machine's graphics card manufacturer (which would allow you to configure X properly) might be enough. On the other hand, you might want to be able to rewrite network configurations, mouse/keyboard settings, and so on, in which case you'd need to be able to properly identify each individual machine.

[COLOR=Blue]Two examples:[/COLOR]

This should spit out the MAC address of eth0, which would be a perfectly good "label" for a machine.```
$ ifconfig eth0 | grep HWaddr | sed 's/^.*HWaddr\s\([0-9A-F:]*\)\s*$/\1/'
00:0F:EE:53:68:41
```Here's another example. The first command identifies the PCI slot your graphics card is connected to, so the second can use it to identify who made it. "0x10de" is the manufacturer code for Nvidia.```
$ lspci | grep -i vga | cut -d" " -f1
02:00.0
$ cat "/sys/bus/pci/devices/0000:02:00.0/vendor"
0x10de
```**II - Create some configuration repositories**

Anyhow, let's assume you've made something similar to the above, so you can calculate a sort of label for each of your computers. Using my Nvidia graphics card as an example, you could ...```
sudo mkdir -p /opt/hwprofiles/0x10de
```Now, you'd have a place for your hardware configurations (eg /opt/hwprofiles), and a directory inside it called 0x10de (ie "Nvidia"), where you could store your /etc/X11/xorg.conf, /etc/hostname, /etc/network/interfaces, or whatever config files you happened to want to customise.

[B]III - Set up a fallback
[/B]
Like you suggested, you might not always be using a machine you've seen before. You might like to create an /opt/hwprofiles/fallback, to handle such a situation with generic configurations.

[B]IV - Connect everything together
[/B]
Imagine you created something like this...```
#!/bin/bash

PCI_BUS=`lspci | grep -i vga | cut -d" " -f1`
LABEL=`cat "/sys/bus/pci/devices/0000:$PCI_BUS/vendor"`

cp /opt/hwprofiles/$LABEL/xorg.conf /etc/X11
```You could save it somewhere like /usr/local/sbin/reconfigure. I've kept things simple, but in practice such a script would be written to properly handle errors & fall back on a default configuration if the appropriate hardware profile directory was nowhere to be found. In any case, you could (in theory) now rewrite your entire hardware configuration with a single command.

**V - A little polish**

This post is getting a little long-winded, so I'll be brief! If you like the idea, I can always go into more detail later, but next on my list would be ...[LIST]
[*]To set up a system "service" (just like CUPS, bluetooth, etc.) that rewrites your system configuration automatically during the boot process, by running the "reconfigure" script.
[*]Make "reconfigure" smarter, so it can handle machines it's never seen before, by giving them a generic configuration.[/LIST]The last thing I would do is make "reconfigure" smarter still, so when you shut down, it copies the computer-specific configuration back into /opt/hwprofiles.  Most of the time, doing that would be a waste of time, but if you refined a computer's configuration in some way, the changes would be preserved, giving you an easy way to teach your Ubuntu to handle new machines.

---

### Post by ericnord on 2007-07-04
Holy Cow Kidders...this is awesome. Way more than I could have asked for! Thank you so much.

That being said I haven't messed around w/ Linux in 5+ years so I could use a little more detail on some of your suggestions. Where would I put the initial script that starts this whole process of identifying. That is, what does Ubutu use to start calling the xconfig file? I'm assuming that is where I would add the code you've mentioned. From there I just identify the HW and then direct to appropriate Xconf file for graphics cards, etc.

I understand all your other suggestions, at least the idea behind them. If the code is correct I can easily past it into the file you define above. 

Thanks so much for this!

---

### Post by kidders on 2007-07-05
Hey again,

Where you put things doesn't *really* matter, but there are a few conventions that are worth adhering to. For instance, scripts & binaries you write/compile yourself, that are intended for use chiefly by root, normally go in /usr/local/sbin. Scripts for starting/stopping services live in /etc/init.d.

I would suggest thinking of automatic system reconfiguration as a "service", that can be started at boot (ie replaces generic configuration files with hardware-specific ones) and stopped at shut-down (ie restores the original generic configuration). Two reasons for doing this are:[LIST=1]
[*]The scripts would always leave your Linux in the condition they found it. That way, you can decide not to use them for a few boots, without having to worry about undoing any tweaks they've made.
[*]The Debian service architecture lets you control startup order, so you can very easily force your scripts to do their thing before the services they modify (eg Xorg) start up. You can also have your system skip execution of your scripts during failsafe boots, etc.
[/LIST]

**Suggestions for handling "new" computers...**

However you decide to do it, imagine that you've defined $LABEL, and that it contains the current computer's identifier. You could do something like this, to set a previously unknown computer up with a generic configuration. Then you (or any helper app) can refine it as you normally would, happy in the knowledge that your changes are being preserved.

```
if [ ! -e "/opt/hwprofiles/$LABEL" ]; then
     mkdir "/opt/hwprofiles/$LABEL"
     cp -dpR /opt/hwprofiles/fallback "/opt/hwprofiles/$LABEL"
fi
```

**Two approaches to preserving configuration changes...**

I'm not sure which of these is better, but here are two ideas:

[COLOR="Blue"]- I -[/COLOR]
Doing what effectively amounts to **cp /opt/hwprofiles/00:11:22:33:44:55/xorg.conf /etc/X11/xorg.conf**. Later, when your service shuts down...```
rm /opt/hwprofiles/00:11:22:33:44:55/xorg.conf
mv /etc/X11/xorg.conf /opt/hwprofiles/00:11:22:33:44:55
cp /opt/hwprofiles/fallback/xorg.conf /etc/X11
```I suppose the main advantage of that approach is that a user who screws up his system configuration beyond rescue can restore it by re-running the boot-time script (eg /usr/local/sbin/reconfigure).

[COLOR="#0000ff"]- II -[/COLOR]
Doing something more like **ln -s /opt/hwprofiles/00:11:22:33:44:55/xorg.conf /etc/X11/xorg.conf**. Later, when you shut down...```
rm /etc/X11/xorg.conf
cp /opt/hwprofiles/fallback/xorg.conf /etc/X11
```Some people might find this a cleaner, more sensible approach. Your system's xorg.conf, etc. would simply be symbolic links to the appropriate location in /opt/hwprofiles.

One possible end result could be...[LIST=1]
[*]As your system boots, it interleaves your service into the boot process in such a way that it runs *before* any of the apps whose configurations it alters.
[*]Your service invokes "/usr/local/sbin/reconfigure", which symlinks various bits & pieces to the appropriate locations in /opt/hwprofiles, creating new hardware profiles as required.
[*]Your system then works as though it was no different than anyone else's. Anything you do (eg activating a vendor-specific display driver) works just like normal.
[*]When you shut down, a call to "/etc/init.d/yourservice stop" invokes "/usr/local/sbin/reconfigure deconfigure" (or something), breaking all the links between system config files & your profile repository.
[*]If your next boot is a failsafe boot of some sort, you don't have to do anything special to get your system to work properly.
[/LIST]

So you might end up with a configuration script that looks something like...```
# Detect what computer you're running on somehow.
LABEL= ...

#Are we starting or stopping?
if [ "$1" = "deconfigure" ]; then
     
     # Restore a "normal" system configuration.
     
else
     
     if [ ! -e "/opt/hwprofiles/$LABEL" ]; then
          
          # Create a new hardware profile.
          
     fi
     
     # Copy or symlink the hardware-specific profile into the system.
     
fi
```

> Holy Cow Kidders...this is awesome.Lol I don't know about that! Anyhow, I hope this helps with some of the ideas I glossed over in my first post. What do you think?



**Edit:**
Something kind of important just struck me. It has to do with cleaning up the mess that might result from an unclean shutdown, so maybe it's a thought that can be left until later, but if I don't mention it now, I might forget hehe!

Basically, I'm wondering how best to control what happens in the event you have to power off your PC without shutting it down normally. Most applications & services are equipped to handle that pretty gracefully, so I suppose yours should too. Here are two ideas. Both of them depend on equipping your custom service with the ability to detect what runlevel it's in, which I'll get to in a moment...

**1: The easier, but riskier approach**
Before it does anything at all, your /usr/local/sbin/reconfigure script would check to make sure it wasn't responsible for installing any of the config files currently present in /etc. If you opt for symlinking config files to /opt/hwprofiles, that could be done with **if [ -h /etc/X11/xorg.conf ]**, for example ... ie testing whether xorg.conf is a symlink.

Otherwise, you could invent a convention of some sort. For instance, imagine that any automagically installed config file always contained the word "hwprofiles". You could then detect an unclean shutdown with something like **if [ -n "`grep hwprofiles /etc/X11/xorg.conf`" ]**, which would be true if the file contained your reserved keyword.

**2: The "proper", more complicated approach**
Many apps & services make use of files in /var, designed to indicate state. For instance, where it exists, /var/run/apache2.pid always contains the PID of the parent web server process. If, for some reason, this isn't the case, Apache knows something odd has happened. You could do this too, removing the need to use properties of your configuration files themselves to detect unclean shutdowns.

Successful installation of a hardware profile could be followed by **mkdir -p /var/run/hwprofiles; touch /var/run/hwprofiles/dummy**, to indicate that custom config files are currently installed into /etc. Successful removal would be followed by **rm /var/run/hwprofiles/dummy**.


Whichever avenue you go down, the very first thing your reconfiguration script should do is check whether a previously installed hardware-specific configuration is still in the system and, if appropriate, try to recover by (a) running the de-install procedure, or (b) regarding the orphaned config files as potentially faulty & doing something different.

**A quick note about runlevels**
Since you mention you have experience with Linux (albeit 5 years ago), you probably know this already, but just in case, a Linux system is always in one of a number of "runlevels", which indicates what it is currently doing. For instance, runlevel 6 means "rebooting", so many applications (eg a proxy or web server) will normally refuse to start, if asked to do so in runlevel 6. Runlevel 1 is "single user mode", often used with failsafe boots. Some (but not all) services will refuse to start in runlevel 1 ... or perhaps modify what "start" means ... to accommodate the odd way the system has been booted. To be completely perfect, your reconfigurator script should do this too:[LIST=1]
[*]Detect what computer it's running on.
[*]Check for unclean shutdowns & recover if necessary.
[*]Check the runlevel.
[*]Set up hardware-specific configurations only in runlevels 2,3 & 5 (for example); otherwise terminate.
[/LIST]

That way, you get the best possible guarantee that your system will be able to recover from botched boots/shutdowns, but won't get set up with hardware-specific configurations, when they're not wanted. This would be much more robust than the alternative, which is simply not to start your service at all, when you boot in failsafe mode ... a detail Ubuntu could have taken care of *for* you.

I hope I haven't confused you by mentioning this now!

---

