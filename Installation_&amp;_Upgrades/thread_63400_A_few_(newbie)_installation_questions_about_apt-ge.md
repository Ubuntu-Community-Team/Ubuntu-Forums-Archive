---
title: "A few (newbie) installation questions about apt-get"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by nyheat on 2005-09-07
My first question is really basic: where are most of the programs in Linux installed?
Because I trying to find XMMS so I can add skins, but I couldnt figure out where the skins/ directory is.

My second (set of) question(s) is about apt-get and the synaptic package manager
1) Is apt-get a terminal version of the Synaptic Package Manager?
2) After installing something through apt-get install program_name, does that mean the program is completely installed on my system? or does it only download the files?
3) Sometimes a tutorial I'm reading tells me to *apt-get install whatever*, but I get an error that "couldn't find package whatever" .. does that mean that the tutorial is pointing to a nonexistent package, or that apt-get is looking in the wrong place? how can I get around this if it happens?

Thanks in advance for the help, an answer by anyone to any of these questions would be appreciated

---

### Post by matthew on 2005-09-07
Instead of answering all your questions I'm going to help you know where to look for the answers...I'll answer some though.

[QUOTE=nyheat]My first question is really basic: where are most of the programs in Linux installed?[/QUOTE]
/usr/bin is probably the most common, although this isn't really going to be a helpful answer for you. That directory is where the executable binary for the programs are stored...the program probably has configuration files and data stored elsewhere. Here's a good page to get you started on Linux filesystems...it's a bit detailed, but worth skimming at a minimum.

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

> My second (set of) question(s) is about apt-get and the synaptic package manager
1) Is apt-get a terminal version of the Synaptic Package Manager?
2) After installing something through apt-get install program_name, does that mean the program is completely installed on my system? or does it only download the files?
3) Sometimes a tutorial I'm reading tells me to *apt-get install whatever*, but I get an error that "couldn't find package whatever" .. does that mean that the tutorial is pointing to a nonexistent package, or that apt-get is looking in the wrong place? how can I get around this if it happens?
1) Well, kind of. It's really more the other way around--Synaptic is a graphic version of apt-get.

2) It will be completely installed for you. Cool, huh?

3) Read the links in my signature, especially go to this one: [http://ubuntuguide.org/](http://ubuntuguide.org/) and make sure you have enabled the extra repositories (you will find out how on that page). That will probably take care of this problem.

EDIT: I guess I ended up pretty much answering the questions anyway didn't I? Hopefully the links I mentioned above and below will give you the answers to a lot of the questions you haven't asked yet or didn't know you wanted to ask.

---

### Post by wvslkr on 2005-09-07
XMMS If using Nautilus click on view > enable hidden folders.  Go to xmms/skins.

Synaptic=GUI for apt.

Fully installed.

You haven't enabled the repository where it is located.  See the users guidehttp://ubuntuforums.org/links/showlink.php?do=showdetails&l=7&catid=2

Hope that helps :)

---

### Post by kingbilly on 2005-09-07
edit:  BEAT!

---

