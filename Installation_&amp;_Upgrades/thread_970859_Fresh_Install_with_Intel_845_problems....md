---
title: "Fresh Install with Intel 845 problems..."
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Jim DeLois on 2008-11-04
Hello all - First time poster here, but I've been hooked on Ubuntu since setting up the server edition on one of my home boxes about 18 months ago.  My question, however, is on Ubuntu Desktop, v8.10 and the installation thereof.

I was recently fortunate enough to receive a used Dell as a hand-me-down.  Obviously, the first thing I wanted to do was wipe it out and toss Ubuntu on it.  Unfortunately, this normally simple process has been giving me trouble for three days straight...  I am to the point where I'm about to reinstall Windows instead so I have SOME sort of windowed/GUI-based OS on that box and just call it quits.  But I figured I'd try the forum to see what might come up.

It should be made known that I am dealing with the infamous Intel 845 graphics card problem.  There are three or four posts dealing with this issue alone, the most notable two being:
[http://ubuntuforums.org/showthread.php?t=965478](http://ubuntuforums.org/showthread.php?t=965478) and [http://ubuntuforums.org/showthread.php?t=970037](http://ubuntuforums.org/showthread.php?t=970037) Based on what I've read, my system specs, and the symptoms experienced, this is absolutely the same issue.  HOWEVER, I appear to be the only one in the world who is installing for the first time (as opposed to upgrading, or doing a fresh install over a previous version).  This is why I created a new thread as opposed to adding to that one.  In that sense, it IS a different issue.

Some posts cite several various solutions, most frequently "the Jerry fix"... but these seem to indicate that there is either (a) some rescue mode I can boot into or (b) that I have some CLI to use.  Neither seem available to me unless I am overlooking something glaringly obvious here...

A quick summary:
1 - I downloaded the most recent version and burnt the image to disk.  The disk prompts me to select a setup option, etc.  No "rescue mode" or CLI access seems accessible.  In fact, the CD help displayed in GRUB when viewing install options explicitly states that the CD has no rescue/recovery mode because it doesn't need one since a CLI is available. (Still, I cannot figure out how to get to any CLI with this disk...)
2 - Check CD contents test passed fine. Memory tests passed fine.
3 - After the install process loads enough of the OS into memory to "boot" and continue installation, the screen goes black after loading.  The process dies at this point.
4 - The three available install modes fail in the exact same manner.  There seems to be absolutely no difference in selecting "run without affecting windows", "install," and "safe graphics mode". (Sorry for incorrect verbiage, but I'm at work and forget the exact mode names.  There are only three selections to be made, so you know what I mean).

Ultimately, my question is: "How do I do a FRESH INSTALL of Ubuntu 8.10 in the face of the 845 graphics problem?"

Also note that VERY similar behavior is experienced with version 7.xx of Desktop, although I will occasionally see part of a wallpaper (additionally, in that version I can at least get to a CLI with Ctrl+Alt+F1 if I use safe mode if I am lucky enough for it to load to the point it displays the wallpaper).

Sorry if this should be moved to the DELL threads, but I figured I'd start here in hopes of getting more views on the issue.  I GREATLY appreciate any insight anyone might have.  Ideally, someone will write me and point out that I'm making some completely idiotic and easily-fixable oversight.  I would LOVE to use this OS instead of XP...  Thanks in advance!!!!

---

### Post by Jim DeLois on 2008-11-04
Quick update:  I just found another slightly related post...  [http://ubuntuforums.org/showthread.php?t=965237](http://ubuntuforums.org/showthread.php?t=965237)

It's not directly related, but it is somewhat similar.  In it, I learned more about the "alternate version install."  That picture hadn't really been accurately painted for me and I didn't really understand what that was or meant, but something in the post above cleared it up pretty quickly for whatever reason. As that is obviously the next logical step to take, I'm downloading it now and begin the next iteration of trying out the procedures I've been reading about.  I will update with more information if/when able for the sake of others that might be experiencing this same thing.

I'm also updating again to bump this post  ;-)

---

