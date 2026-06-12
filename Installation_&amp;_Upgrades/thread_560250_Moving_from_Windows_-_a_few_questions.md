---
title: "Moving from Windows - a few questions"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by MikkyX on 2007-09-26
Hi all,
Just installed Ubuntu 7.04 Desktop DVD and I'm having a great time with it and I think I'm ready to move from Windows to Linux ALMOST full-time (aside from games - Steam won't behave so Windows remains my gaming OS for now) - just a few other things I want to query:

1) I used to do all my web development on Windows so I've got several mySQL databases I need to move to mySQL on Ubuntu - what's the best way to get data from Windows mySQL to Ubuntu?

2) What's a good code editor for Linux? Ideally it would have things like PHP / XHTML / CSS syntax highlighting and optionally function folding etc.

3) I need to get approximately three tons of e-mail from Thunderbird/Win to Thunderbird/Lin. I'd originally used MozBackup to back it all up but there's no version for Linux - what's the best way to go about this?

4) I have a Buffalo NAS mounted via smbfs as /media/network but I can't write files to it - I keep all of our music on this drive so how can I get read/write?

Any help appreciated - cheers! :)

---

### Post by dj Kalma on 2007-09-26
> **MikkyX said:**
> 1) I used to do all my web development on Windows so I've got several mySQL databases I need to move to mySQL on Ubuntu - what's the best way to get data from Windows mySQL to Ubuntu?

You could use mysqldump to create dumps of your databases in Windows and then import them in Linux.

---

### Post by straps on 2007-09-26
1) mysqldump

2) look at [Quanta Plus]("http://quanta.kdewebdev.org/index.php"), [Eclipse PDT]("http://www.eclipse.org/pdt/") and [Zend]("http://framework.zend.com/")

3) I'm no sure of this, made 100 backup of your emails :) ... Win and Lin store thunderbird data on the user personal folder as an hidden folder...on Linux thunderbird data is stored on /home/**USER**/.mozilla-thunderbird and in Windows it _should be_ stored on c:\Documents and Settings\**USER**\Application Data\Mozilla\Thunderbird...transfer all data should be a file copy operation but I'm not sure...Google for this

4) If you have mounted it with a command like:
```
sudo smbmount //server/share /media/network
```
you, as a simple user, cant write in it for permissions, but smbmount enable you to specify the user that will be the share owner, ie:
```
sudo smbmount //server/share /media/network -o uid=1000,gid=1000
```
uid and gid stands for UserID and GroupID that you can view from /etc/passwd
```
cat /etc/passwd
```

---

### Post by TNBY963 on 2007-09-26
Thunderbird is easy to migrate between operating systems or different computers. Just copy your whole profile folder in windows and paste it in your linux home folder. I do it all the time.
The path on Windows probably is: C:\Documents and Settings\<Windows login/user name>\Application Data\Mozilla\
and on Linux it's a hidden folder in your home folder (just turn on "show hidden folders" in nautilus) You should find it. 
Now be sure to start thunderbird first on Linux, because that creates the hidden folder. Then copy all the contents of the map which should have some weird name.default and paste them in your Linux map. make sure to only copy the contents of the folder, not the folder itself. 
If all this works you should have all your settings and even extensions.

I hope I make sense. English is not my primary language and for some strange reason I'm having difficulty explaining myself today :)

Greetz

Gert

---

### Post by MikkyX on 2007-09-26
Thanks to all for your replies :)

straps, I've got the drive mounted via /etc/fstab - can I just put those options in place of "defaults" or afterwards? I was trying to follow a guide I found somewhere (can't remember where now, it was at home and I'm at work) which gave a line to put in but when I used it and did sudo mount -a all the drive folder names showed up as M : x00e : x00n : x001 and so on - when I just use "defaults" it works but I can't write.

Regards Thunderbird, I'm running 2.0.0.6 on Windows but when I used Ubuntu to install it (apt-get install mozilla-thunderbird) I ended up with 1.5.0.something - is this going to cause problems and how easy would it be to upgrade to the latest ones?

Will give the suggestions everyone has made so far a try - thanks!

---

### Post by TNBY963 on 2007-09-26
thunderbird 2 runs on ubuntu, I'm using it right now. I don't think that your mail will be inaccessible if you move from 2.0 to 1.5 but your extensions might not work. And I could always be wrong and everything could get screwed up. I don't know
However, I installed it via automatix2, but there must be another method if you don't want to use automatix. Maybe search the forums for a how to?

Gert

---

### Post by LaRoza on 2007-09-26
> **MikkyX said:**
> 
2) What's a good code editor for Linux? Ideally it would have things like PHP / XHTML / CSS syntax highlighting and optionally function folding etc.


There is a sticky in the programming talk forum for Windows programmers (coders) coming to linux. It should help.

---

### Post by MikkyX on 2007-09-26
I'd forgotten about automatix! Uninstalling TB1.5 should be simple enopugh shouldn't it?

---

### Post by R.Bucky on 2007-09-26
Whatever happened to support of Notepad++. Granted, it is a .exe but it is in my opinion, the better syntax editor for web design. A good java version is also jEdit.

---

### Post by MikkyX on 2007-09-26
Just thought of another thing - my MSN messenger conversation histories - is there a Linux client which will work with those so I can keep them?

Thanks for all the help so far :)

---

### Post by MikkyX on 2007-09-26
Thanks for all the help so far all, I've almost managed a complete migration, there's just a few other things to sort out now:

1) When I log in my login screen is a little corrupt - I can still see what I'm doing but I think it's trying to display it in a resolution my monitor shouldn't support. This started when I installed the special ATI driver (fglrx?) in order for my widescreen monitor's 1440 x 900 resolution to be installed. Although when I look in the Restricted Drivers manager, there's no tickbox next to the ATI driver in question - is this normal?

2) My brother has a HP Deskjet F300 AIO connected to his Windows XP box and shared. I can connect to and install the printer from my machine via setting it up as a Samba shared printer, and Ubuntu configures it to use the hpjis driver, but when I send a document through to it (including the test page) the printer sits there as if it's about to start printing but never actually does. Any suggestions? I print a lot of letters so this is quite an important point to fix if possible - if not, I can leave them on the network drive (I got read-write working!) and he can print them for me.

Thanks again!

---

