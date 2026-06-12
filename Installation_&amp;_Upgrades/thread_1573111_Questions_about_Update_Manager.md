---
title: "Questions about Update Manager"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by Jeff Root on 2010-09-12
Ubuntu 9.10 Karmic Koala.  Dial-up Internet connection.
 
I turned off automatic updates before ever connecting to the
Internet.  When I checked for updates manually a few days ago,
forty-some files downloaded.  A few of them were quite large,
perhaps a megabyte or two.  Several of the files near the top
of the list were marked as "Failed".  There were no failures
farther down the list.
 
After they were all downloaded, Update Manager tells me that
315 updates are available, under the two headings, "Important
security updates" and "Recommended updates".  The "Changes"
box at the bottom of the window says that the list of changes
failed to download.  I ran the Update Manager again but it
quickly told me (in effect) that there was nothing new since
the previous check, and nothing more was downloaded.
 
The descriptions of the updates are horribly inadequate.  And
I *am* looking at the long decriptions in the box at the bottom.
For most updates the information is not adequate to determine
what it does, whether it would have any effect on my particular
system, or whether it would benefit me.
 
For example, near the top of the list of 315 updates:
----------------
cpp-4.4
The GNU C preprocessor (Size: 3.0 MB)
 
A macro processor that is used automatically by the GNU C
compiler to transform programs before actual compilation.
 
This package has been separated from gcc for the benefit of
those who require the preprocessor but not the compiler.
----------------
I have programmed using compilers, though never in C or any
related language.  I have a vague idea what the terms mean.
That doesn't help me to determine whether I need the update.
 
Many descriptions are shorter and even less informative.
 
I estimate that the total size of the information displayed
by Update Manager, plus the URLs that aren't shown, must be
about 1/2 megabyte.  As I said above, 40-some files were
received, a few over a megabyte each.
 
What is in all those files?
 
Where are they stored on my computer?
 
Why did some of the files fail to download?
 
How do I determine which updates I need?
 
What are the security risks of not updating?
 
   -- Jeff, in Minneapolis

---

### Post by dirghrabadia on 2010-09-12
>  
 What is in all those files?
All those files have some additional changes/improvements.

>  
 Where are they stored on my computer?
 They are stored on various locations depending where the original files were present.

>  
   Why did some of the files fail to download?
  Don't know the exact reason. Maybe due to some missing packets during the download.

>  How do I determine which updates I need? Mostly by what you use on daily basis, but if you are not sure, its always wise to at least the get the security updates and recommended updates for frequently used applications.

>  What are the security risks of not updating? Probably none, if you never happen to be online. 
But if you do, there might be some loopholes in your current system, which if not updated, can make your system vulnerable to an attacker. Apart from that, it helps in smoother and efficient running of the OS.

---

### Post by Jeff Root on 2010-09-12
> **dirghrabadia said:**
> > 
What is in all those files?
All those files have some additional changes/improvements.
I think you misunderstood.  I am asking what is in the
40-some files which were downloaded.  Those files took
something like 15 minutes to download, so they must have
totalled about 4 MB.  The 315 updates are reported by
Update Manager to total 271.7 MB.  That would require
about 18 hours to download.
 
> **dirghrabadia said:**
> > 
Where are they stored on my computer?
They are stored on various locations depending where the
original files were present.
There were no original files.  I'm asking where the
40-some files of descriptions and whatnot were saved.
 
> **dirghrabadia said:**
> > 
Why did some of the files fail to download?
Don't know the exact reason. Maybe due to some missing
packets during the download.
I see that now when I start Update Manager the missing
"Changes" info is downloaded for each item, apparently
as I switch the focus to that Item.  I haven't let it
download everything yet, but it looks like better info
about what the updates consist of may be in them rather
than in the "Descriptions".
 
