---
title: "Konqueror &amp; Nautlius do not show all entries in root directory"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by maxxware on 2006-10-31
Since upgrading from Dapper to Edgy I notice the following strange behaviour by Nautilus and Konqueror. The problem is independent of the desktop environment chosen (the behaviour is the same whether I've logged on to KDE, Gnome or XFCE).

When I open Konqueror or Nautilusa nd browse to /, the following entries are shown:
/home
/media

The rest of the entries in the root-directory are missing... /tmp, /proc, /var, etc. are simply not shown.

When accessing the root-directory using Thunar (XFCE's browser) alle entries are shown.

Has anyone else seen this behaviour and found a soolution?

gr,
maxx
:wq!

---

### Post by maxxware on 2006-10-31
Sorry... this question was already posted in this forum, with the answer.

---

### Post by mandragor on 2006-11-01
Sorry for sounding like a dolt, but where? I couldn't find it..

---

### Post by albertran on 2006-11-01
Check your .hidden file.  Edgy defaults every folder except /home and /media to hidden.

---

### Post by Krusty Ruffle on 2006-11-06
> Check your .hidden file. I don't have one?? At least not in my home directory... <--dolp! I'm a moron...
Although, I could have sworn that I had already told it to show hidden things. I have to wonder though, why should all of this be hidden from me?? I will be hitting this with sudo rm /.hidden

---

### Post by joebrandt on 2006-11-10
The root directory (/) contains a file called /.hidden. Open this in a text editor and delete the names of the directories which you want to have shown.

Deleting the /.hidden link is not a permanent solution, as it will be restored during the next update of the kubuntu-desktop-setting package.

---

### Post by abovett on 2006-11-13
Just discovered this behaviour - have to say I'm of two minds as to whether it's a good idea. I for one will be immediately disabling the hiding of all items. Anyone know if emptying /etc/kubuntu-default-settings/hidden-root is a suitable (and permanent) method?

<rant>
I know we want to make linux easy for non-geeks, but this smacks of dumbing down and hiding things that should be discoverable. After all, if I'm looking in the root, presumably I'm interested in seeing what's actually going on. I think an easy way to switch between a "simple" view and the full view would have been far preferable.

It's sad to see this sort of thing happening in Linux. One of Microsoft's biggest mistakes with Windows was to try to mke things "easy" for users by hiding the truth of what's going on - always comes back to bite them in the end (I know - my job is to go pick up the pieces when the users get themselves in a total mess!).

Just my opinion, but I'd be interested to know who agrees with me.
</rant>

Andy B.

---

### Post by Sparken on 2006-11-16
I agree.

The Edgy version really made me look bad in front of
my Windozer friends.

Bragging about how Linux lets you configure almost everything
and doesn't hide things from you like Windows,
I had convinced some friends to try kubuntu. I have used 
Breezy since the get go and loved it. But my friends downloaded
the new Edgy and I soon received phone calls that baffled me.

"What do you mean you only see /home and /media?? Type / at the 
konqueror address bar...you STILL can't see the /etc folder??"

I finally did an install of Edgy myself and I had to apologize for 
putting my colleagues through the ordeal. It's bad enough that they
duct taped qtparted onto the text mode installer in a fashion so
counter-intuitive that a 9 year Linux veteran such as myself was 
stumped for 3 attempts. But hiding the root directory is just plain
against everything Linux stands for.

Maybe I haven't seen everything, but has anyone ever actually seen a forum
post from someone who accidentally deleted his /usr folder? 

I am quite disappointed with Edgy and I can't recommend it to people I like.:(

---

### Post by Nikos_M on 2006-11-19
I disagree.
There is some truth in that Linux should be as intuitive as possible but the hidden folders i think does not fall in the counter intuitive category.I think it is more a matter of taste and actually a nice feature.For example I have several accounts on the computer some of which are for people that have little to no experience on Linux.I think for them the whole idea of root account and root folder is confusing so the level of abstraction that the hidden folders provides is good. In fact the option of having a single file that sets the hidden files that is independent of the desktop environment you are using is quite nice (i would prefer to have also a customizable per user file and not only global file cause now i also have to suffer with hidden folders).

In the beginning the .hidden file was also a mystery for me but it didn't take but a simple search on the net to figure it out.No more than 30 sec to understand how to disable the hidden folders, so it wasn't that much of a trouble was it?

---

### Post by entangled on 2006-11-19
I think this idea of *silently* hiding folders *by default* is unhelpful to all users. 
The folders exist, some people want to browse them, some don't. In a file manager, why conceal them? And not document the fact?
If the system is to be specially configured for limited browsing then the .hidden mechanism seems OK, but the simplified mode at least needs to be indicated on screen, e.g. by a status icon, together with a UI to switch the mode.
p.s. the silent hiding presumably only applies to browsing, not file access?

---

### Post by entangled on 2006-11-19
I obviously missed the announcement about this so I am learning (?). 
Actually I am better disposed to this idea now. It only suppresses visibility of top-level directory names and icons in the file manager. If you type in a URI of /etc you can browse in file manager without restriction under that level. It doesn't affect command line navigation.
If you change an entry in .hidden it takes effect only after you restart the file manager. You do not need to remove an entry, just comment with a #.
This is a useful de-clutter for top level browsing and doesn't really inhibit those who know where to go.

---

### Post by abovett on 2006-11-19
I am still not too keen on the idea (see my earlier post!) but I have moderated my views a little as I have now realised that the "Show Hidden Files" option in Konqueror does reveal the hidden directories in the main pane (though not unfortunately in the directory tree as far as I can tell). My main concern was that the directories were not "discoverable" by less knowledgable users, but as that option is fairly visibible in Konqueror and does reveal them that does satisfy some of my concerns. Not sure if the same applies to Nautilus (haven't tried it on a Ubuntu (Gnome) system yet). 

I don't mind "de-cluttering" as long as the mildly curious can still find things easily. In my business I spend a lot of time explaining the basics to non-technical computer users (mostly Windows users, it must be said), and their lack of basic knowledge is astonishing. Part of the reason is that the systems they work with tend to over-simplify to the extent that they lose touch with what they are actually doing and never learn.

Andy B

---

### Post by Splodgi on 2006-11-27
I have just installed Kubuntu 6.06. I already have FC6 on another machine and this is my main machine. I do not mind hidden existing if and only if there is a way to make Konqueror remember so I don't have to edit the hidden file every time I start up Konqueror. Does anyone know if this is possible. If it isn't then it is stupid and totally unacceptable. Some kinky people like being dressed up in nappies with a dummy and being burped by a nanny even though they are middleaged. I don't fancy my OS doing that to me at all.:evil: :evil:

---

### Post by Sparken on 2006-12-03
Splodgi: The hidden file in question is in the root dirrectory and it is named ".hidden". Once you edit it, it seems to stay that way so you only have to edit it once.

My previous comment about the "unintuitive" part was specifically aimed at the installation routine, sorry to mix posts.

As for the .hidden upper level directories, maybe they should have done in a manner such as what entangled was eluding to. Put some kind of icon or indicator to let you know what is going on and/or a simple method to get around it. Make this a per user feature and make root or sudo exempt.

The method used is rather unique to this distro as far as I can tell. I would think that you would at least want to publicize this feature a bit more. 

When I am giving tech support via phone to a user who has just decided to install edgy and I tell him to do a ">sudo konqueror" and tell him to go to /etc directory and he tells me it isn't there... well that's a bad practical joke IMO. I can't very well surf around to find the answer when I am in the middle of a 2 hour commute and he certainly can't because his network isn't configured properly and he is telling me there is no /etc or /var/log directories.

If I am root or sudo, I bloody well expect to be able to see the upper level directories.

---

### Post by Katsujinken on 2006-12-03
Damn.

This seems way, way, WAY out of kilter for Linux to me. 

I've only been using GNU/linux & FreeBSD for six or seven years,
and still consider myself a neophtye, but, c'mon, seriously folks,
HIDDEN directories? Where's the punchline? No warning? No simple
text screen to *suggest* that this may be the case? Seems to me
that a straightforward FreeBSD installer gives one more info and
doesn't hide directories. I love the ease with which one can
install with ubuntu, but why would it have to exclusively appeal to
the lowest common denominator? :confused:

---

### Post by Nikos_M on 2006-12-15
> **Sparken said:**
> Splodgi: The hidden file in question is in the root dirrectory and it is named ".hidden". Once you edit it, it seems to stay that way so you only have to edit it once.

My previous comment about the "unintuitive" part was specifically aimed at the installation routine, sorry to mix posts.

As for the .hidden upper level directories, maybe they should have done in a manner such as what entangled was eluding to. Put some kind of icon or indicator to let you know what is going on and/or a simple method to get around it. Make this a per user feature and make root or sudo exempt.

The method used is rather unique to this distro as far as I can tell. I would think that you would at least want to publicize this feature a bit more. 

When I am giving tech support via phone to a user who has just decided to install edgy and I tell him to do a ">sudo konqueror" and tell him to go to /etc directory and he tells me it isn't there... well that's a bad practical joke IMO. I can't very well surf around to find the answer when I am in the middle of a 2 hour commute and he certainly can't because his network isn't configured properly and he is telling me there is no /etc or /var/log directories.

If I am root or sudo, I bloody well expect to be able to see the upper level directories.


Totally agree with you. I have already stated that the feature should be publicised so that people know who and what is causing hidden folders.But as I said it is a feature not a bug, so treat it as one and you ll see that it is quite usefull(especially if you want to introduce the system to someone that is new to linux).

Besides.... who on earth is launching konqueror as root!? :)

---

### Post by Richard Steven Hack on 2007-02-22
I just installed Kubuntu 6.10 for a client today.

Do you people have ANY idea how STUPID one looks to a client when you don't even know that you can't reach the system directories?

This is UTTERLY unacceptable.

This is equivalent to the STUPID Windows practice of "hide system files", hide extensions, hide this, hide that.

Linux is about FREEDOM - freedom to go where you want and screw up what you want.

Kubuntu is no longer acceptable for me to recommend to clients.

First it was the utterly non-standard and STUPID dumbing down of root access, and now this.

Sorry, Ubuntu and Kubuntu are OUT OF HERE.

What's next? CLIPPY? THE WINDOWS SEARCH DOG?

---

### Post by abovett on 2007-02-26
> **Richard Steven Hack said:**
> I just installed Kubuntu 6.10 for a client today.

Do you people have ANY idea how STUPID one looks to a client when you don't even know that you can't reach the system directories?
Maybe you should make sure you are familiar with the software yourself before you try to install it professionally? This feature is well known by now and easy to work around. Turn on access to hidden files and they all appear.
> This is UTTERLY unacceptable.
I little strong - I find it a little irritating but I can see the point - just because it doesn't work the way you want it to doesn't make it "UTTERLY unacceptable".
> This is equivalent to the STUPID Windows practice of "hide system files", hide extensions, hide this, hide that.
 I don't like "hide extensions" in Windows because it doesn't really work - causes various knock-on problems - but keeping things you don't want to see out of the way is not such a bad idea generally.
> Linux is about FREEDOM - freedom to go where you want and screw up what you want.
Huh?! I'd prefer my customers _not_ to screw up their systems, thank you very much! You haven't lost any freedom - the files are still easily accessible if you want them to be - but most average users never will.
> Kubuntu is no longer acceptable for me to recommend to clients.
Have you asked _them_ if they like the feature?
> First it was the utterly non-standard and STUPID dumbing down of root access, and now this.
If you mean using sudo - I rather like it. Still easy to get to root when you need it (sudo -s instead of su) and is simpler for everyday users without compromising system security.
> Sorry, Ubuntu and Kubuntu are OUT OF HERE.
Your choice of course, but I'm sticking with it, thanks :)

---

### Post by r.stiltskin on 2007-03-12
> **Richard Steven Hack said:**
> I just installed Kubuntu 6.10 for a client today.

Do you people have ANY idea how STUPID one looks to a client when you don't even know that you can't reach the system directories?

This is UTTERLY unacceptable.

This is equivalent to the STUPID Windows practice of "hide system files", hide extensions, hide this, hide that.

Linux is about FREEDOM - freedom to go where you want and screw up what you want.

Kubuntu is no longer acceptable for me to recommend to clients.

First it was the utterly non-standard and STUPID dumbing down of root access, and now this.

Sorry, Ubuntu and Kubuntu are OUT OF HERE.

What's next? CLIPPY? THE WINDOWS SEARCH DOG?

Your response is a bit extreme but I share your irritation.

Ubuntu is essentially an excellent distibution, good enough to make it worthwhile dealing with the silliness of having to individually install those non-free drivers, codecs, and programs that most of us use.  I can understand that there are legal reasons the developers don't build those in.

But it's completely ridiculous that we should have to waste an hour figuring out how to restore functionality that's built into the application.  Why do the devs feel that they have to impose "parental controls" on what we can see, so that only those users who are sufficiently motivated get the full, free use of the software.

If these restrictions are such a good idea, make them a clearly DOCUMENTED option in the installation process.

I'll continue to use it and thank the developers for their efforts.  But they should also be aware that "features" like this are really, REALLY annoying.

---

