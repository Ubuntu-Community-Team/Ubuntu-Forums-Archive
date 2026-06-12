---
title: "nautilus-actions doesn't work with Karmic"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2009-12-08
I installed the distributed version of nautilus-actions into Karmic.  Couldn't make it work.  Found a web site [https://launchpad.net/~randomaction/+archive/ppa](https://launchpad.net/~randomaction/+archive/ppa) which has an updated version of nautilus-actions  	2.29.1-1~karmic1~ppa1.  Installed it and tried to bring up in the Terminal nautilus-actions-config.  Got an error message saying it wasn't installed.  Yet Synaptic showed it as being installed.

Anybody got an idea of where I go from here?

Ralph

---

### Post by aadam12 on 2010-01-16
I had a similar problem. I finally got nautilus-actions 2.29-1 to work in Karmic. 

- I had nautilus-actions v1 installed.
- In synaptic I added the ppa that you linked to
- I also added their pgp key
- I upgraded nautilus-actions v1 to nautilus-actions v2
- I had to delete all of my old version 1 nautilus-action schemas from the list and re-create them in version 2. 
- Now I get a Nautilus Actions submenu when I right-click.

Hope this helps.

---

### Post by mastermindg on 2010-02-22
deb [http://ppa.launchpad.net/randomaction/ppa/ubuntu](http://ppa.launchpad.net/randomaction/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/randomaction/ppa/ubuntu](http://ppa.launchpad.net/randomaction/ppa/ubuntu) karmic main

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 498D2A12

FYI: There are currently NO nautilus-related packages on this ppa.

---

### Post by within on 2010-03-02
Hi there,

I have Karmic installed, with latest Nautilus actions version (2.29.4) and still can't get my new actions to appear in the context menu when I right click in Nautilus.

Since the version I knew of Nautilus Actions, many things changed.

Here is one action example I have (main screen + other options as "standards"):
[IMG]http://img189.imageshack.us/img189/6678/actions1.png[/IMG]
[IMG]http://img189.imageshack.us/img189/9982/actions2.png[/IMG]
+ folder tab has only *
+ conditions tab has * for files, */* for minetypes, both for selection content, and ticked "appears if..."
+ advanced conditions tab has local files selected only

Of course, the shred tool I call is installed.
But I see nothing in Nautilus menu...

One last strange thing: I did install the "open in terminal" package, which is in fact an action, but if it exists and works, it does not appear in nautilus Action configuration tool above...

Did I miss something?

Thanks in advance for your help,
within

---

### Post by Enigmapond on 2010-03-02
Here is how I did that and got the shred to show on nautilus I hope this helps. I'm using Jaunty  but it should work the same...

```
Add

Label = Shred

Path = /usr/bin/find

Parameters = %M -type f -exec shred -f -u -z '{}' \;

Conditions (files and folders) =   Both
Click ok and exit



in terminal type killall nautilus
```

Then I just rebooted and it was there.

Now this will only work, for some reason, on files only and it will leave the folders. Even if the parent directory has folders in it with files you want deleted, It will do only the files just great, albeit a slow depending on the file size, but leave the folders.

---

### Post by within on 2010-03-02
Thanks Enigmapond,

It really works this time.
I really don't see what's wrong with my settings, I just did follow some example given and working previously on Jaunty...

---

### Post by Enigmapond on 2010-03-02
Glad I could help! Your path setting I think had a lot to do with it not working. If you find a way for the folders to also be deleted, although not a big issue, post it..I've tried several variants with no success. When I added -d it kills everything in a directory...which is good in some cases but if you have, for example files on the desktop and you go to shred one, they will all go...:)

Cheers!;)

---

### Post by within on 2010-03-03
yes, thanks for your help, really.

You're probably right about the path, but to my defense, I'd say I followed what I did important. Indeed, I also have the Wipe action I did important for a file, and the path was 'just' the application name... of course, this one also does not work, so maybe the import was 'not enough'. I'll have a look.

Concerning folder, I'd read the -d 'should' delete the folder and contact, but with your desktop example, that can be tricky and/or terrible...

I really prefer to focus on files...

---

### Post by Tankerdog2002 on 2011-01-24
Enigmapond thank you.
I've been trying to figure out how to get shred to work in Ubuntu 10.04.
The trick was: killall nautilus

I used your parameters the first time with no success. Then I ran the "killall nautilus" command and "VOILA" Shred appeared in my menu.

---

