---
title: "flash player problem"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by zhongwei on 2007-03-31
Hello I have a problem

I recently tried to install flash 9 for edgy, using this command line: 

sudo aptitude update && sudo aptitude install flashplugin-nonfree

I recieved an error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache

so I followed this up (a mistake I think) and ran this line of code:
zhongwei@zhongwei:~$ sudo dpkg --configure -a
Setting up libssl0.9.7 (0.9.7k-3) ...

Which resulted in this (I show only the end message):


No candidate version found for flashplugin-nonfree
The following packages have been kept back:
  azureus vmware-player 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the vmware-player package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

I am a real noob, and cant seem to get a grip on this command line stuff as yet. this is slow progress here lol.

What do I need to do to get flash up and running?

---

### Post by aysiu on 2007-03-31
Try this instead:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

By the way, you need to [enable the Multiverse repositories](http://www.psychocats.net/ubuntu/sources) to install Flash using *aptitude*.

---

### Post by zhongwei on 2007-03-31
Aysiu

I followed all instructions on the links provided. It appeared to work. Unfortunately flash still does not work. Is there a file that I could post here to see where the problem is?

---

### Post by aysiu on 2007-03-31
Hm. That's odd. A few follow-up questions.

You say you "followed all instructions on the links provided." Does that mean you installed it both manually *and* through the repositories? If so, which did you do first?

Also, can you elaborate a bit on "Flash still does not work"? When you visit a site that requires Flash, what happens? Are you told there's a missing plugin? Or does the plugin appear to be doing something, but you get a little blank square instead of moving Flash animation?

Can you post the output of these commands? ```
cd ~/.mozilla/plugins/
ls
cd /usr/lib/firefox/plugins
ls
```

---

### Post by zhongwei on 2007-04-01
zhongwei@zhongwei:~$ cd ~/.mozilla/plugins/
bash: cd: /home/zhongwei/.mozilla/plugins/: No such file or directory
zhongwei@zhongwei:~$ ls
automatix2.key  Desktop  Firefox_wallpaper.png  flash terminal stuff  Paul
zhongwei@zhongwei:~$ cd /usr/lib/firefox/plugins
zhongwei@zhongwei:/usr/lib/firefox/plugins$ ls
flashplayer.xpt                  libunixprintplugin.so
libflashplayer.so                mplayerplug-in-gmp.so
libtotem-basic-plugin.so         mplayerplug-in-gmp.xpt
libtotem-basic-plugin.xpt        mplayerplug-in-qt.so
libtotem-complex-plugin.so       mplayerplug-in-qt.xpt
libtotem-complex-plugin.xpt      mplayerplug-in-rm.so
libtotem-gmp-plugin.so           mplayerplug-in-rm.xpt
libtotem-gmp-plugin.xpt          mplayerplug-in.so
libtotem-mully-plugin.so         mplayerplug-in-wmp.so
libtotem-mully-plugin.xpt        mplayerplug-in-wmp.xpt
libtotem-narrowspace-plugin.so   mplayerplug-in.xpt
libtotem-narrowspace-plugin.xpt
zhongwei@zhongwei:/usr/lib/firefox/plugins$

---

### Post by zhongwei on 2007-04-01
When trying to watch you tube I get this message:

Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player. 

I checked firefox preferences. Javascript and java is enabled.

---

### Post by zhongwei on 2007-04-01
sorry answer to first question:


You say you "followed all instructions on the links provided." Does that mean you installed it both manually and through the repositories?

I think I did the repositories first. But to be honest I am not certain. Which should I do first?

---

### Post by aysiu on 2007-04-01
Well, it looks as if you definitely have it installed: ```
zhongwei@zhongwei:/usr/lib/firefox/plugins$ ls
flashplayer.xpt libunixprintplugin.so
libflashplayer.so mplayerplug-in-gmp.so
``` As for that message you get, do you have Javascript turned off (or do you use the NoScript extension in Firefox?)? If you installed it through the repositories, you may, in fact, have an older version of Flash (Flash 7 instead of Flash 9).

As for the order, there is no order. You're actually not supposed to do both. You're supposed to *either* install it through the repositories *or* install it manually.

I'd suggest you install it manually and just forget about the repositories for now.

Can you close Firefox, follow all of these instructions and only these instructions, and then visit again that site that requires Flash?
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by zhongwei on 2007-04-01
[I]I'd suggest you install it manually and just forget about the repositories for now.

Can you close Firefox, follow all of these instructions and only these instructions, and then visit again that site that requires Flash?
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)[/I]

Still does not work. yes I  copied instructions into text file, then did the steps with firefox closed. 

the attachment has installation from terminal info.

---

### Post by zhongwei on 2007-04-02
If anyone is reading this thread, I will add something. Grasping at straws here lol

I recently switched from dapper to edgy because dapper was proving difficult with regards to getting it to recognize my nvidia card. With dapper I could watch youtube but not video files. now with edgy I can watch video but not youtube (flash worked). 

I dont have any idea if this is related to my present problem, but maybe it is?

---

### Post by KeighleHawk on 2007-04-03
So these instructions do not seem to be working for me either.  When I look at the file type management on a windows box, I notice I have an entry for .swf and .spl.  On my Ubuntu box I have only an entry for .spl.  I assume I need the .swf entry.  How do I add it?

---

### Post by KeighleHawk on 2007-04-03
Okay, I found it...

Open Firefox and type about:plugins in the URL Field.  You should see two entries for Shockwave files.  The ill behaved one will be fairly obvious as it specifically talks about drinking all your milk and shooting kittens from a cannon.  Locate and remove the file associated with that one.  For me, it was in /usr/lib/mozilla/plugins and was named libswfdecmozilla.so.

Restart Firefox and begin YouTube'ing...

---

### Post by zhongwei on 2007-04-03
Hi, thanks for posting.

could you walk me through the steps? I tried typing about plugins and aboutplugins in url of firefox. went to a website on plugins. yes I am a complete noob lol

---

### Post by KeighleHawk on 2007-04-04
Sorry, that's what I get for posting without previewing.  The text got turned into a smiley.  The correct text was about colon plugins with the actual ':' and no spaces.  

I see now there is a disable smilies check box so let's see if I can make this appear right....

about:plugins

And it should work from there....

---

