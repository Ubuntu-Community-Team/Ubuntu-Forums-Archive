---
title: "Suggestions for the Ubuntu Software Center"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Copernicus1234 on 2009-10-11
[SIZE="4"][FONT="Arial Black"]About the In Progress View[/FONT][/SIZE]

[IMG]http://img0.uploadhouse.com/fileuploads/4698/469887035da89a4baddab4c7bf19aac907cfe2b.png[/IMG]

1. The **In Progress category** to the left could be split up to show separate downloads and their individual progress as tree nodes, like this:

In Progress (4 of 4):
 - Eclipse (35% done)
 - Eric python IDE (20% done)
 - Winefish LaTeX Editor (54% done)
 - Shoes (11% done)

This brings me to suggestion 2:

2. **Parallel downloading**. Files should be downloaded in parallel by default and there should be download queue handling.

3. **Download queue**. Options to set how many files you want to download in parallell by default. For every file in the download queue, it should be possible to move it up or down in the queue and the top X number of files should be downloading. The others should be on hold.

4. **Export/import installed packages**. Every package that has been installed after installation of Ubuntu would export to a list that the Ubuntu Software Store can read. This will allow for people to very easily set up pre-installed ubuntu machines with the software they wish to be available.






[SIZE="4"][FONT="Arial Black"]About the Get Free Software & Installed Software Views:[/FONT][/SIZE]

[IMG]http://img2.uploadhouse.com/fileuploads/4698/4698952a357746ba1e82e2ee9bb2a39dcc604a8.png[/IMG]

1. **Columns with details.** Within a category, the *version* number of the software should have a column. There should also be a column for when the software was *added* to the repository (for Installed Software, this column should show when the software was installed by the user). These columns should be sortable, so someone could sort on updated software added to that category. There should also be a *rating* category.

**NOTE**: Its particularly important to give the user a way to see what software **he/she** installed so he can go through that list and remove everything he doesnt use. You can do this by having the column with install date above or some other way, but there needs to be a way.




[SIZE="4"][FONT="Arial Black"][FONT="Arial Black"]General look of the GUI[/FONT][/FONT][/SIZE]

[IMG]http://img8.uploadhouse.com/fileuploads/4698/4698988018a66887d034178a3dfcb0aed286271.png[/IMG]

1. The **blue background** has to go. Perhaps replace with a nice gradient or even just a white background. This is probably what made my first impression of the tool so bad. Please get rid of it.

2. The **Departments headline**. Please do something about this because it looks really bad and not professional at all. Perhaps remove it altogether because there really is no need to explain the icons.



[COLOR="RoyalBlue"]So those are my suggestions. As always, this is a personal opinion and I encourage people to use this thread to discuss the Ubuntu Software Store and how it could be improved. Go crazy with ideas. :)[/COLOR]

---

### Post by Leighman on 2009-10-11
I agree that the departments title and colour have to go!
I would also like the see the addition of ratings, but I think something would have to be done about default apps, since these were always 5-star in Add/Remove.  Perhaps labelling them 'default' or a single, different coloured star instead?

---

### Post by rex4u on 2009-10-11
> **Leighman said:**
> I agree that the departments title and colour have to go!
I would also like the see the addition of ratings, but I think something would have to be done about default apps, since these were always 5-star in Add/Remove.  Perhaps labelling them 'default' or a single, different coloured star instead?

I will also suggest user-reviews to be added.
Thanks...

---

### Post by tgpraveen on 2009-10-11
Since you have take a lot of efforts and make some good points i suggest you mail all these ideas to ubuntu-desktop mailing list.

There the developers willl actually pay attention to your ideas. and you can discuss it.

The devs hardly ever visit the forums.

You could also then file bugs/wish lists as required.

---

### Post by Copernicus1234 on 2009-10-11
> **tgpraveen said:**
> Since you have take a lot of efforts and make some good points i suggest you mail all these ideas to ubuntu-desktop mailing list.

