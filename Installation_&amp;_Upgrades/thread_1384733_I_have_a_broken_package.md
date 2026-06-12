---
title: "I have a broken package?"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by 006ruler on 2010-01-18
Hi, I have been looking on these forums to get some help with my broken package warning. Often, when i try to install something, it says that i have a broken package. Ive run the synaptic thing and that thing that you can do with the terminal, but it still says something is broken. Can i get some help?

---

### Post by blackened on 2010-01-18
Post the output of

```
sudo apt-get install -f
```

---

### Post by 006ruler on 2010-01-18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgstreamer-plugins0.8-0 gstreamer0.8-oss libwavpack0 gstreamer0.8-x
  libgstreamer0.8-0 libswfdec0.3 libmad0 gstreamer0.8-misc gstreamer0.8-swfdec
  libgstreamer-gconf0.8-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by Sef on 2010-01-18
System > Administration > Synaptic Package Manager > Edit > Fix Broken Packages

---

### Post by blackened on 2010-01-18
Umm, I don't see anything wrong apart from that you have some packages that aren't being used anymore and can be removed with 
```
sudo apt-get autoremove
```

---

### Post by 006ruler on 2010-01-18
woops, sory blackened for sending the message- it looked like no one had repleid. But i still have some broken package somewhere.

---

### Post by blackened on 2010-01-18
> **006ruler said:**
> ...But i still have some broken package somewhere.

What makes you think that? Exactly where is the system telling you that you have a broken package? In the Upgrade Manager?

---

### Post by 006ruler on 2010-01-18
System>Administration>Hardware drivers. I have not yet activated the driver on that. I try to activate that, and heres what it says:
SystemError: E:Unable to correct problems, you have held broken packages.

also, when i try to install things from the synaptic software thing, it says that it cant due to broken packages.

---

### Post by 006ruler on 2010-01-18
...
...
...
CCCRRRAAAAPPPPPPPPPP!!!!!!!!!!!!!!!!
OH< S**T!!!
aparently, i deleted the Ubuntu Desktop. Im guessing thats REALLY important. i think that may be why it all got messed up. So i tried to reinstall it, and wadia know? it has about 100 dependants. And none of them will download because i dont have the Ubuntu Desktop.

...
is there a way to just reset the entire thing to go back to when i first started ubuntu?

or an easy way to reinstall?

---

### Post by 006ruler on 2010-01-18
hello?
please tell me your not all laughing your heads off...

---

### Post by blackened on 2010-01-18
> **006ruler said:**
> hello?
please tell me your not all laughing your heads off...

Can't say I've ever really been much for finding humor in others' misfortunes.

What way did you try to reinstall the ubuntu-desktop package? Post the output of

```
sudo apt-get install ubuntu-desktop
```

---

### Post by 006ruler on 2010-01-18
The desktop is responsable for all downloads, so nothing could be done. How do you uninstall Ubuntu? Ill be reinsalling it


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: deskbar-applet but it is not going to be installed
                  Depends: ekiga but it is not going to be installed
                  Depends: foomatic-db-hpijs but it is not going to be installed
                  Depends: gimp-print but it is not going to be installed
                  Depends: gnome-btdownload but it is not going to be installed
                  Depends: gnome-cups-manager but it is not going to be installed
                  Depends: gnome-volume-manager but it is not going to be installed
                  Depends: gok but it is not going to be installed
                  Depends: gthumb but it is not going to be installed
                  Depends: hal-device-manager but it is not going to be installed
                  Depends: hwdb-client but it is not going to be installed
                  Depends: irssi but it is not going to be installed
                  Depends: nautilus-cd-burner but it is not going to be installed
                  Depends: openoffice.org but it is not going to be installed
                  Depends: powermanagement-interface but it is not going to be installed
                  Depends: python-adns but it is not going to be installed
                  Depends: python-cddb but it is not going to be installed
                  Depends: python-clientcookie but it is not going to be installed
                  Depends: python-egenix-mxproxy but it is not going to be installed
                  Depends: python-egenix-mxstack but it is not going to be installed
                  Depends: python-egenix-mxtexttools but it is not going to be installed
                  Depends: python-egenix-mxtools but it is not going to be installed
                  Depends: python-epydoc but it is not going to be installed
                  Depends: python-eunuchs but it is not going to be installed
                  Depends: python-examples but it is not going to be installed
                  Depends: python-gd but it is not going to be installed
                  Depends: python-genetic but it is not going to be installed
                  Depends: python-geoip but it is not going to be installed
                  Depends: python-htmlgen but it is not going to be installed
                  Depends: python-id3lib but it is not going to be installed
                  Depends: python-imaging-sane but it is not going to be installed
                  Depends: python-jabber but it is not going to be installed
                  Depends: python-ldap but it is not going to be installed
                  Depends: python-mysqldb but it is not going to be installed
                  Depends: python-netcdf but it is not going to be installed
                  Depends: python-numeric but it is not going to be installed
                  Depends: python-pexpect but it is not going to be installed
                  Depends: python-pgsql but it is not going to be installed
                  Depends: python-pisock but it is not going to be installed
                  Depends: python-pyao but it is not going to be installed
                  Depends: python-pylibacl but it is not going to be installed
                  Depends: python-pyvorbis but it is not going to be installed
                  Depends: python-reportlab but it is not going to be installed
                  Depends: python-simpletal but it is not going to be installed
                  Depends: python-syck but it is not going to be installed
                  Depends: python-unit but it is not going to be installed
                  Depends: python-xmpp but it is not going to be installed
                  Depends: python2.4-dbus but it is not going to be installed
                  Depends: python2.4-libxml2 but it is not going to be installed
                  Depends: python2.4-libxslt1 but it is not going to be installed
                  Depends: serpentine but it is not going to be installed
                  Depends: slocate but it is not going to be installed
                  Depends: ttf-arphic-ukai but it is not going to be installed
                  Depends: ttf-arphic-uming but it is not going to be installed
                  Depends: x-window-system-core but it is not going to be installed
E: Broken packages

---

### Post by blackened on 2010-01-18
Ack. That's not good. No need to uninstall, just make sure you overwrite the existing partitions when you go to reinstall.

---

### Post by amber21 on 2010-01-19
Hi
I am not so sure I know the right protocol about making a rude interruption in a conversation - so please excuse me. 
I am using Ubuntu Karmic in my desktop and Jaunty in my Laptop. Recently I am unable to update my Karmic - update manager gets stuck on Building dependency. I was reading this thread and took a cue and did sudo apt-get install -f
It says:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Please tell me what I can do now?
Thanks

---

### Post by blackened on 2010-01-19
> **amber21 said:**
> Hi
I am not so sure I know the right protocol about making a rude interruption in a conversation - so please excuse me.

What you're referring to is impolitely called thread-hijacking.

Please begin a new thread with a title that adequately describes your problem(s) so that others can direct their advice to your particular issue.

---

### Post by amber21 on 2010-01-28
Thanks for the advice. i shall start a new thread

---

### Post by 006ruler on 2010-01-28
Oh, sorry for not responding back, the problem has been fixed. I just had a bit of a problem with some kind of net sencor wear that doesn't like peer-too-peer, but its all good now. Thank you all so much for you help!!

---

