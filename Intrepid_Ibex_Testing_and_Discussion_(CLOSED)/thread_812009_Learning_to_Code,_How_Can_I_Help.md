---
title: "Learning to Code, How Can I Help?"
date: 2008-05-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by talkingwires on 2008-05-29
I used to think that there were teems of people working on the Next Great OS Release, but apparently that's not the case. I swung by the Ubuntu Developer's Summit in Prague and there were, at best, three dozen guys (and a couple gals) there. Then I saw [this blog post](http://blogs.gnome.org/cneumair/2008/05/26/i-need-a-helping-hand-make-nautilus-tabs-a-joy-for-users/) by a Nautilus developer. I quote:> As of writing, I am the only active Nautilus maintainer, and I am totally running out of time due to my studies.The *only* developer for Gnome's file manager? Okay, I'm not the world's greatest coder. In fact, I've only taken a few CS classes for my CS minor, and they were in Java. But I want to start helping out. It'll probably take weeks to get all the function calls to obscure libraries into my head, but I want to start. Where can a beginning programmer, with hardly any real world experience, get a foothold in such a massive project?

---

### Post by gnomeuser on 2008-05-29
You should probably start with selecting a bug and examining it, then fixing it. Learn the existing codebase and get a bit of a connection with the upstream development community.

You could also go to the bugtracker and search for all the bugreports with patches attached. Then find one that interests you, review the bug and the patch to see if it still applies and if it fixes the bug. There are sadly many such bugs, and it would be a great way to get involved with development. 

Try not to bite off to much to chew, start small. Set small goals and try to learn from the existing community on how to interact.

---

### Post by olskar on 2008-05-29
Take a look here :)

[http://developer.gnome.org/doc/](http://developer.gnome.org/doc/)

That nautilusdeveloper sure needs some help..

---

### Post by 23meg on 2008-05-29
> **talkingwires said:**
> I swung by the Ubuntu Developer's Summit in Prague and there were, at best, three dozen guys (and a couple gals) there. 

There were at least a hundred people at the summit. Not all of them were Ubuntu developers, but then not all Ubuntu developers are meant to be there either. Probably the session you attended wasn't very crowded.

[QUOTE=talkingwires]Then I saw [this blog post](http://blogs.gnome.org/cneumair/2008/05/26/i-need-a-helping-hand-make-nautilus-tabs-a-joy-for-users/) by a Nautilus developer. I quote:The *only* developer for Gnome's file manager? 
[/QUOTE]

Maintainer != developer. Upstream maintainers (GNOME module maintainers in this case) are the people who oversee the code that goes into the project, make the final call on what code goes in, and play the lead role in shaping the vision of the project in general. The previous Nautilus maintainer, Alexander Larsson, [took a long leave]("http://www.nabble.com/New-nautilus-maintainer---Alex-on-parental-leave-to16158110.html") a while ago, and left the maintainer role to two major contributors, one of whom is Neumair. Apparently Neumair is alone in the maintainer role now, but that doesn't mean there's one person working on Nautilus in the whole world.

With all this said, I'd be the first one to tell you that shortage of workforce is usually the most important reason why things stagnate in the FOSS world when they do. I've seen a ridiculous amount of discussions where people come up with all kinds of weird ideas for "improving" projects that don't quite work the way they want through all sorts of policy changes, when the underlying reason they aren't aware of is that there's simply not enough workforce going into the project.

This is more true for Ubuntu than many other projects, since Ubuntu is pretty young, and due to the nature of its target audience, doesn't have a high ratio of contributors to users.

[QUOTE=talkingwires]Okay, I'm not the world's greatest coder. In fact, I've only taken a few CS classes for my CS minor, and they were in Java. But I want to start helping out. It'll probably take weeks to get all the function calls to obscure libraries into my head, but I want to start. Where can a beginning programmer, with hardly any real world experience, get a foothold in such a massive project?
[/QUOTE]

I agree with gnomeuser. Check [the MOTU team's weekly list of small bugs]("https://wiki.ubuntu.com/MOTU/TODO#head-c6381d8a50f2fc9b5bfe26415d4d09c194d326fe") intended for new contributors. You'll also find many more by doing a search for the "bitesize" bug tag in [the bug tracker]("https://bugs.launchpad.net/ubuntu"). And then there's Daniel Holbach's "[Really Fix It!]("http://daniel.holba.ch/blog/?p=98")", which provides a list of bugs fixed elsewhere, or with patches attached. And it's a good idea to read the following to get acquainted with the processes:

[https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment)
[https://wiki.ubuntu.com/UbuntuDevelopers](https://wiki.ubuntu.com/UbuntuDevelopers)
[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)
[https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs)

Also note that Ubuntu is made up of the products of lots of independent upstream projects. If your interest lies in a certain component, you may want to contribute directly to the project that provides it, and Ubuntu (as well as the rest of the FOSS world) will still benefit from your work.

---

