---
title: "Audacious Audacity"
date: 2015-08-20
forum: MINT
---

### Post by mozart1 on 2015-08-20
Hi,

I am not new to Ubuntu; I have been using it for about 5-6 years now.  However, I am not v/good at the technical side of things, & have a friend who usually fixes things for me.  Sadly, he is away overseas at present, & I am trying to solve a problem that has just begun to present itself.  

I run Linux mint 18 or 19 I think (well, the most recent incarnation). I have been using Audacity for editing music tracks almost from the beginning, & as a professional musician, use it almost every day in one way or another.  But last evening it began going crazy.  Every few tracks it would stall, & I had to 'Force Quit".  I have uninstalled & re-installed it many times, but the problem remains.  I can only assume a recent Linux Mint update is interfering with it.  Has anyone reported a similar problem, & better still!, can anyone help me solve this problem?

Mozart1

---

### Post by PaulW2U on 2015-08-20
*Thread moved to **MINT**.*

---

### Post by trtle on 2015-09-09
could this be your problem Wxwidgets?  From the link
> **GNU/Linux:** 
[LIST]
[*] **Some Linux distributions are supplying Audacity builds that are unstable because built with wxWidgets 3.x which [Audacity does not yet support]("http://bugzilla.audacityteam.org/buglist.cgi?keywords=wx3&resolution=---").** This applies for example to Ubuntu "Daily Builds", [Ubuntu Vivid]("https://wiki.ubuntu.com/VividVervet/")  and Debian Jessie (Testing). Audacity 2.1.1. will now issue a warning  at start up if it was built with wx3 by mistake.  You can find out more  about this here: [Incorrect wxWidgets Version]("http://wiki.audacityteam.org/wiki/Incorrect_wxWidgets_Version").   To avoid issues you can build wxWidgets 2.8.12 then [compile Audacity against wxWidgets 2.8.12]("http://wiki.audacityteam.org/wiki/Developing_On_Linux#wxWidgets"). 
[/LIST]


Link-->[URL="http://wiki.audacityteam.org/wiki/Release_Notes_2.1.1"]http://wiki.audacityteam.org/wiki/Release_Notes_2.1.1
[/URL]

I don't know what to recommend, you could try upgrading to v2.1.1 because then at the very least a warning window would pop up notifying that Wxwidgets is built wrong.
but to check and see without doing that type at Command Line Interface (CLI) prompt$   dpkg -l | grep libwx
and in the listing you should be able to see which version of WxWidgets you are using....

---

