---
title: "A solution that Worked for getting Frostwire to WORK in Edgy"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by myke on 2006-11-07
I may have cross posted this in the "how to" section but I'm not sure if it made it up so if it did ... moderators, I apologize and remove one but it seems to be an ongoing problem for getting a new installation of FrostWire working with Edgy.  Also, if there is a more appropriate forum for this post, please feel free to move it.  I thought this one fit best.   I tried to provide this solution that may help a few folks to the frostwire and gnutella forums as well.   I was so frustrated by the problem, I hoped to at least help a Edgy user or two to fix the same problem.

Anyway ...

I use the Kubuntu Edgy variant of Linux and have tried everything that was proposed here, the frostwire forums, and in the gnutella forums to fix the nagging issue of my new installation of FW freezing at the "starting connection" point and detecting a firewall that wasn't there.   Here is what finally worked for me.

I started with this thread:  [http://www.frostwire.com/forum/viewtopic.php?t=666](http://www.frostwire.com/forum/viewtopic.php?t=666) that suggested dumping the hosts listed on the gnutella.net file with a new list as mentioned in the thread.  I tried that but it didn't work along with several other solutions (port forwarding, java selection, etc.).  However,  the following was suggested to me as a variant of the solution for replaces then sources in the gnutella.net file:

[quote="et voilà"]mykeCXV: then replace your gnutella.net with this one [http://mc3.electronicbox.net/gnutella.net](http://mc3.electronicbox.net/gnutella.net)[/quote]

I did this and IT WORKED.  FW is now running with an 'excellent connection' and on false detection of a non-existent firewall.  

Go to your home folder and check "view hidden files" from the view drop down menu.   Open the .frostwire folder.  Then DELETE the gnutella.net~ file.  This one is a backup file that FW automatically creates.  It will put the deleted sources right back in on FW's restart and cause the same connection problem.  It did on mine anyway.   After deleting this file, open the gnutella.net file with a text editor.  Select all and cut or delete out the list.  Copy and paste the much much longer list of sources from the link above kindly provided by et voila.    Save the file.  FW will create a new backup file for just this list.  You should, of course, shut down FW prior to all of this and restart it afterward.  After pasting in this new and much longer list of sources, my FW started up quickly, connected quickly, and didn't detect a false firewall.  

I hope this helps another Linux user!

---

### Post by Ouchy on 2006-11-07
This worked for me! (Had same problem in Dapper)

Thanks a lot! :)

---

### Post by Jongi on 2007-01-07
Good to know

---

### Post by Spike-X on 2007-02-14
I was stuck at the 'Starting Connection' stage. I tried Port Forwarding. Nothing. I checked out the links given above - neither of them currently work. The one for the Frostwire forums is outright broken, and the one to the alternate list of sources for gnutella.net diverts to something called 360share.com.

I did replace the list of sources in my gnutella.net file with a list I found on the actual Gnutella site, but that didn't fix the problem either. Then...

BRAINWAVE!!! I copied my gnutella.net list from my Limewire installation on my Windows drive! EXCELLENT CONNECTION!!!

---

### Post by plvaulter06 on 2007-12-22
i love you!!!!! something that worked

---

### Post by fourthdimension on 2008-01-05
It doesn't work for  me..:(  the link just asks me to download a filesharing program for windows.

---

### Post by Jongi on 2008-02-24
Here is the file

---

### Post by swiftbiscuit on 2008-04-21
After two hours of replacing gnutella.net files, changing router settings, and even removing iptables from my machine, this finally did the trick. And if anyone is interested I am running on a ps3. 

  Thank you!

  -Adam

---

### Post by gottatrieit on 2008-04-22
Thank you,jongi, for a clean link!
I downloaded it, unzipped it, and swapped it with the old file and bingo --- Frostwire is now downloading some songs for me as I type!
I had installed/uninstalled Frostwire about three or four times in the last nine months to get it to work on Gutsy!
I am a very happy person thanks to you!

           Rick \\:D/

---

