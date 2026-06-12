---
title: "Jaunty 64bit"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Lazy-buntu on 2009-04-12
I took the plunge and installed 9.04 beta 64bit with ext4.

I'm working on re-setting up my computer. I was wonder where the blacklist is now? I do ```
sudo gedit /etc/modprobe.d/blacklist
``` and I get a blank text file. Note: I want to blacklist that annoying pcspkr.


Also, I want to install extra repos like Medibuntu and some others from: [http://blog.ibeentoubuntu.com/2009/03/extra-repositories-for-ubuntu-810-you.html](http://blog.ibeentoubuntu.com/2009/03/extra-repositories-for-ubuntu-810-you.html)

Would I still add this line to the software sources? ```
deb http://packages.medibuntu.org/ intrepid free non-free
```

---

### Post by drs305 on 2009-04-12
On my install of jaunty there is an /etc/**modprobe**/blacklist.conf. In my hardy install it is /etc/**modprobe.d**/blacklist but the contents are more or less the same.

2. It looks like there is a jaunty repo, so change *intrepid* to *jaunty*
This is in my /etc/apt/sources.list.d/medibuntu.list
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

---

### Post by Lazy-buntu on 2009-04-12
> **drs305 said:**
> On my install of jaunty there is an /etc/modprobe/blacklist.conf. In my hardy install it is /etc/modprobe.d/blacklist but the contents are more or less the same.

2. It looks like there is a jaunty repo, so change *intrepid* to *jaunty*


Thanks, I'll try that.

edit: You're the man! All I needed to do was add the .conf to the end.

---

### Post by connorh123 on 2009-04-12
Do you guys have trouble with sound?
Or have you fixed it?
I have problems running sound on Youtube and games I try to play, which makes it useless unless I solve this problem.

---

### Post by fooman on 2009-04-12
> **Lazy-buntu said:**
> 

...Would I still add this line to the software sources? ```
deb http://packages.medibuntu.org/ intrepid free non-free
```

no,  run the following command in a terminal to add the jaunty repos to your sources:

```
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.listthen
``` then get the gpg key with this command:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```hope that helps.

---

### Post by Lazy-buntu on 2009-04-12
Thanks guys, and to the guy above: my sound works fine.

---

### Post by Lazy-buntu on 2009-04-12
From [http://blog.ibeentoubuntu.com/2009/03/extra-repositories-for-ubuntu-810-you.html](http://blog.ibeentoubuntu.com/2009/03/extra-repositories-for-ubuntu-810-you.html)

I added medibuntu, wine, vlc, compiz, and open office (replacing "intrepid" with "jaunty"). Is it safe to say that that's what the repository is?

How do I know it worked and where can I get the public jaunty keys or whatever the update manager bothers you about?

---

### Post by drs305 on 2009-04-12
If you got them, then it worked.

Medibuntu just went to a single command entry for adding the repo and keyring. It identifies what you are running and does the entire thing, including importing the keys, in one sequence. If you already have it correctly set up you can still do this and it won't hurt anything if you still have doubts about what you have done so far:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```

It's from here:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Lazy-buntu on 2009-04-12
So if it got added, then it is a repo? I.E. if I added [http://myfakeubunturepo.org](http://myfakeubunturepo.org), it would tell me I'm full of crap?

---

### Post by Lazy-buntu on 2009-04-12
Unrelated question: if I want to install KTorrent, do I need to install all of the KDE packages?

On my old install I had all three desktop environments (KDE, Gnome, and XFCE). I loved KTorrent, but I don't want any other desktop environment other than Gnome.

---

### Post by drs305 on 2009-04-12
Yes, you will need the associated dependencies.

If you use synaptic it will show you what additional programs are going to be installed. There is a section in synaptic where you can specify whether or not you want to install *recommended* packages (Settings, Preferences, General).

Using the command line for the install it will show you how much you have to download and how much space will be taken up after in the install (for ktorrent, on my system, 150MB). It will then wait for you to indicate Y or n.  There are options to apt-get to allow you to bypass recommended packages to reduce the number/size of the download. You can see the options with "man apt-get".

---

### Post by Lazy-buntu on 2009-04-12
I figured :(

In my opinion KTorrent is so much better than Transmission or Deluge, so I may go install that later. The only thing I didn't like before was my splash thing and a few other things I had to go back and fix.


Anyway, so what about the repos? 

> If you got them, then it worked.

> So if it got added, then it is a repo? I.E. if I added [http://myfakeubunturepo.org](http://myfakeubunturepo.org), it would tell me I'm full of crap?

---

### Post by drs305 on 2009-04-12
You can put anything you want in sources.list. The format is normally:  
deb server version component
For instance:
deb [http://www.gtlib.gatech.edu/pub/ubuntu/](http://www.gtlib.gatech.edu/pub/ubuntu/) jaunty universe main 

However, the server must be set up a certain way and you just can't put any website address in sources.list and expect it to work. So in answer to your question, you would get an error message - most likely a 404 error saying the server couldn't be found. There are other error messages as well.

For servers which do have deb packages but are not part of the official repositories, you have to make a decision about how much you trust them. The packages may not have been tested with ubuntu and security is an issue to be considered.

You can read more about repositories here:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by lavinog on 2009-04-12
> **Lazy-buntu said:**
> I figured :(

In my opinion KTorrent is so much better than Transmission or Deluge, so I may go install that later. The only thing I didn't like before was my splash thing and a few other things I had to go back and fix.


Just curious, but what is missing in Transmission/Deluge?
I haven't used KTorrent yet, but I noticed that there were some changes in Transmission for Jaunty.

---

