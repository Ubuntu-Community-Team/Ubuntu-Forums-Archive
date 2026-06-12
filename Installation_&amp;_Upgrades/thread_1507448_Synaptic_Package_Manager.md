---
title: "Synaptic Package Manager"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by sansa90 on 2010-06-11
When I try to open Synaptic Package MAnager, a dialouge box comes up stating that and error ocured, the sais this:

E:Malformed line 58 in source list /etc/apt/sources.list (dist parse)
E:The list of sources could not be read.
Go to the re3pository dialoge to correct the problem.
E:_cache->opne()failed, pleas report.

What should I do?

---

### Post by QIII on 2010-06-11
Have you added, deleted or modified any of the entries in your sources.list, particularly manually through a text editor?

Can you open sources.list and cut and paste line 58?

---

### Post by sansa90 on 2010-06-12
So, i found a code I recently used from a website to download DockbarX. Here is what I used. 
sudo sh -c "echo 'deb [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu) YOUR_UBUNTU_VERSION_HERE main' >> /etc/apt/sources.list"

I substituted YOUR_UBUNTU_VERSION_HERE with intrepid like it said to do. What do you think I should do to correct this problem??? PS, it wount allow me to open synaptic or the update manager

---

### Post by drs305 on 2010-06-12
Sansa, 

Welcome to the Ubuntu forums.

As QIII requested, post your sources.list. 
```
gksu gedit +58 /etc/apt/sources.list
```
If you aren't familiar with terminal commands, to open a terminal go to Applications, Accessories, Terminal. When you enter the command above, you will be asked for your password. Just type it in and press enter.

This will open a root editor on the line that is bad. Copy the entire contents here and we can take a look at it.  
When you paste the entry into a new post, press the # icon in the post's menu. This will generate "code" tags. Pasting large partions of text between the code tags makes your inputs more readable.

---

### Post by sansa90 on 2010-06-12
[COLOR=Magenta]deb [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu) intrepid[/COLOR]

This is for line 48, not 58, because I accidentaly typed in 58. anyways, this is the right one, but the code i entered for the DockbarX is line 49, so ill include it just in case. 

[COLOR=Magenta]deb [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu) YOUR_UBUNTU_VERSION_HERE main[/COLOR]

---

### Post by drs305 on 2010-06-12
Edit: As I made this post I was thinking your signature line said you were currently using Lucid - must have been another post I was working on. If you are using Karmic or Lucid, the following commands will work (except substitute "karmic" in the example of what was added). If you are using an earlier version, let us know which one it is. If you really are using Intrepid, none of the normal Ubuntu repositories will work as it is no longer supported so you would most likely be getting other errors as well.

Remove the entries referencing DockbarX and let Ubuntu add the entry automatically (if you are using Karmic or Lucid). 

By running the following commands, the correct repository information and security key will be imported into your lists. The information won't actually go into /etc/apt/sources.list, but in a file in the /etc/apt/sources.list.d folder (where ppa information is normally stored). 

```
sudo add-apt-repository ppa:dockbar-main && sudo apt-get update
```

As a note, here is the format of the repository that will be added:
> 
deb [http://ppa.launchpad.net/dockbar-main/ppa/ubuntu](http://ppa.launchpad.net/dockbar-main/ppa/ubuntu) lucid main


If you would like to learn more about repositories, you can view the Ubuntu community doc here:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

If you want to stick with the command line, you can install it with:
```
sudo apt-get install dockbarx
```

Also note that this is still considered 'experimental' by Ubuntu and is not included in the normal repositories. This means that it has not been tested and received the 'blessing' of Ubuntu.

---

### Post by sansa90 on 2010-06-12
THANK YOU SO MUCH! I'll definately look into it and post any questions I have on these forums. Again, Thanks so much.

---

