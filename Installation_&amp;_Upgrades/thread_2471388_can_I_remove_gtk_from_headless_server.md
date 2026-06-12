---
title: "can I remove gtk from headless server?"
date: 2022-01-28
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2022-01-28
Can I remove gtk packages from a headless server?

```
$ sudo apt list --installed | grep gtk

libfm-gtk-data/impish,now 1.3.2-1 all [installed]
libgtk-3-common/impish,now 3.24.30-1ubuntu1 all [installed]
libgtk2.0-common/impish,now 2.24.33-2ubuntu1 all [installed]
libjavascriptcoregtk-4.0-18/impish-updates,impish-security,now 2.34.4-0ubuntu0.21.10.1 arm64 [installed]
```

---

### Post by MAFoElffen on 2022-01-28
What is your goal? To be a headless, console only server?

---

### Post by Tadaen_Sylvermane on 2022-01-29
Run this command but don't hit the Y at the end. This will give you a list of everything that needs them in some way. I'm sure there is a better way to get this list.

```
apt --purge autoremove [COLOR=#000000][FONT=&amp]libfm-gtk-data [/FONT][/COLOR][COLOR=#000000][FONT=&amp]libgtk-3-common [/FONT][/COLOR][COLOR=#000000][FONT=&amp]libgtk2.0-common [/FONT][/COLOR][COLOR=#000000][FONT=&amp]libjavascriptcoregtk-4.0-18[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp]

This is one of the reasons I switched to Debian where possible, no offense to Ubuntu of course. If I want to install Xfce I get Xfce. Not Xfce + the whole Gnome stack. If I want Seahorse but not the rest of Gnome I can do that too. I'm sure there are reason's Canonical messed with the dependencies like they did but that is above my pay grade.[/FONT][/COLOR]

---

### Post by bjlockie on 2022-01-30
> **MAFoElffen said:**
> What is your goal? To be a headless, console only server?

 I have a headless console only server.
I don't have enough ram to run a GUI so I wondered if I can delete those gtk packages.

---

### Post by bjlockie on 2022-01-30
> **Tadaen_Sylvermane said:**
> Run this command but don't hit the Y at the end. This will give you a list of everything that needs them in some way. I'm sure there is a better way to get this list.

```
apt --purge autoremove [COLOR=#000000][FONT=&amp]libfm-gtk-data [/FONT][/COLOR][COLOR=#000000][FONT=&amp]libgtk-3-common [/FONT][/COLOR][COLOR=#000000][FONT=&amp]libgtk2.0-common [/FONT][/COLOR][COLOR=#000000][FONT=&amp]libjavascriptcoregtk-4.0-18[/FONT][/COLOR]
```[COLOR=#000000][FONT=&amp][/FONT][/COLOR]

```
$ sudo apt --purge autoremove libfm-gtk-data libgtk-3-common libgtk2.0-common libjavascriptcoregtk-4.0-18
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  libfm-gtk-data* libgtk-3-common* libgtk2.0-common* libjavascriptcoregtk-4.0-18*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 25.6 MB disk space will be freed.
Do you want to continue? [Y/n]
```

---

### Post by Tadaen_Sylvermane on 2022-01-31
Looks like they won't hurt to remove then. After a good while managing a system you get a feel for what packages need to be there vs what shouldn't. Nothing jumps out at me with that list as they are just libs without any programs that depend on them it seems.

I take no responsibility for my advice in this case but I think it's a safe bet.

---

### Post by MAFoElffen on 2022-01-31
> **Tadaen_Sylvermane said:**
> 
I take no responsibility for my advice in this case but I think it's a safe bet.


Agreed in the way you worded that... LOL. What makes me wary is the background scenario of this. My hesitancy is that no matter if it is there or if it is removed, they are "not use", they are not using memory.

It is a headless server, that is not using a GUI. He says it's RAM is limited, but didn't say how much is actually has installed, what job it has (hosted services), etc.

In the past, I could run a headless in 128 to 256 GB and not worry. But 20.04.3 uses a bit more, especially in the install stage. There are ways to tune things, depending if you are runnin reports and audits to see what is is doing and how close it gets to machine limits. That is going to be important, especially since headless. 

It needless to be able to scream for help to something... Does that make sense?

If you want just to ensure that you had no GUI, and that a GUI would not start... There are  other ways to ensure that. Just saying. Even with uninstalling those packages, which I initially see no harm, there are other things that you can do also.

If you just wanted to make sure that the OS install had no piece of a GUI:
```

sudo apt install ubuntu-server

```
Would remove any GUI support, and make sure it was configured for server services. That is how you change a Desktop Edition into a Server Edition...

Another thing to look at in audits, is paging... It's use, it's size, where it runs from.

---

### Post by bjlockie on 2022-01-31
> **MAFoElffen said:**
> .It is a headless server, that is not using a GUI. He says it's RAM is limited, but didn't say how much is actually has installed, what job it has (hosted services), etc.


1 GB.
I guess I can leave it since it doesn't use ram and I have lots of storage.

---

