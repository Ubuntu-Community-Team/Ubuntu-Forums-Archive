---
title: "Tracker Search... no longer installed by default?"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hanzomon4 on 2009-10-09
I just realized that tracker wasn't installed on my system and beagle is no longer in the main repos.. What happened?

---

### Post by steeleyuk on 2009-10-09
Tracker wasn't in Jaunty if I remember correctly. Could be wrong though...

Beagle has [stopped development]("http://mail.gnome.org/archives/dashboard-hackers/2009-September/msg00005.html") pretty much. Though I thought it might have made it into the repo's for this version.

---

### Post by Joe_Bishop on 2009-10-09
Tracker is too buggy and will be. Beagle is too slow.

---

### Post by dasunst3r on 2009-10-09
Desktop search never really caught on with me and was one of the things I removed as soon as I finished installing Ubuntu.

---

### Post by lovinglinux on 2009-10-09
> **dasunst3r said:**
> desktop search never really caught on with me and was one of the things i removed as soon as i finished installing ubuntu.

+1

> **steeleyuk said:**
> Tracker wasn't in Jaunty if I remember correctly. Could be wrong though...

I think it was.

---

### Post by 23meg on 2009-10-09
Tracker wasn't installed by default in Jaunty, and still isn't in Karmic, the reason being that it's been causing too many performance and database corruption issues for little benefit, since it's not utilized by many projects yet. It will most likely come back, once 0.8 (which is a major departure from the pre-0.7 series) is finalized and it's more deeply integrated with GNOME. 

It is still in Main, though. If you don't see it in the repositories, there's definitely something wrong with your repository configuration.

---

### Post by dadedo123 on 2009-10-09
What is tracker? lol

---

### Post by steeleyuk on 2009-10-09
> **dadedo123 said:**
> What is tracker? lol

Assuming that's a serious question (I miss the point of the lol), its a search tool which looks at the content of files and allows you to search via that content.

For example, traditional, basic search commonly works via the filename whereas using the content, you can search via a sentence in an email or the ID3 tag in an MP3.

It could be likened to Google search engine for your computer... and yes I'm aware Google has its own desktop search. :)

---

### Post by donato roque on 2009-10-09
I am still using tracker search and you're right it isn't installed by default in Ubuntu 9.04 jaunty but it is in the repositories.  Tracker is nominated to be included in Gnome 2 so development is still continuing.

---

### Post by hanzomon4 on 2009-10-09
Oh I thought it was already a part of gnome and I'm sure it was included by default at one time because I remember the big flap over getting picked as opposed to beagle... Those were the days, tracker/beagle compiz/beryl

---

### Post by Endolith on 2009-10-09
I installed both to try to compare them.  Everything seemed to be working fine until I realized that Tracker wasn't indexing.  After I rebooted it started indexing, and now it's completely hogging the CPU and pissing me off.  I tell it to pause indexing and trackerd is still hogging the CPU, even with "performance" turned to the lowest setting.  This is BS.  I'm removing it and sticking with Beagle.

