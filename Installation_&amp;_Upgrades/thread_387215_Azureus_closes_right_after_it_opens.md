---
title: "Azureus closes right after it opens"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Frenzy-br on 2007-03-18
i installed azureus because its the only torrent client i found that you can choose which files to dl and which files not to dl, it worked great, then when i restarted my machine and tried to open azureus it opens and closes right back if i try to add another torrent file to it it will open and close right back as well , can some one offer some assistance...

---

### Post by Kateikyoushi on 2007-03-18
Go to your home directory in Nautilus and push CTRL+H to see hidden files and directories, then open the .azureus directory, go to logs and delete every logfile in it, then go to save and delete every logfile again, then start azureus.

---

### Post by Fylen on 2007-03-18
It works great for me, thanks  a lot ^^

---

### Post by Frenzy-br on 2007-03-18
it worked great... thx alot... do you mind telling me why it works???

---

### Post by petehall on 2007-03-19
I'm having the same problem, but the above suggestion didn't work. In fact, even if I delete my .azureus directory entirely, it still crashes when I try to load it.

I've looked at the log file and the problem seems to be centred around a call to java.net.NetworkInterface.getAll()

UPDATE: Disappointingly, I solved this problem by restarting my computer.

---

### Post by Frenzy-br on 2007-03-19
> **petehall said:**
> I'm having the same problem, but the above suggestion didn't work. In fact, even if I delete my .azureus directory entirely, it still crashes when I try to load it.

I've looked at the log file and the problem seems to be centred around a call to java.net.NetworkInterface.getAll()

UPDATE: Disappointingly, I solved this problem by restarting my computer.

wow i thought that it was only in windows that you could fix problems by restarting your pc...

---

### Post by airtonix on 2007-03-19
could have tried this maybe?

```

sudo killall java

```

or this :
```

sudo apt-get remove azureus

```
  
lol, i hate this program, its total bloatware.

oh and OP...and others...you may want to check out rtorrent....

pros : 
 + extremely low mem & cpu resource usage as it use s the ncurses interface...
 + therefore can be run in a virtualTerminal.....tty1-tty5
 + therefore will keep running if you need to logout of your desktop(ie leave the room for long time....me sooo H****NY (sorry lol))
 + you can choose which files to download

cons
 + gui fan boiz will cry.
 + you will need more harddrive space.

or you could try ktorrent. or the windows utorrent under wine.....

/cry.....shame utorrent isnt native to linux as it really is what your looking for here its only 170kb in total, the program is only one file! absolutly kickarse.
sigh just have to put up with the wine thingo...

---

### Post by Kateikyoushi on 2007-03-19
> **petehall said:**
> I'm having the same problem, but the above suggestion didn't work. In fact, even if I delete my .azureus directory entirely, it still crashes when I try to load it.

I've looked at the log file and the problem seems to be centred around a call to java.net.NetworkInterface.getAll()

UPDATE: Disappointingly, I solved this problem by restarting my computer.

I didn't say you have to delete .azureus in your case probably java was still running, have to stop that first.

---

### Post by Frenzy-br on 2007-03-21
> **airtonix said:**
> could have tried this maybe?

```

sudo killall java

```

or this :
```

sudo apt-get remove azureus

```
  
lol, i hate this program, its total bloatware.

oh and OP...and others...you may want to check out rtorrent....

pros : 
 + extremely low mem & cpu resource usage as it use s the ncurses interface...
 + therefore can be run in a virtualTerminal.....tty1-tty5
 + therefore will keep running if you need to logout of your desktop(ie leave the room for long time....me sooo H****NY (sorry lol))
 + you can choose which files to download

cons
 + gui fan boiz will cry.
 + you will need more harddrive space.

or you could try ktorrent. or the windows utorrent under wine.....

/cry.....shame utorrent isnt native to linux as it really is what your looking for here its only 170kb in total, the program is only one file! absolutly kickarse.
sigh just have to put up with the wine thingo...

HOW DO YOU GET UTORRENT TO RUN ON LINUX.... there is absolutely nothing better than utorrent for torrent.... damn it they need to make it open source

---

### Post by slave1 on 2007-03-21
Thank you Kateikyoushi. Your workaround was spot on. 2 thumbs up for you :KS 