There the developers willl actually pay attention to your ideas. and you can discuss it.

The devs hardly ever visit the forums.

You could also then file bugs/wish lists as required.

Thank you, but its probably a good idea to see what other people has to say as well first. :)

---

### Post by cyberkilla on 2009-10-11
I agree. The blue background looks out of place. It would be much nicer if it took on the colour scheme of a file browser box.

It has improved dramatically though. I'm not sure how they'll address those cases when you try to remove a package and it tries to remove the entire operating system:P

---

### Post by ljrmorgan on 2009-10-11
I don't understand the point of the software centre. I also don't think the categories are particularly useful. I mean say you wanted to install a new IDE. You go to the programming category (like in the screenshot above) and see endless IDEs, yet you have no way of telling if a certain one is going to do what you want. How many people would just install the first one they saw, try it out for a few hours, ditch it and go on to the next one?

I personally can't see many people doing that. When I want to install an app, I search around online for something which compares them, maybe go to the app website, find the one I want and install it. For this the categories are pointless - say I did some research and decided to install eclipse. I'd then go into synaptic or whatever, and search for eclipse, and install it. I wouldn't need to browse the "programming category".

Basically, what I'm trying to say, is that you already have to have hunted around on the internet to find a suitable application, and then go to your package manager and install it. The categories etc. are completely useless, because you'd just type in the name of the app you want, having already researched it, and install it.

If, however, the software centre had some way of letting users compare etc. then the categories might be useful. I'm not sure about reviews - I imagine that every programmer is going to give great reviews to the IDE they use because it does what they want better than anything else, that's why they use it! It doesn't mean that that program is suited to someone who's just starting out programming say.

I think instead apps should be sorted within their category based on popularity. I think as a rule of thumb, if you're not sure entirely what you want then chances are the most popular thing will roughly do what you want OK. This wont be true for everyone, but I think it will be for the majority, the rest can go off and do some research until they find the app they want, and then install that. I also think if you know quite a lot already about the area (to continue the IDE example, say you were quite an experienced programmer) then you probably already know the app you want to install.

---

### Post by zekopeko on 2009-10-11
> **rex4u said:**
> I will also suggest user-reviews to be added.
Thanks...

Epic fail. Read the wiki spec. Already planned.

> **ljrmorgan said:**
> I don't understand the point of the software centre. I also don't think the categories are particularly useful. I mean say you wanted to install a new IDE. You go to the programming category (like in the screenshot above) and see endless IDEs, yet you have no way of telling if a certain one is going to do what you want. How many people would just install the first one they saw, try it out for a few hours, ditch it and go on to the next one?


> 
I personally can't see many people doing that. When I want to install an app, I search around online for something which compares them, maybe go to the app website, find the one I want and install it. For this the categories are pointless - say I did some research and decided to install eclipse. I'd then go into synaptic or whatever, and search for eclipse, and install it. I wouldn't need to browse the "programming category".

Basically, what I'm trying to say, is that you already have to have hunted around on the internet to find a suitable application, and then go to your package manager and install it. The categories etc. are completely useless, because you'd just type in the name of the app you want, having already researched it, and install it.

Ever hear of apt:// links?

> If, however, the software centre had some way of letting users compare etc. then the categories might be useful. I'm not sure about reviews - I imagine that every programmer is going to give great reviews to the IDE they use because it does what they want better than anything else, that's why they use it! It doesn't mean that that program is suited to someone who's just starting out programming say.

There is a link to the web site for (almost) every piece of software. Also tagging will help (deb-tags FTW), along with better descriptions and searching within the description.

> I think instead apps should be sorted within their category based on popularity. I think as a rule of thumb, if you're not sure entirely what you want then chances are the most popular thing will roughly do what you want OK. This wont be true for everyone, but I think it will be for the majority, the rest can go off and do some research until they find the app they want, and then install that. I also think if you know quite a lot already about the area (to continue the IDE example, say you were quite an experienced programmer) then you probably already know the app you want to install.

