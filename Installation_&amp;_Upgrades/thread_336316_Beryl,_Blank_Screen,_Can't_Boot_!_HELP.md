---
title: "Beryl, Blank Screen, Can't Boot ! HELP"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by Jaygo333 on 2007-01-11
Ok, Yersterday I wanted to install Limewire but when I did. I got a funny error which I thought was caused by Beryl, since I hearrd Beryl sometimes doesnt work well with Java.
So I didabled Beryl in start up and entered normal GNOME to install limewire. I did, got same error. I checked forums for answer found it and fixed Limewire. I then decied to enable Beryl in the Sessions manager to use it. I restarted X11 and when I logged in, the boot splash would appear but after that, nothing. The window would just hang. the mouse would load but after that, nothing. The colour that starts up Ubuntu when splash-screen is running. Thats where it hangs.
The panels are gone and the desktop is gone. In safe mode, I just get a blank white box in the corner of my screen.

I do believe its Beryl, because the splash-screen disappears the moment I usually see Bery starting.

So how do I fix this and also how do I disable startup programs from terminal. I have no access to Sessions to do it.

---

### Post by arnieboy on 2007-01-11
```
rm -f ~/.config/autostart/beryl-manager.desktop
```

---

### Post by Jaygo333 on 2007-01-11
thank you, gonna test it, Give ten minutes.

Could you explain what the command does so I can use it next time if needed on  another program?

---

### Post by Jaygo333 on 2007-01-11
I mnanaged to stop Beryl, 
I did get an error in terminal about rm being invalid.
So I decided to find the config fime and remove beryl.
Now when I start, i get 
"failed initialise HAL.
Help agin plz.

---

### Post by arnieboy on 2007-01-11
If you have automatic logon enabled, change it to "timed logon" with a delay of 5 seconds.

---