> **dirghrabadia said:**
> > 
How do I determine which updates I need?
Mostly by what you use on daily basis,
That isn't the info I need.  I need to know whether what
I use depends on the updates.  The example I quoted was
"cpp-4.4, The GNU C preprocessor".  I have no idea whether
that is already installed on my computer or not.  I have
no idea whether I use it constantly or have never used it
and will never need to use it.  The description does not
give me a clue as to whether it updates something that
is essential to the operation of the computer or is only
needed if I want to write programs in C and "preprocess"
them, whatever that means.
 
> **dirghrabadia said:**
> 
but if you are not sure, its always wise to at least get
the security updates and recommended updates for frequently
used applications.
As I said, there are 315 of them.  I read the descriptions
(though not the changes, yet.  I'll do that now that they
are available) and none of them was obviously essential.
None out of 315.  But most of the descriptions didn't tell
me anything.
 
> **dirghrabadia said:**
> > 
What are the security risks of not updating?
Probably none, if you never happen to be online. 
But if you do, there might be some loopholes in your
current system, which if not updated, can make your
system vulnerable to an attacker.
That is extremely vague.  I realize of course that a
detailed description of each vulnerability is not what
I should expect here, but I would expect something a
bit more concrete.  At least an example or two of how
specific updates can prevent specific vulnerabilities.
Maybe the "Changes" info will answer this question.
 
Thanks for trying.  :-)
 
   -- Jeff, in Minneapolis

---

### Post by snowpine on 2010-09-12
Hi Jeff, it is recommended to install all 315 updates. They are security patches and bug fixes for packages that you already have installed. I realize this is a very large download, but please understand 9.10 was released in October 2009 so there is almost an entire year of updates! 

The original 40-something files you downloaded were simply the list of available packages and updates. They are stored in /var/cache/apt I believe.

---

### Post by Jeff Root on 2010-09-13
Thank you, snowpine.  I don't see how the 42 files could
be explained as being only the list of updates and their
descriptions, since, as I said, the info I could see was
a total of maybe 1/2 megabyte, while the downloaded files
must have totaled about 4 megabytes.  That leaves me
wondering what the other 3.5 megabytes is.
 
The "Changes" info downloads when I click on each update
in the list.  One more update was added in the last day,
so there are now 316 updates totalling 272.1 MB.  I've got
the first 150 or so, and have skimmed them.  They do give
the detail I want, but they are so arcane that I can only
learn a very little from them without going into a great
deal of research-- far more than would make sense.
 
In some cases, though, it is fairly obvious that the
update isn't relevant for me, such as an update for
PostScript when the one and only time I've ever seen
a PostScript file was over fifteen years ago.
 
The "Changes" info appears to be about twice as voluminous
as the descriptions previously downloaded.  Altogether it
might total 1.5 MB.
 
   -- Jeff, in Minneapolis

---

### Post by snowpine on 2010-09-13
Ubuntu is not a "Keep It Simple, Stupid" distro like Slackware or Arch that only gives you exactly what you want/need. Not every user will need/use every single package, however most Ubuntu users find it a waste of time to micromanage every update. I repeat my recommendation to simply install all updates without worrying about it.

If you want fine-toothed control over your Ubuntu system, I recommend starting with a Minimal Install and adding only exactly what you need: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Of course, the brillance of "open source" is that, if you have the time and expertise, you can download each update without installing it, then inspect the changes to the source code to see **exactly** what is different and decide whether you want the change on your system. Most Ubuntu users in my experience opt for the "plug and play" experience of simply trusting the developers and applying all available updates. Of course, there are also some users who never update their system, and even some users who continue to use obsolete "end of life" releases. It is your choice how far you are willing to go in pursuit of security and stability.

---

### Post by Jeff Root on 2010-09-16
As I said, I have to click on each entry in Download Manager
to get the "Changes" info.  I now find that after clicking on
about half of the 316 updates listed, closing Download Manager
makes all of the "Changes" info disappear the next time I run
the program.  Are these bugs, or what?
 
   -- Jeff, in Minneapolis

---

