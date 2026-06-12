---
title: "vlc : video screen and interface stay in separates windows"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by broussaille on 2009-02-24
/ I'm French, i hope you will understand my explanation/

Hi,

In VLC (0.9.8a) the 'screen windows' is dissociated from the interface of control (with play, stop, open...), and this interface is no more apparating in full screen mode with mouse gesture.

I selected all usual settings to join the 2 windows, and make the interface appear in full screen. 
To be sure, I compare with settings in VLC 0.9.4 (Intrepid) in an other computer.

The same problem had existed in VLC 0.9.4 (Intrepid) around october 2008. It was considerated as a bug, but it have been fast solved. 

We're at least 2 french people with the same problem, and no one deny : 
[http://forum.ubuntu-fr.org/viewtopic.php?id=297068](http://forum.ubuntu-fr.org/viewtopic.php?id=297068)

I hope someone will understand my words, hard for me to do better ^^

Have you the same problem?
If anyone thinks it's really a bug, can he report it with a best explanation?

Thanks!

Edit : have wrotten Gusty instead of intrepid... Sorry, i was tired

---

### Post by zekopeko on 2009-02-24
same here. report the bug and link it to this thread so that me (and anyone else affected) can track it.

---

### Post by broussaille on 2009-02-24
I have report, i hope i do it well

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/334110](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/334110)

---

### Post by obscur156 on 2009-02-24
+1  Same for me here

---

### Post by rogerdean on 2009-02-25
same story here...

---

### Post by taavikko on 2009-02-25
> **broussaille said:**
> I have report, i hope i do it well

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/334110](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/334110)

It was reported already, so I marked it as a duplicate, thanks anyway :)
Always a good idea to try search existing bugs...

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038)

---

### Post by Kow on 2009-02-25
This bug seems to have been reintroduced since I think it was either intrepid or hardy....

---

### Post by taavikko on 2009-02-25
> **Kow said:**
> This bug seems to have been reintroduced since I think it was either intrepid or hardy....

It was in intrepid, reported by me...

Just hang tight, it should come through eventually..

---

### Post by broussaille on 2009-02-25
Ok, thanks evertbody for your efforts.

---

### Post by Sand &amp; Mercury on 2009-02-25
Same behavior for me too.

---

### Post by taavikko on 2009-02-25
> **Sand & Mercury said:**
> Same behavior for me too.

Yep, everyone who installed through multiverse is affected.

---

### Post by misterbeetz on 2009-03-14
+1 for me as well.  I'm glad the issue is being worked on.

---

### Post by ubu-for on 2009-03-14
I think it's not a bug, because VLC for Windows and Mac has also two separate windows.

But I have to say that I would prefer the classic look, too.

---

### Post by Darkshade on 2009-03-14
> **ubu-for said:**
> I think it's not a bug, because VLC for Windows and Mac has also two separate windows.

But I have to say that I would prefer the classic look, too.

I'm pretty sure it is, since there's actually an option to embed the video in the main interface and it does not make any change. It used to though.

---

### Post by noworry on 2009-03-15
Same problem here in Kubuntu Jaunty !
Is there any temporary fix till the fixed package is released ?

Thanks a lot...

---

### Post by mc4man on 2009-03-18
> Is there any temporary fix till the fixed package is released ?
I doubt there will ever be a 'fix' in any 0.9.x version (there has been in 1.0 though several other things are currently broken

The 'fix' for 0.9.x is to enable the embedded video in the source before building. If you build it yourself it's quite simple, a line needs to be replaced in /modules/gui/qt4/qt4.cpp

The are several launchpad ppa's that offer a 'patched' 0.9.8a for jaunty
here's one
[https://launchpad.net/~medigeek/+archive/ppa/](https://launchpad.net/~medigeek/+archive/ppa/)

a short discussion about
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038)

It's really a matter of choice, vlc considers it broken though many debian users never suffer any ill effects



The section if you build (at or around 216
orig.
```
#if 0
    add_submodule();
        set_capability( "vout window", 50 );
        set_callbacks( WindowOpen, WindowClose );

```
replaced
```
#if !defined (Q_WS_X11) || defined HAS_QT43
    add_submodule();
        set_capability( "vout window", 50 );
        set_callbacks( WindowOpen, WindowClose );
```

---

### Post by jesterthejedi on 2009-03-23
Works brilliantly, many thanks :)

---

### Post by Joe_Bishop on 2009-03-23
I can't find any reason to use vlc as media player now - only network streams.
Totem is much better for hd (lol, it's even better than repository mplayer), supports dvd menu. Choose right deinterlacing method.

---

### Post by ubu-for on 2009-03-24
Now I've added the [PPA for VLC](https://launchpad.net/~c-korn/+archive/ppa) to my source.list and signed it with the public key, but Synaptic can't find any newer VLC version.

Thanks in advance for every hint!

---

### Post by biasquez on 2009-03-24
NEWS: compiling git version of vlc (1.xxx) this problem is solved!

---

### Post by jesterthejedi on 2009-03-31
You need to do this after "sudo apt-get update" do "sudo apt-get install vlc" in your terminal.

---