### Post by Jaygo333 on 2007-01-11
I dont have any logon timer set.
I decied to reboot and when did so wanted to see what was letting my shutdown hang.
I fould out when shutting down, then PC hangs at, Stting down ALSA..
I have a Sound blaster X-FI and since htere are no drivers, have been following the article found at [http://ubuntuforums.org/showthread.php?t=334358](http://ubuntuforums.org/showthread.php?t=334358) with no success. I did do alsaconf and since ubuntu didnt recognize my sound card went with the option to istall Intel, sound stuff insted of legacy.
How do I stop ALSA from lagging ant shutdown.

P.S. The HAL question disappeared when I restarted,  and I can load beryl properly in terminal when booted but not with Session managere, why?

---

### Post by Jaygo333 on 2007-01-11
Thank yo for all your help arnieboy. Ubuntu fo Life.

---

### Post by arnieboy on 2007-01-11
> **Jaygo333 said:**
> I dont have any logon timer set.
I did not say you do. Read my post carefully again. Do you automatically log on to Gnome everytime or you punch in your user name and password?

---

### Post by Jaygo333 on 2007-01-11
I punch in my name and password all the time.

---

### Post by arnieboy on 2007-01-11
> **Jaygo333 said:**
> I punch in my name and password all the time.

alright. The HAL initialization often has to do with some services (which start only after xserver starts) not starting up quickly enough. Its a known bug but is not regularly reproducible.  The lag in log in time often solves this issue.
As for your sound card, have you modified any of the ALSA config files such as ~/.asoundrc or /etc/asound.conf? 
If yes, post their contents here:
```
cat ~/.asoundrc
cat /etc/asound.conf
```

---

### Post by Jaygo333 on 2007-01-11
Thank you for the HAL issue.
The Alsa issue, Ive never configured alsa before the results of the commands yield nothing

jaygo333@edgy:~$ at ~/.asoundrc
syntax error. Last token seen: /
Garbled time
jaygo333@edgy:~$ cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory
jaygo333@edgy:~$ cat /etc/asound.conf

the only command Ive ever run about Alsa is alsaconf that's it.

---

### Post by arnieboy on 2007-01-11
open up **/etc/modutils/alsa-base** and comment out the lines (add a # before them) which try to load your creative X-fi card. This card is currently unsupported by ALSA and Creative has promised closed source support for the same in the second quarter of 2007.
you can also paste the output of the following:
```
cat /etc/modutils/alsa-base
```

---

### Post by Jaygo333 on 2007-01-11
Problem, I just checked and the alsa-base file doesnt exist

jaygo333@edgy:/etc/modutils$ ls
apm  bluez  evms  lvm-common  nvidia-kernel-nkc
jaygo333@edgy:/etc/modutils$ 

Noo sound.. Im going to break one of my legs for this.
Im going to have to start using windows agaoin just fo sound. ..

---

### Post by Jaygo333 on 2007-01-11
Should I just sudo-apt-get remove alsa to stop it from shutdown problems or is there a way to disable it from loading.

---

### Post by arnieboy on 2007-01-11
okay the correct location is /etc/modprobe.d/alsa-base
post the results of the following:
```
cat /etc/modprobe.d/alsa-base
```

---

### Post by Jaygo333 on 2007-01-11
I have another alternative to use in Linux. I have an onbaord sound card for the motherboard (ASUS  P5LD2) Is there a way to enable that sound and install it drivers for it.
I do believe I have the onboard sound card enabled.

---

### Post by Jaygo333 on 2007-01-11
jaygo333@edgy:/$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
jaygo333@edgy:/$

---

### Post by arnieboy on 2007-01-11
ok try this: Open up the file as follows:
```
sudo gedit /etc/modprobe.d/alsa-base
```
and comment out the last two lines
> options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
by making them look as follows:
> #options snd-usb-audio index=-2
#options snd-usb-usx2y index=-2
save and close the file and try restarting your computer.

---

### Post by Jaygo333 on 2007-01-11
It worked, I thnk, Ill have to shutdown in terminal to see any changes but the computer did shutdown so I'm pleased. 
Is tehre a way to have sound throught the onboard one though ?

---

### Post by Jaygo333 on 2007-01-11
1 more random question, if you have the time. 
Whenever I run limewire, I get ablank screen. Is it Beryl. ( I have it enabled)

---

### Post by arnieboy on 2007-01-11
> **Jaygo333 said:**
> It worked, I thnk, Ill have to shutdown in terminal to see any changes but the computer did shutdown so I'm pleased. 
Is there a way to have sound throught the onboard one though ?
well the module which loads your intel integrated card seems to be added to ALSA. paste the results of the following:
```
more /proc/asound/cards
lspci | egrep audio

```

---

### Post by Jaygo333 on 2007-01-11
jaygo333@edgy:~$ more /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd7ff8000 irq 50
jaygo333@edgy:~$ lspci | egrep audio
01:01.0 Multimedia audio controller: Creative Labs Unknown device 0005
jaygo333@edgy:~$ 

So it is working, Let me test a bit??

---

### Post by Jaygo333 on 2007-01-11
YEEEEEEEEEEESSSSSS, THANK you. It is working. 2.1 though, Im happy thoug, I can now wai till later in the year for the drivers.

---

### Post by arnieboy on 2007-01-11
> **Jaygo333 said:**
> 1 more random question, if you have the time. 
Whenever I run limewire, I get ablank screen. Is it Beryl. ( I have it enabled)

yes its because of Beryl and how it talks to java. Make sure you have java 1.5 installed 
```
java -version 
```
will tell you that.
Also, install frostwire which is an open sourced version of limewire and works just as well if not better.
The latest deb can be found here:
[http://www.frostwire.com/download.php?file=http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.4.i586.deb](http://www.frostwire.com/download.php?file=http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.4.i586.deb)

---

### Post by Jaygo333 on 2007-01-11
jaygo333@edgy:~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
jaygo333@edgy:~$ 

Installing frostwire now

---

### Post by penvzila on 2007-01-11
> **arnieboy said:**
> alright. The HAL initialization often has to do with some services (which start only after xserver starts) not starting up quickly enough. Its a known bug but is not regularly reproducible.  The lag in log in time often solves this issue.
As for your sound card, have you modified any of the ALSA config files such as ~/.asoundrc or /etc/asound.conf? 
If yes, post their contents here:
```
cat ~/.asoundrc
cat /etc/asound.conf
```

Good catch.  My automatic login was too fast.

---

### Post by Jaygo333 on 2007-01-11
> **arnieboy said:**
> yes its because of Beryl and how it talks to java. Make sure you have java 1.5 installed 
```
java -version 
```
will tell you that.
Also, install frostwire which is an open sourced version of limewire and works just as well if not better.
The latest deb can be found here:
[http://www.frostwire.com/download.php?file=http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.4.i586.deb](http://www.frostwire.com/download.php?file=http://www.peercommons.com/frostwire/4.13.1/frostwire-4.13.1.4.i586.deb)

It runs but still blank screen In Terminal..

sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:211)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:314)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)

Rest of command continued on next post.

---

### Post by Jaygo333 on 2007-01-11
Event dispatch in wrong thread
expected thread was [Lirc.DispatchThread;@82d210
current thread is Thread[main,5,main]
please submit a bug report to [email]bugs@frostwire.com[/email] with the following information :
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1158)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.print(Unknown Source)
        at irc.gui.pixx.BaseAWTSource.reportReceived(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at irc.EventDispatcher.dispatchEventSyncEx(Unknown Source)
        at irc.ListenerGroup.sendEventEx(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.ListenerGroup.sendEvent(Unknown Source)
        at irc.Source.report(Unknown Source)
        at irc.IRCServer.sendStatusMessage(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCServer.connect(Unknown Source)
        at irc.IRCApplication.newServer(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:211)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:314)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:256)
        at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at com.limegroup.gnutella.gui.Main.main(Main.java:44)
jaygo333@edgy:~$

---

### Post by Jaygo333 on 2007-01-11
It forgot the top part ..\

jaygo333@edgy:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
java.lang.ClassNotFoundException: irc.plugin.
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:268)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:164)
        at irc.IRCApplication.loadPlugin(Unknown Source)
        at irc.IRCApplication.init(Unknown Source)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<init>(ChatMediator.java:119)
        at com.limegroup.gnutella.gui.chat.ChatMediator.<clinit>(ChatMediator.java:68)
        at com.limegroup.gnutella.gui.MainFrame.<init>(MainFrame.java:121)
        at com.limegroup.gnutella.gui.GUIMediator.<init>(GUIMediator.java:211)
        at com.limegroup.gnutella.gui.GUIMediator.instance(GUIMediator.java:314)
        at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:25