This entire response can be summarized with: READ THE WIKI SPEC!!!
Everything that was said here is covered in the spec (for the most part).

---

### Post by cicoandcico on 2009-10-11
> **cyberkilla said:**
> I agree. The blue background looks out of place. It would be much nicer if it took on the colour scheme of a file browser box.

It has improved dramatically though. I'm not sure how they'll address those cases when you try to remove a package and it tries to remove the entire operating system:P

+1.
Also, i would replace the clickable icons with big buttons, just like the gnome control center... it would seem more integrated with the gnome environment.

---

### Post by Marlonsm on 2009-10-11
I agree with your changes.

One I'd add is to do something about that big unused space in the left part of the window. Maybe making it show the "Departments".

Something like this (I'm not good with GIMP):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131587&stc=1&d=1255271313[/IMG]

(I'm not sure if it has been planned already, tho)

---

### Post by MadsRH on 2009-10-11
There's a sub-wiki for Software Center comments [https://wiki.ubuntu.com/SoftwareCenter/Comments](https://wiki.ubuntu.com/SoftwareCenter/Comments)

---

### Post by Seventh Reign on 2009-10-11
> **ljrmorgan said:**
> I don't understand the point of the software centre. I also don't think the categories are particularly useful. I mean say you wanted to install a new IDE. You go to the programming category (like in the screenshot above) and see endless IDEs, yet you have no way of telling if a certain one is going to do what you want. How many people would just install the first one they saw, try it out for a few hours, ditch it and go on to the next one?

I personally can't see many people doing that. When I want to install an app, I search around online for something which compares them, maybe go to the app website, find the one I want and install it. For this the categories are pointless - say I did some research and decided to install eclipse. I'd then go into synaptic or whatever, and search for eclipse, and install it. I wouldn't need to browse the "programming category".

Basically, what I'm trying to say, is that you already have to have hunted around on the internet to find a suitable application, and then go to your package manager and install it. The categories etc. are completely useless, because you'd just type in the name of the app you want, having already researched it, and install it.

If, however, the software centre had some way of letting users compare etc. then the categories might be useful. I'm not sure about reviews - I imagine that every programmer is going to give great reviews to the IDE they use because it does what they want better than anything else, that's why they use it! It doesn't mean that that program is suited to someone who's just starting out programming say.

I think instead apps should be sorted within their category based on popularity. I think as a rule of thumb, if you're not sure entirely what you want then chances are the most popular thing will roughly do what you want OK. This wont be true for everyone, but I think it will be for the majority, the rest can go off and do some research until they find the app they want, and then install that. I also think if you know quite a lot already about the area (to continue the IDE example, say you were quite an experienced programmer) then you probably already know the app you want to install.

This post was a joke right?  There's no way anyone could write that with a straight face .. its not possible.  No way No how.

#1. The Software Center is designed to combine and eliminate the need for several other applications.  Why have 5 different apps that do the exact same thing when you can have 1 that does it and does it better?

#2. The Software Center is no where near complete yet.  It most likely wont be 'finished' for a few more Releases.  IF it ever truly is.  Additions will probably be added and removed for several years.  

#3.  The Software Center is for Ubuntu.  Users with little to moderate GNU/Linux experience.  Most 'experienced' programmers probably wont be using Ubuntu as their primary system.  Why drive a Pinto when you can build a Ferrari yourself?

---

### Post by cyberkilla on 2009-10-11
If I was going to suggest anything, it would be this:

Try to make it possible to **vote for the usefulness of a package**! If you have a 5 star rating system, you can hide anything less than 3 stars by default. Obviously, a way to show all results would be required too.

I know this is all community stuff, but honestly, 90% of the games (for instance) are pathetically bad. They are not worthy of installation.

A list of a few hundred applications which claim to do the same thing (but don't, and you can't know until you install them) is not very useful at all.

They'd probably have to set up a server to keep a database of the votes, indexed by package name. I don't know if it is feasible, but it would be brilliant:P

---

