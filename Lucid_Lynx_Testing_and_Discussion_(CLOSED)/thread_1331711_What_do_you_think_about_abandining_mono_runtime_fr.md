---
title: "What do you think about abandining mono runtime from lucid?"
date: 2009-11-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BbICEP on 2009-11-19
So, they are only tomboy and f-spot in the live cd, but gnote is lighter, start quicker and eats 3 times less memory than tomboy. On the other hand, F-Spot doesn't seem to be a good solution for photo management: it's slow, can't work with the file system (I still prefer working with FS, it's too much unnecessary work with taging, and in most cases it just emulates FS) and it's still buggy. So, why do we need in mono-runtime in the default install.

---

### Post by Merk42 on 2009-11-19
So you propose Gnote instead of tomboy, but what is your proposal to use for photo managent other than F-Spot?

---

### Post by BbICEP on 2009-11-19
> **Merk42 said:**
> So you propose Gnote instead of tomboy, but what is your proposal to use for photo managent other than F-Spot?
No one. They are all have a really bad quality. In addition, linux is not used widely by photographers, since there is no Photoshop here, so, there is no serious need to have photo management software. If someone need it, he can install Picasa, because it's way better than F-Spot. But removing mono let us to save GIMP, and it's much more valuable, because the lack of **drawing** software is just ridiculous.

---

### Post by zekopeko on 2009-11-19
> **BbICEP said:**
> No one. They are all have a really bad quality. In addition, linux is not used widely by photographers, since there is no Photoshop here, so, there is no serious need to have photo management software. If someone need it, he can install Picasa, because it's way better than F-Spot. But removing mono let us to save GIMP, and it's much more valuable, because the lack of **drawing** software is just ridiculous.

So let me get this straight. You want to remove a FLOSS application and you propose a closed source application that works under Wine and is not supported as of 3.5 on Linux?
And not to mention the two largest OS vendors both have photo management applications by default in their products; Window has Live Gallery and OSX has iPhoto. Both aren't targeted at pro or semi-pro photographers but at average users that just want to sort their photos and share them with friends.

And GIMP really isn't for average users. How many average users have to draw something in a semi-professional level app like GIMP?

---

### Post by steeleyuk on 2009-11-19
Gthumb was a relatively popular choice prior to its removal from the install back around 8.04... as a replacement for F-spot that is.

---

### Post by slumbergod on 2009-11-19
Mono and its associated applications should be an opt-in option rather than forced on everyone by default. Since the inclusion of it is very controversial it is better to just have it in the repos and let users decide.

---

### Post by zekopeko on 2009-11-19
> **BbICEP said:**
> So, they are only tomboy and f-spot in the live cd, but gnote is lighter, start quicker and eats 3 times less memory than tomboy. On the other hand, F-Spot doesn't seem to be a good solution for photo management: it's slow, can't work with the file system (I still prefer working with FS, it's too much unnecessary work with taging, and in most cases it just emulates FS) and it's still buggy. So, why do we need in mono-runtime in the default install.

Just to say something about F-spot. The core team lost the person that started it all at the end of 2008 so F-spot has been neglected a little.
But if you watch planet.gnome.org you will see that the development is starting to pick up. Some pretty nice things are coming (like face recognition). 
And F-spot in 9.10 has file system view if you want it.

---

### Post by zekopeko on 2009-11-19
> **slumbergod said:**
> Mono and its associated applications should be an opt-in option rather than forced on everyone by default. Since the inclusion of it is very controversial it is better to just have it in the repos and let users decide.

No. There is nothing controversial about it. Some people might like to pretend like it is but they are either misinformed, paranoid or simply trolls.

---

### Post by Merk42 on 2009-11-19
> **zekopeko said:**
> So let me get this straight. You want to remove a FLOSS application and you propose a closed source application that works under Wine and is not supported as of 3.5 on Linux?
And not to mention the two largest OS vendors both have photo management applications by default in their products; Window has Live Gallery and OSX has iPhoto. Both aren't targeted at pro or semi-pro photographers but at average users that just want to sort their photos and share them with friends.

And GIMP really isn't for average users. How many average users have to draw something in a semi-professional level app like GIMP?

No no, he's saying 
"In addition, linux is not used widely by photographers, since there is no Photoshop here, so, there is no serious need to have photo management software."

However GIMP is
" much more valuable, because the lack of drawing software is just ridiculous."

So F-Spot is the equivalent of Photoshop and no one needs to manage photos but they all need to edit them more than the usual red eye / cropping :confused:

> **zekopeko said:**
> No. There is nothing controversial about it. Some people might like to pretend like it is but they are either misinformed, paranoid or simply trolls.
And there's the real "reason" for this thread.  Yet another Mono thread.

---

### Post by steeleyuk on 2009-11-19
> And there's the real "reason" for this thread. Yet another Mono thread.

If people can stay away from the political side of Mono then it is a reasonable question.

A bit of discussion took place about adding Gnote due to its reduced size (amongst other things). However it was said that once all the shared libraries were added up (both Mono and C), they worked out about the same in terms of overall disc space.

My thought is that if (remember that an if) you remove one of the Mono apps from the default install, you might as well remove the other plus the entire framework and save the space (providing the replacements are up to standard).

---

### Post by Merk42 on 2009-11-19
> **steeleyuk said:**
> If people can stay away from the political side of Mono then it is a reasonable question.
I hope we all can.

> **steeleyuk said:**
> My thought is that if (remember that an if) you remove one of the Mono apps from the default install, you might as well remove the other plus the entire framework and save the space (providing the replacements are up to standard).
I understand, but my point to the original post was that no replacement was suggested for F-Spot
Then the later logic behind that was just confusing to me and zekopeko

---

### Post by zekopeko on 2009-11-19
> **steeleyuk said:**
> If people can stay away from the political side of Mono then it is a reasonable question.

A bit of discussion took place about adding Gnote due to its reduced size (amongst other things). However it was said that once all the shared libraries were added up (both Mono and C), they worked out about the same in terms of overall disc space.

My thought is that if (remember that an if) you remove one of the Mono apps from the default install, you might as well remove the other plus the entire framework and save the space (providing the replacements are up to standard).

Well that is the problem. Mono discussions aren't about technical merit (most of the time) as they should be but about politics.
I have no problem with replacing Tomboy or F-spot if the replacements are nicer. As of now there are no serious replacements. Tomboy has more people working on it and as I said F-spot is getting better as of late.
Not to mention that Lucid+1 will most likely have Banshee instead of Rhythmbox which is another mono app (but it really shouldn't matter that it's a mono app).

---

### Post by gnomeuser on 2009-11-19
[The technical board hath spoken](http://ubuntuforums.org/showthread.php?t=1200946) - Roys anti mono trolls can go back to their cave now. Mono is the foundation for important quality applications now and in the future, no danger to Ubuntu or it's users has been found.

[For those still unconvinced Jo Sheilds (Directhex) one of the Mono maintainers for Ubuntu has made a Mono-less Ubuntu spin avaiable](http://www2.apebox.org/wordpress/linux/210/)

End of thread!

---

### Post by jpeddicord on 2009-11-19
This thread is going downhill rather quickly and brings nothing new to the table, so I'm going to close it. Debating Mono is beating a dead horse - as gnomeuser said, the TB has made their statement on Mono: it isn't going anywhere soon.

If you believe that there is a point in re-opening this thread, please post in the Resolution Center.

---