---

### Post by Jaygo333 on 2007-01-11
Too confusing...
I wanna go bath so will be back in 20 minutes. (Too early in the mornig for me) 
Thank you arnieboy for all your help.

---

### Post by arnieboy on 2007-01-11
Refer to this thread for a workaround to this issue (It has two solutions, the first one in in the first post should work out of the box):
[http://ubuntuforums.org/showthread.php?t=321727](http://ubuntuforums.org/showthread.php?t=321727)

---

### Post by Jaygo333 on 2007-01-11
I was looking around for a fix to the Java thnig and ran across a script that people have been running to make Java work. I tried the script but doesnt work for me I dont know why.
A person has posted a way I think to make it permanaent but I dont understand it.
Could you simplify it for me please.

[http://noiesmo.dnsalias.net/article.php?story=20061217105248161](http://noiesmo.dnsalias.net/article.php?story=20061217105248161)

---

### Post by arnieboy on 2007-01-11
```
gedit ~/.bash_profile
```
and add the following lines to the end of the file:
> AWT_TOOLKIT=MToolkit
export AWT_TOOLKIT 
save and close the file and log out of Ubuntu and log back in and run frostwire.

---

### Post by Jaygo333 on 2007-01-11
> **arnieboy said:**
> ```
gedit ~/.bash_profile
```
and add the following lines to the end of the file:

save and close the file and log out of Ubuntu and log back in and run frostwire.

I did that and when restarted, linux couldnt log in.
I log in and no splash window, it just hangs. I thought it was Beryl, disabled it and still just hangs.
Now  have no clue, either its the script i jsut did to bash thingie or the script I got for the frostwire thing that couldnt chmod.
Its just hanging.

---

