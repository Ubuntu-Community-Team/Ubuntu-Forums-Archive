---
title: "Edgy Upgrade Problems Resolved"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by marc.m on 2006-11-13
I originally posted this as a "note to self" on my personal site, but thought they may be of use to someone, so here they are.  These are my notes on problems and resolutions while upgrading from Dapper 6.06 to Edgy 6.10.

I upgraded from KDE, by using the recomended command, [FONT="Courier New"]kdesu "update-manager -c"[/FONT] or [FONT="Courier New"]gksudo "update-manager -c"[/FONT] (if in Gnome) as recommended in the [documentation]("https://help.ubuntu.com/community/EdgyUpgrades").

All seemed to be going ok until an error :( stating 

> trying to overwrite '/usr/X11R6/bin', which is also in package opera"

after which the update stopped, leaving the system about half-baked. :-?  

I found the following [reference]("http://groups.google.com/group/linux.debian.user/browse_thread/thread/e0e985c822a26971/06b4f21d6a214b90?lnk=st&q=trying+to+overwrite+%60%2Fusr%2FX11R6%2Fbin%27%2C+which+is+also+in+package+opera&rnum=2&hl=en#06b4f21d6a214b90") giving a purge command for opera

> sudo dpkg -P opera

Now knowing, I would advise anyone else to remove opera prior to upgrading. After removing Opera, I used Synaptic, since my repositories had already been updated by update-manager, fixed dependencies, marked all upgrades, and applied the changes which still took quite a while to download and install.  Everything went well this time and the upgrade finished. 

When I rebooted, I encountered a problem starting X, so from the command line, I tested my configuration using the following steps, and proceeded to fix the issues.

How to test your xorg.conf file can be found <a href="http://www.gentoo.org/doc/en/xorg-config.xml">here</a>.

> X -config /root/xorg.conf.new

If all goes well, you should see a simple black and white pattern. Verify if your mouse works correctly and if the resolution is good. You might not be able to deduce the exact resolution, but you should be able to see if it's too low. You can exit any time by pressing Ctrl-Alt-Backspace.


The first error I encountered was that the NVidia driver wasn't present. The steps to fix this are pretty easy.
[LIST]
[*][FONT="Courier New"]apt-cache search nvidia[/FONT] and you'll see the "nvidia-glx" driver
[*]Install it with [FONT="Courier New"]sudo apt-get install nvidia-glx[/FONT]
[/LIST]

After adding the NVidia driver I tested my configuration again and got the following error. ](*,) 

> (EE) No input driver matching 'keyboard'
(EE) No input driver matching 'mouse'
No core keyboard


A post on the [UbuntuForums.org]("http://www.ubuntuforums.org/archive/index.php/t-35094.html") site contained the fix.

> The xserver is going modular, you need to get xserver-xorg-input-mouse, xserver-xorg-input-kbd, and xserver-xorg-driver-foo where foo is the driver you use (unless you use a proprietary ATI or nVidia one). If X still fails to start after that edit xorg.conf and change Driver 'keyboard' to Driver 'kbd' and you should be good.


After following this, my X11 configuration tested successfully, and I was able to boot graphically as normal.

There were a couple of other minor things :-k that had to be done before I felt like I was really running an up-to-date Edgy system. One was Azureus. I had manually installed a version once upon a time, and was still running that version. Reinstalling Azureus using Synaptic quickly fixed that.

Second was a version of Firefox, again that I manually installed. Using Synaptic I installed Firefox, and then had to remove firefox from [FONT="Courier New"]/opt/firefox/firefox[/FONT] and create a new symbolic link to [FONT="Courier New"]/usr/lib/firefox/firefox[/FONT].  To do this, [FONT="Courier New"]ln -s /usr/lib/firefox/firefox /opt/firefox/firefox[/FONT].  After this, I think you can safely remove the rest of the files in the [FONT="Courier New"]/opt/firefox/[/FONT] directory (although I havn't verified this).

At this point, I had and have a fully functional Ubuntu 6.10 Edgy Eft machine, and am very happy with all of the improvements, it was just a bit of work to get here.

i hope this helps. Enjoy Edgy! :)

---

### Post by marc.m on 2006-11-14
I just found that, in fact, Azureus is not working on my upgraded machine.  [-(  I know that I test ran it a couple of days ago while working out the kinks of the upgrade. However, tonight, the splash screen runs, and as soon as the application window displays, it dies with the following.

> # An unexpected error has been detected by HotSpot Virtual Machine:
#
# SIGSEGV (0xb) at pc=0xb0527d02, pid=8613, tid=3085334192
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C [libglibjni-0.4.so+0x8d02]

Searching around there were several fixes proposed, but none resolved the issue for me. Then I remembered :rolleyes: some of the steps required last time I configured Azureus (maybe in Ubuntu 5.10, a year isn't too bad without any problems). One of these steps was pointing to a different version of Java, so I searched my machine ([FONT="Courier New"]locate java | less[/FONT]) and found a few versions other than the one on the default path. So I tried them, and found that a couple of them worked and made Azureus happy.

To make Azureus use one of these versions when it starts, I changed the [FONT="Courier New"]/usr/bin/azureus[/FONT] start script. You can enter [FONT="Courier New"]whereis azureus[/FONT] to find where the start script is located on your machine.

The command to start Java and Azureus is at the end of the script. In my case I changing the line

```
exec java -Djava.library.path=/usr/lib/jni:/usr/lib \
```

to

```
exec /usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/bin/java -Djava.library.path=/usr/lib/jni:/usr/lib \
```
or
```
exec /usr/lib/j2re1.5-sun/bin/java -Djava.library.path=/usr/lib/jni:/usr/lib \
```

resolved the problem. :p (basically changed java to the full path for a different java version).

Your path may differ depending on the version(s) of java available on your machine. You can always grab other versions using apt or Synaptic.

---

### Post by mgmiller on 2006-11-15
I remember having a similar problem with azureus in breezy.  The solution is easier than you have posted.  You noted that your system had several versions of java installed, as mine did.  The following command shows you what is there and allows you to select the one you want to use.  Quick and easy.  I just switched mine to the sun java and all was well with azureus and everything else.

```
sudo update-alternatives --config java
```

---

