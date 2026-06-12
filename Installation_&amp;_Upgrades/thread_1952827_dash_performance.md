---
title: "dash performance"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by g.a. on 2012-04-05
dear all,

i installed 11.10 recently and started testing the dash performances.

by typing [special key]+F the "search for files & folders" option of dash nicely shows up.

however, typing the name of folders never find them, with the files it is a little bit better but it is clearly not a "search".

using the right menu and the option for searching specifically folders the result is a little bit better but not sufficient.

any suggestion?
thanks
g.

---

### Post by Paddy Landau on 2012-04-05
Hmm. I get the same result as you.

Please would you raise this as a bug.

---

### Post by g.a. on 2012-04-06
are you sure it is a bug? 

btw, this morning I run dash to run thunderbird and, after having typed "thu" the correct program icon showed up together with 5 files that do not have "thu" in their name (!?!), 3 jpg files and 2 textual files.

is there something that i'm missing or some configuration to set?

it is frustrating to browse folders because, even with the exact name, i do not know other way to quickly located them in the hard disk.

best,
g.

---

### Post by Paddy Landau on 2012-04-06
> **g.a. said:**
> are you sure it is a bug?
I consider that to be a bug! I also often have inconsistent results, such as returning a file one time but not another for the same query.

> **g.a. said:**
> ... the correct program icon showed up together with 5 files that do not have "thu" in their name (!?!), 3 jpg files and 2 textual files.
It displays files with the item not just in the name but also in the contents. Maybe there is "thu" in the image properties of the JPG files.

---

### Post by g.a. on 2012-04-08
thanks for your reply. I would like to bother you again with a couple of further questions:

a) I never open a bug but always added comments on existing bugs on launchpad. I searched and no one bug is covering my case, well... how to open a bug report? (this guide does not seem to be correct for me
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs))

b) what about filling a wish list? is it the same procedure (but writing wish list in the title)? I would like to have the "open containing folder" option in dash when (finally) a file is found

thanks in advance,
g.

---

### Post by Paddy Landau on 2012-04-08
> **g.a. said:**
> I never open a bug but always added comments on existing bugs on launchpad. I searched and no one bug is covering my case, well... how to open a bug report? (this guide does not seem to be correct for me
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs))
That is the correct method. In short, you use [ubuntu-bug as illustrated]("https://help.ubuntu.com/community/ReportingBugs#A4._Collect_information_about_the_bug").

> **g.a. said:**
> what about filling a wish list?
That is not done as a bug. Have a look at [Brainstorm]("http://brainstorm.ubuntu.com/"). If it is not already raised, raise a new Brainstorm there.

---

### Post by g.a. on 2012-04-09
done thanks, this bug-report system seems to be really powerful.

the ubuntu-bug command did not show up for me from dash, I had to run apport from shell with the correct PID and it finally worked.

best
g.

---

### Post by Paddy Landau on 2012-04-09
Please post a link to the bug so that I, and others finding this thread, can vote for it.

BTW, ubuntu-bug is a command. You don't find it in the dash, but instead by pressing Alt-F2.

---

### Post by g.a. on 2012-04-09
right. one is:

Dash - Search for a folder gives everything inside the folder, except the folder itself
[https://bugs.launchpad.net/ayatana-design/+bug/749566](https://bugs.launchpad.net/ayatana-design/+bug/749566)

and the wishlist is

[wishlist] unity-lens-files open containing folder option 
[https://bugs.launchpad.net/unity/+bug/977044](https://bugs.launchpad.net/unity/+bug/977044)

i will fill another bug on the file search but first i need to better focus the problem on my pc.
g.

---

### Post by Paddy Landau on 2012-04-09
Thank you. I have voted for the bugs. The first one has generated plenty of interest already.

Personally, I would have put the second item (the wish) in [Brainstorm]("http://brainstorm.ubuntu.com/"), because I didn't realise that Launchpad could include wishes! But it seems that you did the right thing.

---

