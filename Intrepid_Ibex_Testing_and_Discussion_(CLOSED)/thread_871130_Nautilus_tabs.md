---
title: "Nautilus tabs"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-07-26
I just noticed an odd thing. I opened a folder from a bookmark in a new tab. The folder's contents is large enough to need a scrollbar, but you don't get one. If you open the bookmark in the existing tab, the scrollbar is there.

Anyone else able to duplicate this?

---

### Post by phenest on 2008-07-26
The same thing happens if you have a folder open that has a scrollbar, and click File > New Tab. The new tab does not have a scrollbar, yet it's the same folder.

---

### Post by lapcat66 on 2008-07-26
Working as expected for me in Nautilus 2.23.5.1.  The bookmark opened in a new tab has a scrollbar.

---

### Post by Lev.NL on 2008-07-26
I have the same issue, the upstream bug-report is here: [http://bugzilla.gnome.org/show_bug.cgi?id=542396](http://bugzilla.gnome.org/show_bug.cgi?id=542396) . launchpad bug-report is here [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/251809](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/251809)

---

### Post by phenest on 2008-07-27
To add to this:

I open my home folder in a new tab. Now select the new tab. Everything seem ok. Open one of your folders. Nautilus freezes.

Now this may not work, as it doesn't with me except for one folder. This particular folder is my download folder which has no folders and some large files (iso's, mpg's, etc). I can reproduce it, but with only one folder.

---

### Post by Gina on 2008-07-27
Hmm... I can't get Nautilus to open anything other than sub-directories of the / filesystem.  It won't mount any other partitions.  (At least, not from the GUI)  Will be investigating further...

---

### Post by kahlil88 on 2008-07-27
Whoa, hold the phone...what's this I'm hearing about Nautilus and tabs? The feature I've been dying to have since I switched to Gnome from KDE!

---

### Post by amano on 2008-07-27
Yeah, strange times. With version 4 KDE switched to Dolphin as the standard file manager which lacked tab-support and at the same time Nautilus gets tabs. Interesting.

But what I hear is that tabs will reappear in KDE/Dolphin 4.1.

---

### Post by ronacc on 2008-07-27
@ Gina yes I,ve noticed that also , I added comments to that effect to the original 'double mount" bug .

---

### Post by phenest on 2008-07-28
> **phenest said:**
> To add to this:

I open my home folder in a new tab. Now select the new tab. Everything seem ok. Open one of your folders. Nautilus freezes.

Now this may not work, as it doesn't with me except for one folder. This particular folder is my download folder which has no folders and some large files (iso's, mpg's, etc). I can reproduce it, but with only one folder.

I think there was something wrong with that folder. I moved the iso's into another folder (I had to use a terminal) and the freezing has ceased. Not sure what that was about.

---

### Post by waspbr on 2008-07-28
I am happy to report that there ares no issue on my nautilus :D

---

### Post by kahlil88 on 2008-07-29
Can I run the unstable version of Nautilus on Gnome 2.22.3, and is there an Ubuntu package for it? I'd like to dump PCManFM. I really only use it for the tabs!

---

### Post by alopecoid on 2008-10-07
> **kahlil88 said:**
> Can I run the unstable version of Nautilus on Gnome 2.22.3, and is there an Ubuntu package for it? I'd like to dump PCManFM. I really only use it for the tabs!

This is exactly what I would like to know! I am running Hardy, which has nautilus without tabs... but I would love to run the most stable version of nautilus available that *does* have tabs. Is there any [easy] way to do this?

Thank you!

---

### Post by jdeslip on 2008-10-24
Just installed 8.10 - and whenever I open a new tab in nautilus the scrollbar on the first tab dissapears.  This sounds a lot like the problem in the original post.  This makes me sad - tabs in nautilus are clearly not working well yet.

---

### Post by heavensblade23 on 2008-10-24
Why can't your drag and drop onto a tab?  That limits some of the usefulness.

---

