---
title: "howto make a HOWTO?"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by savage on 2005-05-08
I am relatively new to Linux, but have taken it up with a fervor. Luckily my employer is happy that someone in the office has jumped into the ring with Linux and OSS. Since October I have been making installations, configuring machines, setting them up as webservers, to the point that within the last month I installed Ubuntu as my main work and home environment.

As I have been working with all these Linux and related tools I have kept as much notes as possible. The problem is that they are really a horrible notes, nothing is in much order. Mostly chronological, and as the systems would change (I distro hopped 5 times) the software that I used to take the notes changed. Now I'm using Emacs alot and am starting to dabble with Tex, LaTex, etc.

What I would like to know, and I believe this would be valuable to others is Howto HOWTO? What are the tools and techniques that you use to keep things organized across different systems thru sometimes hasty installations, possibly on a caffeine fueled allnighter? Are there favored commands that you use to record the output of a programs installation or configuration feedback? How do I copy and paste commands from the command line? What if you are SSH'd, telnetted, XDMCP'd, or otherwise remotely connecting to a machine?

The only way I'm going to get good at writing Howto's is to write them. But I often find myself at the end of an installation, or after having solved a problem, having traversed the net, with a pile of disorganized half taken notes, that seem more likely of corrupting a persons brain than helping them out.

I've posted this to the users list as well, and will gather all the responses and make a Howto HOWTO post.

---

### Post by 23meg on 2005-05-08
i've been taking notes of just about every tweak i make to my installation in multiple plain text files. i'm looking for a better information management system (or multiple ones); i've so far tried notemeister and tomboy, which are satisfactory, but haven't given me the speed i used to have with Keynote under windows. 

there's also [basket](http://basket.kde.org/), which is a very promising kde app. i hope it will be in the repositories soon.

---

### Post by savage on 2005-05-10
for instance, does anyone know how I can get running output of the command line dumped to a text file? these are the sort of techniques I am after. stuff I can use on the most basic system to document what I am doing,

---

### Post by oracle2025 on 2005-05-10
you can use tee for this, it splits the output, and it goes to the screen plus a file.

---

### Post by gandonov on 2005-05-10
> ... does anyone know how I can get running output of the command line dumped to a text file? ...
You can use *script*:
```
script -a out.file
...
commands...
...
Ctrl + d
Script done, file is out.file
```
All your activity (in this terminal) will be saved to *out.file* (in your current directory).

---

### Post by derrick1985 on 2005-05-10
Notes!

This is great, i got a bunch of my own too that i would like to get organized.

It really does pay to surf forums.

---

### Post by thegreedyturtle on 2005-05-10
I think the first thing that I'd say to you is to find out what has and hasn't been done yet!

I went out and whipped this up: [http://www.ubuntulinux.org/wiki/UbuntuHowCome](http://www.ubuntulinux.org/wiki/UbuntuHowCome)

And then I found out by hanging out at #ubuntu-doc and the Ubuntu-doc mailing list that there's other stuff going on that supercedes what I've written. I'm still glad I wrote it, for my own value and since the other stuff still hasn't been finished yet.

For example theres a quick user guide and an administration guide and an FAQ  at: [http://people.ubuntu.com/~mako/docteam/quickguide/](http://people.ubuntu.com/~mako/docteam/quickguide/) and [http://people.ubuntu.com/~mako/docteam/adminguide/](http://people.ubuntu.com/~mako/docteam/adminguide/) and [http://people.ubuntu.com/~mako/docteam/faqguide/](http://people.ubuntu.com/~mako/docteam/faqguide/)

I'd say you should take a look at [http://www.ubuntulinux.org/wiki/DocteamGettingStarted](http://www.ubuntulinux.org/wiki/DocteamGettingStarted) and get involved!

---

### Post by savage on 2005-05-16
Thank you all for the useful responses. I did a little poking around the DocBook area and it looks like I have some learning to do there. Now I know what to aim for with what format the documentation should take. The commands to record terminal output are really going to be useful as well. Now when I have a question about what I did I can just look thru the history of the actual command line sessions.

It looks like I will have to pick up on a versioning system as well. That seems to be the most logical thing to do to keep tabs on what software I am using and will give me some sort of trail that I can follow for system changes. Strewing copies of config files and backups of directories everywhere I go just isn't cutting it. Since I'm no programmer I didn't realize that CVS or Subversion could be used to wrangle whatever sort of data is running roughshod over your booty at the moment.

I want to get in the habit of creating well documented systems, with instructions of what was done where and when, plus tools to put things back when they break. As well to be able to document what I do. It's not so much learning Linux. With persistance that isn't a problem, as there is to much documentation. Alot of what I am about is proving this platform to both myself, and to those around me. The systems I have built so far are a mess, and don't show any signs of improving in the organizational area. If I can knock out systems that anyone in my office can administrate because of succint documentation then I will be one step closer to winning over the critics. Plus I'll be able to stand in front of a machine I cobbled together years down the line, and be able to figure out something that has long left my tiny memory.

There is so much to take in within the *nix / FOSS worldview that it is very easy to miss areas that may be of the most use for someone starting out. Plus everyone has a different aspect that they are coming from, different expectations, different environments, different needs, are a precursor to the spheres of influence a new user will focus on.

Thanks again, I'm well on the path to actually giving the community something back now :)

---