Tried rtorrent as well, and I think I'll stick to Azureus. The key navigation reminded me too much of vim (and I don't have the patience to learn a whole new bunch of key commands).

Ta,
Slave1.

---

### Post by Darko-TheRaven on 2007-03-21
> **petehall said:**
> I'm having the same problem, but the above suggestion didn't work. In fact, even if I delete my .azureus directory entirely, it still crashes when I try to load it.

I've looked at the log file and the problem seems to be centred around a call to java.net.NetworkInterface.getAll()

UPDATE: Disappointingly, I solved this problem by restarting my computer.

I had this problem, try installing Sun Java Console

---

### Post by grogger13 on 2007-04-01
your fix worked at first, but then about 30 seconds to about a minute it crashed again, so then i redeleted the files and it crashed again after the same time

---

### Post by rillip on 2007-04-01
I personally like ktorrent, and it has the feature you mention. I like the Azreus frog, but found the pgram itself annoying to use.  I'm not interested enough to learn to use rtorrent (I wouldn't say I'm a gui fan boy, but, I did install a gui for a reason...).

Edit: Also note that if you're out of disk space, unpredictable things can start to happen.  I let ktorrent fill my drive and my webbrowser (Opera) started to randomly close itself.  Not to mention when I rebooted there wasn't enough room to create the fiels neccesary tostart xserver, so I couldn't get past a login prompt.  It sounds silly, but it's worth the time to check.

---

### Post by TheFuzz4 on 2007-06-20
That worked like a champ.  For those wanting to run utorrent I was able to get it to run through WINE so you might want to try that.  I got it run in WINE through Fedora so I'm not totally sure in Ubuntu I just switched over about two weeks ago.  But no more dual boot on this machine Ubuntu only :)

---

### Post by shaynegryn on 2007-08-14
This worked!!!! Thank you Kateikyoushi! \(^_^)/ u r teh l33t

---

### Post by zorkerz on 2007-09-19
This has not worked for me.

Here is my terminal output
> 
azureus
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
DEBUG::Wed Sep 19 21:00:07 EDT 2007::org.gudy.azureus2.pluginsimpl.local.utils.resourcedownloader.ResourceDownloaderURLImpl::download::516:
  Inconsistent stream length for 'http://192.168.1.1:2869/IGatewayDeviceDescDoc': expected = 3441, actual = 3442
    ResourceDownloaderURLImpl$2::runSupport::319,AEThread::run::69
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  Internal Error (53484152454432554E54494D450E435050020F), pid=8421, tid=3084934032
#
# Java VM: Java HotSpot(TM) Server VM (1.6.0_02-b05 mixed mode)
# An error report file with more information is saved as hs_err_pid8421.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)

looks like some kind of java error anyone know how to fix it?

---

### Post by novakry on 2007-10-20
bump.

having the same problem as the guy above (with same error showing up in the terminal when i run it from there), I went about reinstalling java from java.com and no avail there. by deleting the .azureus folder it lets me set up the client and then when it comes to using it properly it just crashing again like before. 

currently using utorrent with wine and alltray, it does what i need but I would prefer to be using azureus.

Hope someone can work out.

---

### Post by moffa on 2007-10-20
> **Frenzy-br said:**
> HOW DO YOU GET UTORRENT TO RUN ON LINUX.... there is absolutely nothing better than utorrent for torrent.... damn it they need to make it open source

It works perfectly with wine

---

### Post by misterbeetz on 2007-10-20
> **novakry said:**
> bump.

having the same problem as the guy above (with same error showing up in the terminal when i run it from there), I went about reinstalling java from java.com and no avail there. by deleting the .azureus folder it lets me set up the client and then when it comes to using it properly it just crashing again like before. 

currently using utorrent with wine and alltray, it does what i need but I would prefer to be using azureus.

Hope someone can work out.

I found another thread that focuses on the same problem in 32-bit gutsy:

[http://ubuntuforums.org/showthread.php?t=580028&highlight=azureus&page=2](http://ubuntuforums.org/showthread.php?t=580028&highlight=azureus&page=2)

I posted a quick fix in there that worked for me.

- misterbeetz

---

### Post by SammyBoy247 on 2007-11-02
Had the same Azureus problem and the log file trick worked fine - does any one know the cause of the problem?  Just curious.

---