(What I really wish, though was that developers would swallow their egos, stop wasting everyone's time mediocrely duplicating the same functionality, and cooperate on making One Thing that does it well.)

---

### Post by Endolith on 2009-10-09
> **steeleyuk said:**
>  Beagle has [stopped development]("http://mail.gnome.org/archives/dashboard-hackers/2009-September/msg00005.html") pretty much. Though I thought it might have made it into the repo's for this version.

Aghhhh.  So what's going to be the next desktop search tool?

---

### Post by emarkay on 2009-10-10
> **dasunst3r said:**
> Desktop search never really caught on with me and was one of the things I removed as soon as I finished installing Ubuntu.

Agreed, I never liked Windows "indexing" my drive and never liked any performance/space used redundantly when "Search for Files" does all I need.

---

### Post by Endolith on 2009-10-10
> **emarkay said:**
> Agreed, I never liked Windows "indexing" my drive and never liked any performance/space used redundantly when "Search for Files" does all I need.

How is "Search for Files" different from "Desktop Search"?

---

### Post by marcelo.matos on 2009-10-10
When you "search for files" the system search in the names of your files, or in some other information like date of creation, size, type of file, etc. The system doesn't look "inside" (the content) of you files.

The so called "desktop search engines" like Tracker, Beagle, or Google Desktop look at the same information that "search for files" does plus inside your files. With the information gathered from the content of your files, It builds a index file. This aproach allows a much more powerful and faster search (After the indexing process and if you have a lot of data to search in)

Maybe, I wasn't clear enough, but my English skills aren't exactly the best ones. :P

---

### Post by Endolith on 2009-10-10
> **marcelo.matos said:**
> When you "search for files" the system search in the names of your files, or in some other information like date of creation, size, type of file, etc. The system doesn't look "inside" (the content) of you files.

That's not the same thing.  How can you even find anything with that?  :)

---

### Post by pt123 on 2009-10-10
Interestingly tracker is being developed actively
[http://blogs.gnome.org/mr/2009/09/30/tracker-0-7-released/](http://blogs.gnome.org/mr/2009/09/30/tracker-0-7-released/)
[http://blogs.gnome.org/mr/2009/09/18/tracker-update-2/](http://blogs.gnome.org/mr/2009/09/18/tracker-update-2/)

but without focusing on stability issues. 

------------
On Jaunty Tracker ignores users preference to not "Index file contents" resulting in large PDFs appearing on search results for any term, and there by making tracker use less.

Even getting it to reindex the files results the same thing.
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/410545](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/410545)

---

### Post by nanog on 2009-10-10
Although its still partially closed source google desktop search works fine for me in both amd64 and x86. IMO, tracker is akin to a technology demo in comparison.

[http://googledesktop.blogspot.com/](http://googledesktop.blogspot.com/)

---

### Post by emarkay on 2009-10-10
> **marcelo.matos said:**
> When you "search for files" the system search in the names of your files, or in some other information like date of creation, size, type of file, etc. The system doesn't look "inside" (the content) of you files. The so called "desktop search engines" like Tracker, Beagle, or Google Desktop look at the same information that "search for files" does plus inside your files. With the information gathered from the content of your files, It builds a index file. This aproach allows a much more powerful and faster search (After the indexing process and if you have a lot of data to search in) Maybe, I wasn't clear enough, but my English skills aren't exactly the best ones. :P


Oh, well I have been using PC's since the Apple II and I guess I figured If I don't know what's in my own files, or a file I have been given for a legit purpose, I better go back to the typewriter.  
Seriously, I never needed to do that in all these years; wait for an app to find keywords and sentences from afar, but I do sometimes open items and search, if it's an unfamiliar document or a website.
Thanks!

---

### Post by marcelo.matos on 2009-10-14
> **Endolith said:**
> That's not the same thing.  How can you even find anything with that?  :)

Yeah, you're right. I've said some wrong things up there. In fact, the "search for files" do look inside your files. But in Jaunty It never worked for me.

Only with "tracker" I could search inside my files. And I could never found anything. It was a pain because in Windows this kind of thing aways worked OK.

Since tracker worked OK, I never worried. I just tought it was a "Linuxthing" but I've been thinking since Your comment and... Maybe... Just Maybe.... something could be wrong here. :-$

PS: In Karmic the search for files is ok.

---

### Post by Endolith on 2009-10-14
> **marcelo.matos said:**
> Yeah, you're right. I've said some wrong things up there. In fact, the "search for files" do look inside your files. But in Jaunty It never worked for me.

Nautilus's "Search for files"?  That has never worked for me, either.  I'm not sure what it's even supposed to do.  Search by filename?  Search inside files?  It doesn't say.  When I have to find something inside a file and the Tracker/Beagle can't find it, I use grep, because I can't find any graphical tool that does the same thing as grep.  It takes *forever*, though.

---

