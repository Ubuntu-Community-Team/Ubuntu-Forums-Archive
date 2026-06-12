---
title: "EasyFileSharing"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ikt on 2010-03-08
[https://wiki.ubuntu.com/EasyFileSharing](https://wiki.ubuntu.com/EasyFileSharing)
[https://blueprints.launchpad.net/ubuntu/+spec/easy-file-sharing](https://blueprints.launchpad.net/ubuntu/+spec/easy-file-sharing)

Is there any chance of seeing this being implemented/worked on?

At the moment I don't think file sharing is as easy as it could be.

---

### Post by ikt on 2010-03-11
bump

any reason why file sharing between linux and mac is recommended with smb?

---

### Post by rockin_goliath on 2010-03-11
I wouldn't know why smb is recommended for the Mac over others like sftp, which always worked great for me. I don't own a Mac myself, so take what I have to say with a grain of salt (or just try it out).

Although I haven't used it recently, I have had excellent luck with gnome-user-share (in the repositories), which creates an webdav server and makes is discoverable with Avahi, which should work with a Mac. 

For Ubuntu to Ubuntu sharing, you also might check out Giver (in the Karmic repositories). Never tried it out myself, but it always fascinated me.

Another thing you might try is just turning on the "link local" connections in your chat client of choice (I use Empathy), which will look for other people on the local network using Avahi, which might also be compatible with the Bonjour account feature for iChat.

At the very least, you can just install ssh (sudo apt-get install ssh) and you will be running an ssh server in seconds.

Hope that helps!

---

### Post by Morbius1 on 2010-03-11
I don't understand the original question. For some time now Ubuntu Gnome has had Nautilus-share. The user right clicks a folder and selects " share this thing" ( I'm paraphrasing ;) )

Works pretty much like "Simple Sharing" does on Windows. As for the Mac, it can see it in Finder without any modification on it's end.

---

### Post by bsmith1051 on 2010-03-11
I thought that the default Nautilus-share used Samba (Windows/SMB) protocol, which is the most commonly-used.  The problem, really, is that Ubuntu has not had 'sane' defaults for Samba and forced the user to dig into the advanced configuration to make anything work correctly.

If you try to share a folder (from it's right-click context menu) it will prompt you to install Samba, so that part is automated, at least.
______________

There's a new 'Personal File Sharing' option under Lucid's System > Preferences but it's not enabled by default, and it doesn't tell you what you need to do to enable it, either.  When I click on the Help button I get this:
> gnome-user-share uses a WebDAV server to share the Public folder, and advertises the share on the local network using mDNS
which is nicely detailed but doesn't directly tell you how to install 'gnome-user-share' via Synaptic (which I assume is what's needed).

---

### Post by Morbius1 on 2010-03-12
> **bsmith1051 said:**
> I thought that the default Nautilus-share used Samba (Windows/SMB) protocol, which is the most commonly-used.  The problem, really, is that Ubuntu has not had 'sane' defaults for Samba and forced the user to dig into the advanced configuration to make anything work correctly.

It does use Samba and if you read all the posts about connecting one machine to the other one would agree with your statement about "sane" samba defaults.

All I can tell you is I can get samba file sharing working out of the box - once samba is installed.

All of my workgroup names are different
Never had to set up lmhosts file.
Never had to install winbind
Never had to reconfigure any of the global options in smb.conf
No nsswitch, wins server, or any other kind of adjustment.

The only peculiarity I have found is a time delay when browsing for shares on my network - but that same phenomenon happens between Windows boxes in my network as well.

---

