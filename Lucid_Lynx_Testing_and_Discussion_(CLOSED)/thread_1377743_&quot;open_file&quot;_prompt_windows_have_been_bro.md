---
title: "&quot;open file&quot; prompt windows have been broken for weeks"
date: 2010-01-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-01-10
Whenever a program calls up a file selection window, you can't simply  click on the file or use the arrow/enter keys to select it anymore. Doing so will take you to some  random directory within the folder you are browsing. The only way to  select the file is to type out the first few letters in the text box and select the matching file from the drop-down box.

Has anyone else experienced this? Also, are such windows part of nautilus or gtk?

---

### Post by ranch hand on 2010-01-10
Works fine on mine.

That would have to be part of nautilus as the file manager.

Sounds like a bug needs filed on that to me.

---

### Post by ronacc on 2010-01-10
Yes I'm getting that too , I thought I had bugged it but I can't find the bug report now , go ahead and bug it and I'll confirm .

Edit! found the bug # 502784 but they marked it invalid , go ahead and file yours mabye if enough of us report it they will believe us .

---

### Post by jpeddicord on 2010-01-11
> **ranch hand said:**
> Works fine on mine.

That would have to be part of nautilus as the file manager.

Sounds like a bug needs filed on that to me.
> **ronacc said:**
> Yes I'm getting that too , I thought I had bugged it but I can't find the bug report now , go ahead and bug it and I'll confirm .

Edit! found the bug # 502784 but they marked it invalid , go ahead and file yours mabye if enough of us report it they will believe us .


Because it's not nautilus, it's just gtk.

And please **do not** re-report the same bug. It just generates additional noise and creates more problems.

---

### Post by Ibidem on 2010-01-11
Bug NOT confirmed here (SciTe, Leafpad, GTK, pcmanfm-nohal, no nautilus).

The file dialogs are part of the toolkit used (GTK, Qt, FLTK, or whatnot), with a few rare exceptions.
I find that keyboard navigation with arrow keys works perfectly (for now).
Ibidem

---

### Post by ronacc on 2010-01-11
@jpeddicord thank you,  I didn't know for sure, I guessed nautilus and thought whoever triaged would change it to the correct package .

@ibidem yes keyboard nav works but the mouse is supposed to also hence the bug .

---

### Post by ronacc on 2010-01-11
they marked it invalid again and said it is "already registered" but don't say what it is a duplicate of.

---

### Post by VMC on 2010-01-11
> **ronacc said:**
> they marked it invalid again and said it is "already registered" but don't say what it is a duplicate of.
That's weird. Do you comment asking what duplicate?

---

### Post by ronacc on 2010-01-11
yes I did , haven't heard back yet .

---

### Post by chrisccoulson on 2010-01-11
> **ronacc said:**
> they marked it invalid again and said it is "already registered" but don't say what it is a duplicate of.

That's because we often don't have time to go searching for duplicates

---

### Post by ranch hand on 2010-01-11
> **chrisccoulson said:**
> That's because we often don't have time to go searching for duplicates
Oh come on, we are nearly at A2 on this pre-release, surely you guys aren't busy with bugs.

Sorry (not very) couldn't resist.

---

### Post by chrisccoulson on 2010-01-11
> **ranch hand said:**
> Oh come on, we are nearly at A2 on this pre-release, surely you guys aren't busy with bugs.

Sorry (not very) couldn't resist.

Unfortunately, we get too many bugs because users are too enthusiastic with reporting them ;)

On a serious note though, there are a lot of open bugs in Launchpad and a lot of bugs get reported multiple times. The volume of bugs sometimes make it very time consuming to search for duplicates (you can easily spend 15 minutes sometimes searching for a master bug, and those minutes soon add up and consume time that would be better spent doing more productive tasks). This especially applies for the more obscure bugs where it is not obvious what terms to search for, or where reporters haven't written a good description.

This doesn't just make it difficult for people triaging the bugs. People reporting bugs may also have a hard time finding out if their bug has already been reported too.

This means that occasionally we close bugs that we know are already reported somewhere, but just don't have the time to search for the master bug. In these instances, you either need to take our word for it that we know the bug is real, or search for the bug yourself and link them appropriately.

---

