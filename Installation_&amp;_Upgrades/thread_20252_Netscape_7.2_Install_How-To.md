---
title: "Netscape 7.2 Install How-To?"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by grenadier on 2005-03-15
Hi,

I am trying to install Netscape 7,2, something I have done previously, countless times.
After downloading  Netscape 7.2,  the script, **./netscape-installer** no longer works, at least, it doesn't in ubuntu.

As root no longer has a desktop in ubuntu, how on earth do I install applications in ubuntu? :x 

----------------

grenadier

---

### Post by cletusbaird on 2005-03-15
I would recommend going to the synaptic package manager  and select the Mozilla
Web Browser. 
It has all the features in found in Netscape 7.2.  Be sure and install
Mozilla Thunderbird Mail client as well. This is as simple as finding the package,selecting mark for install, and hitting apply . 
The whole mozilla suite is in the package selection and already installed on your computer no download or buggy thing to install.Its easy!!

In my earlier years, I used Netscape 7.2 because I liked the sky pilot theme.Then, I found out that all Netscape browsers since 6.2 came from the Mozilla Project and that they were equally as functional and often more reliable than the spin-off
Netscape Browser.

I know this does not specifically answer your post,but, I sincerely hope it helps.

some websites: [http://www.mozilla.org/](http://www.mozilla.org/)
[http://mozdev.org/](http://mozdev.org/)
[Http://www.betanews.com/](Http://www.betanews.com/)

---

### Post by wmcbrine on 2005-03-16
Yeah, Netscape is useless. AFAIK, the latest version is just Firefox (which you already have installed by default in Ubuntu), plus some ugliness and brokenness. It's dead, let it R.I.P.

root doesn't need a desktop. You can either use sudo, or open a Root Terminal from under Applications, System Tools. Note that the password you'll be prompted for is *your* password, not root's. This works because the first regular account created is placed in the admin group.

You can also make root live again by giving it a password. I dunno about a desktop (there's a separate option to unblock that), but anyway you can log in on a terminal then. I just use it to su from a regular terminal. But in retrospect, now that I understand the Ubuntu security model, I needn't have activated the root account this way.

Oh, and I'd suggest looking through packages in Synaptic before taking other approaches to adding software, just to keep the system tidy and easily upgradeable. Make sure you add the universe and multiverse repositories to increase the selection. (Netscape won't be there, though.)

---

### Post by grenadier on 2005-03-16
Thank's for the response guy's,

My preference is for Netscape 7.2.

I get this output when using the install script **./netscape-installer** ,

**./netscape-installer-bin: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory**


I still need to know how to install Applications as I have several to install, that are simillar to  the Netscape install script,

I already have given root a password.

Now I need to know how to unblock root's desktop. :sad: 


----------------------------
grenadier

---

### Post by std on 2005-03-16
Have you installed libgtk1.2 ?
It's been a while since I used Netscape and its netscape-installer. If you do have libgtk1.2 installed, my guess is that the installer is looking in the wrong place to find it and a symlink should solve this.
I have to hit the road to school right now, but I promise I'll try to look over the netscape-installer tonight to see what changed with it.

---

### Post by grenadier on 2005-03-16
Hi,

Netscape 7.2 installation solved.

The gtk Libraries were required and after installation via synaptic, the netscape install script worked as per usual. :lol:

---------------------------------
grenadier

---

### Post by themelvin on 2005-04-21
I have problems with installing Mozilla, it shows the same error:
```

./mozilla-installer-bin: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

Where do I get this libgtk1.2* file and how do I install it.

---

