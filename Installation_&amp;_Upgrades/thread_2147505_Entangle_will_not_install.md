---
title: "Entangle will not install"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by Janno2 on 2013-05-22
I'm quite a newbie in Linux-land, sorry.

I did add the get-deb repository, and tried to install entangle.
This seemed to go well, but the package is not installed.
So I used "sudo apt-get install entangle" again
And got back (translated from Dutch, sorry for the bad English):
"Packet-lists are reading in...Ready"
"Tree of dependencies (?) is building"
"Status infrmation is read.. Ready"
"Some packages could not be installed. This may be caused because you did ask for an impossible situation or that you
are using the 'unstable'-distributin and that some packages still are locked up in 'incoming'"
"The following information may be of help:"

"The following packages do not carry the needed dependencies:
entangle: dependecy needed:  libgexiv2-2 (>= 0.4.1.) but is not installable 
             dependencies: libglib2.0-0 >= 2.35.0) but 2.323-0ubuntu1 will be installed
             dependencies: libraw5 (>=0.14.6) but 0.14.4ubuntu2 will be installed
E: unable to slove problems, you are locking defect packages.

How to solve?

---

### Post by ibjsb4 on 2013-05-22
Are you running 13.04?  That seems to be the package you downloaded.

---

### Post by Janno2 on 2013-05-22
> **ibjsb4 said:**
> Are you running 13.04?  That seems to be the package you downloaded.

I'm running Ubuntu 12.04

I found out that dpkg -- status entangle should give me the version.

However, the answer is: 'entangle' has not been installed and no info is available.

Which I knew already.

The problem seems, to me, that those missing dependencies are causing the trouble.

But, again, I'm an ubuntu newbie.

---

### Post by ibjsb4 on 2013-05-22
Me thinks you downloaded the 13o4 package.  libgexiv2-2 is only offered in raring.

[http://packages.ubuntu.com/raring/libgexiv2-2](http://packages.ubuntu.com/raring/libgexiv2-2)

---

### Post by Janno2 on 2013-05-22
> **ibjsb4 said:**
> Me thinks you downloaded the 13o4 package.  libgexiv2-2 is only offered in raring.

[http://packages.ubuntu.com/raring/libgexiv2-2](http://packages.ubuntu.com/raring/libgexiv2-2)

Thank you for the quick reply.

Quite possible I did download the 13o4 package, I remember to have seen 'raring' on the screen.

So what to do now?

---

### Post by ibjsb4 on 2013-05-22
```
sudo dpkg -r entangle
```

That should remove it and then you can try again :)

---

### Post by Janno2 on 2013-05-22
> **ibjsb4 said:**
> ```
sudo dpkg -r entangle
```

That should remove it and then you can try again :)

Tried that.

Result:

dpkg: warning: there's no installed package matching entangle

Well, that's no surprise. 

I earlier did write you:

"I found out that dpkg -- status entangle should give me the version.

However, the answer is: 'entangle' has not been installed and no info is available."

It's my guess that I indeed did download entangle, however in the wrong version.

So I do see twee options now:

A) Upgrading Ubuntu to 1.04. 
    I wonder if that's a clever thing to do.

B) Completely remove all of Entangle from my system.
    Which may be quite difficult.

---

### Post by Janno2 on 2013-05-22
OK, found a solution:

I did install Aptitude.
Next I used 'sudo aptitude install entangle'

I did get a proposal: 'keep entangle in current position?'
I denied, got a new proposal: 'install entangle 0.5.1.-1-getdeb (precise-getdeb1)'
I agreed, and got an error (no cennection).

Tried again, and installation went on.
Installation ended without message 'finished' or so.
But Entangle showed up in the Dash, and could be started.

I connected my Nikon D5000, and could make photos.

Now all I must find out s how to use the Live View option of the camera
in Entangle, in order to preview a phote before shooting.

But: I'm on my wy way to get it working.

---

### Post by ibjsb4 on 2013-05-23
Congratulations

I haven't been around for a day, but sounds like you got it :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Janno2 on 2013-05-23
> **ibjsb4 said:**
> Congratulations

I haven't been around for a day, but sounds like you got it :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Yes, but...

I tried earlier to use Gtkam. Installing it was no problem, but Live View works only with the very first photo I take, after that the photo's are taken without Live View. And the option "view miniatures" was not working.

Any how: it proved that my Nikon D5000 is capable of working with Live View in GtKam (more or less). So it should work in Entangle as well.

The problem with Gtkam as well as Entangle is that it is very hard to find help. There are no good user manuals, there are no helpdeks or dedicated forums.

I did sent an e-mail to the developper of Entangle. Hope never dies....;)

---

### Post by ibjsb4 on 2013-05-23
Nope, there is not much on it at all.  For what its worth.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Entangle&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Entangle&sa=Search&cof=FORID:9)

---

### Post by Janno2 on 2013-05-23
> **ibjsb4 said:**
> Nope, there is not much on it at all.  For what its worth.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Entangle&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Entangle&sa=Search&cof=FORID:9)

Thanks. Most of it I did already encounter when looking for a solution.

However, the developer Daniel Berrange, replied. He thinks it's libgphoto2 that'causing the problems. May be it's too old.
He adked for the installed version (libgphoto  2.4.13-iubuntu), and indeed, that's not the newest one.

---

### Post by Janno2 on 2013-05-27
Still having the same problem: Using my Nikon D5000 which has Live View. 
But Entangle does not use it.
That is: the very first time a took a photo it worked, after that never again.
I finally did uprade Ubuntu from 12.04 to 12.10. 
Did not yet now that the DebGet repository had to be re-installed. 
Did so, an installled Entangle. 
Enangle shows up in the Dash again, like last week.
So, I did connect the camera, and did start Entangle. 
After unmounting the camera I was able to take a photo.
And another, a.s.o.
However: still no Live View.

---

### Post by Janno2 on 2013-05-27
Solution found in the readmefile in usr/share/doc/entangle.

Using the keyboard shortcut "p" toggles the Live View mode!

Threat can be closed now.

---

