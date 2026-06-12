---
title: "I found a bug in Nautilus in 9.04, but not sure"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Olnex on 2009-04-06
Hello, I found a bug in 9.04, but not sure if it is just my problem.
I installed 9.04 beta several days ago, and did a full update, I also changed the background of nautilus from white to Onyx(so the background is dark and the file names are white), everything is fine.

Today I want to move some files from one directory to another, so I used Ctrl+X(cut) and then opened a tab(instead of opening another nautilus window), then I found the file names are all black as if the background is white, I tried many times, but still see the problem.

Also, when I opened a nautilus window, if it is the first one(only one), then the mouse cursor is always busy and there are some busy icons on the top right of the window(above the "icon view" combo box), after I open another nautilus window, the busy icons disappear in the first window, and the second window also does not have the busy icon problem.

---

### Post by coffeecat on 2009-04-06
> **Olnex said:**
> Hello, I found a bug in 9.04, but not sure if it is just my problem.
I installed 9.04 beta several days ago, and did a full update, I also changed the background of nautilus from white to Onyx(so the background is dark and the file names are white), everything is fine.

Today I want to move some files from one directory to another, so I used Ctrl+X(cut) and then opened a tab(instead of opening another nautilus window), then I found the file names are all black as if the background is white, I tried many times, but still see the problem.

Yes, I can confirm this. I couldn't find an 'Onyx' background among patterns, so I used 'Blue Type' and I get the same. [Launchpad bug #339165]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/339165") seems to be describing this. It's marked as 'confirmed', but there hasn't been a comment for nearly a month.

> **Olnex said:**
> Also, when I opened a nautilus window, if it is the first one(only one), then the mouse cursor is always busy and there are some busy icons on the top right of the window(above the "icon view" combo box), after I open another nautilus window, the busy icons disappear in the first window, and the second window also does not have the busy icon problem.

I think I follow what you mean. Were you opening a folder with a very large number of files in it - something like /usr/bin? If so, this is normal behaviour, but it should only go on for a few seconds as the system caches all the file names.

I'll ask a moderator to move this thread to the Jaunty subforum. Jaunty is still in Beta and it's more likely to be seen by Jaunty testers there.

---