### Post by ronacc on 2010-01-11
I searched for anything that looked like a dupe both when I first entered it and after they invalided it , I didn't dee anything that looked likely . but I have a question , How do they know its a dupe but not what its a dupe of ?

edit   @chrisccoulson  sorry I was typing my response while you were posting , I hope you can understand that it can be frustrating and discouraging to us when we seem to get shunted off to never never land .

---

### Post by chrisccoulson on 2010-01-11
Yeah, I understand the frustration there.

We touch quite a few bugs, so quite often we come across bugs that we know we've seen reported before, but just don't know the bug number (or how to search for it).

---

### Post by 23meg on 2010-01-11
> **ronacc said:**
> 
edit   @chrisccoulson  sorry I was typing my response while you were posting , I hope you can understand that it can be frustrating and discouraging to us when we seem to get shunted off to never never land .

I agree, but at least as a regular tester, and now that you know the reason, there's no reason for you to feel like that. 

This is an unfortunate side effect of the volume of bug triage work being beyond the capabilities of the existing workforce. Had we had a significantly larger workforce, there would have been no excuse for it, but right now it's something we have to live with. 

The solution, of course, is to contribute to bug triage and take some load off the shoulders of people like Sebastien who wrestle with literally thousands of bugs every week. In the meantime, you'll occasionally have to trust the judgement of (in the very least) people who are part of the Ubuntu Bug Control team in knowing which bug is being tracked and which isn't. A possible temporary measure may be to come up with a better standard response for this situation than the generic "this bug has already been reported" one, which should ideally be reserved to cases where a specific bug has been marked as duplicate.

---

### Post by VMC on 2010-01-11
> **chrisccoulson said:**
> That's because we often don't have time to go searching for duplicates

How do you know its a duplicate in the first place, and not the first reported bug?

---

### Post by ranch hand on 2010-01-11
> **23meg said:**
> I agree, but at least as a regular tester, and now that you know the reason, there's no reason for you to feel like that. 

This is an unfortunate side effect of the volume of bug triage work being beyond the capabilities of the existing workforce. Had we had a significantly larger workforce, there would have been no excuse for it, but right now it's something we have to live with. 

The solution, of course, is to contribute to bug triage and take some load off the shoulders of people like Sebastien who wrestle with literally thousands of bugs every week. In the meantime, you'll occasionally have to trust the judgement of (in the very least) people who are part of the Ubuntu Bug Control team in knowing which bug is being tracked and which isn't. A possible temporary measure may be to come up with a better standard response for this situation than the generic "this bug has already been reported" one, which should ideally be reserved to cases where a specific bug has been marked as duplicate.
OK, how does  aperson go about doing this?  I, I must add, hope that folks doing triage are somewhat (or a bunch) more knowledgeable than I am.

---

### Post by 23meg on 2010-01-12
> **ranch hand said:**
> OK, how does  aperson go about doing this?  I, I must add, hope that folks doing triage are somewhat (or a bunch) more knowledgeable than I am.

Do you mean helping with bug triage? Taking a look at [https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs) and joining the #ubuntu-bugs IRC channel on Freenode would be a good way to start.

---

### Post by chrisccoulson on 2010-01-12
> **VMC said:**
> How do you know its a duplicate in the first place, and not the first reported bug?

I explained that in my last post

---

### Post by ronacc on 2010-01-12
I always try to search for a similar bug report before I add a new one ,so I understand what you mean by "not always knowing how to search for it" . Perhaps a few changes to the search mechanism might help . I have noticed that when you sort on "newest first" it seems to sort by "most recently posted" to and not "most recently filed" . this does not seem logical . Also some kind of "keyword" search in the body of reports might be helpful since many of us ( often myself) are not always sure what package is causing it ,only the behavior manifested . and a "search within results" capability would allow us to sort out the most likely candidates when we are returned a long list of hits . I realise that as a worldwide community there will always be some confusion about terminology and and description .

---

### Post by ranch hand on 2010-01-12
> **23meg said:**
> Do you mean helping with bug triage? Taking a look at [https://wiki.ubuntu.com/HelpingWithBugs](https://wiki.ubuntu.com/HelpingWithBugs) and joining the #ubuntu-bugs IRC channel on Freenode would be a good way to start.
Thank you.  That was exactly what I was looking for.

I will study the info on the link.

---

