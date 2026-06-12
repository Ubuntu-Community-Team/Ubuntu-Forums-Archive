---
title: "Promote f-spot 0.5 for a feature freeze exception!"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Teamgeist on 2008-09-19
Hi.
A new and improved Version of f-spot, the default photo managing software of Ubuntu, came out two days ago and has a ton of bug fixes and a couple of new features in it.

    * new sidebar, reworked editors
    * color profile support
    * duplicate detection at import
    * reworked db interractions, with O(1) queries
    * reducing and batching db access
    * light-speed tagging
    * FullScreen mode enhancement
    * new extensions, updated docs, updated translations
    * hundreds of bugfixes 


Especially the new sidebar and the reworked editors are interesting, as they will make it even easier to quickly edit pictures (red eyes, color adjustment, etc).

Also color profile support seems pretty cool since usually pictures on the monitor screan look bright and natural, but if you print them paper they look not too brilliant.
Color structures correct the image in view of physical opportunities of devices of a conclusion. So it is is possible to facilitate the life of users and present them too more functionality with adding the support of color profiles in f-spot.

(taken from: [http://code.google.com/soc/2008/gnome/appinfo.html?csaid=EA52069810BFAB27](http://code.google.com/soc/2008/gnome/appinfo.html?csaid=EA52069810BFAB27) )

As I think Ubuntu should ship the latest and greatest software that open source has to offer, we should promote F-spot 0.5 for Intrepid.

Bugreport here: [https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/271895](https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/271895)

So get going and comment on the bug.
Also if someone could come up with a diffstat for the new version would be awesome.

Thank you!

---

### Post by Bou on 2008-09-19
Meh. I would if only it had Inotify support. These other changes you mention are OK, I guess, but only Inotify really interests me.

---

### Post by Nullack on 2008-09-19
Bug spam!

Please refer to the Ubuntu wiki for bug best practices.

Its better to subscribe to a bug to show your support.

---

### Post by olskar on 2008-09-19
:( Everything gets updated after feauture freeze! Why why why! :(

---

### Post by michelinux on 2008-09-21
In the while, if you want to try **F-Spot 0.5.**0 and you are too lazy to compile it, I packaged it for both Hardy and Intrepid. Further infos and instructions on 
[URL="http://www.soccio.it/michelinux/2008/09/21/new-f-spot-050-build-for-ubuntu/en/"]
http://www.soccio.it/michelinux/2008/09/21/new-f-spot-050-build-for-ubuntu/en/[/URL]

Unfortunately it doesn't want to build on amd64 and I still did not understand why. If you have any idea, let me know.

---

### Post by Mr. Picklesworth on 2008-09-21
Michelinux, 0.5 built / installed / ran for me just fine on Hardy. Does 0.4 build for you?

---

### Post by Yannick Le Saint kyncani on 2008-09-21
> **olskar said:**
> :( Everything gets updated after feauture freeze! Why why why! :(

Yeah, f-spot-0.5 does not fix any major issue so I hope the feature freeze will be enforced and make intrepid reasonably bug-free :)

---

### Post by michelinux on 2008-09-21
Sorry, Mr. Picklesworth, I did not try to build any of the 0.4 serie. Are you using a 64bits machine? Have you installed any extra or more updated package (expecially Mono related) that are not included in the official Ubuntu repositories?
Thanks.

---

### Post by rbmorse on 2008-09-21
0.5 actually crashes (a lot) for me on Ubuntu 8.10 (32-bit). I don't think I could support a freeze exception at this point, either.

---

### Post by michelinux on 2008-09-22
> **rbmorse said:**
> 0.5 actually crashes (a lot) for me on Ubuntu 8.10 (32-bit). I don't think I could support a freeze exception at this point, either.
rbmorse, are you using a package or have you compiled F-Spot 0.5.0 from scratch?

---

### Post by olskar on 2008-09-22
> **rbmorse said:**
> 0.5 actually crashes (a lot) for me on Ubuntu 8.10 (32-bit). I don't think I could support a freeze exception at this point, either.


Run f-spot with --debug , can you see what images make it crash? for me it was gif-files

---

### Post by olskar on 2008-09-22
> **michelinux said:**
> In the while, if you want to try **F-Spot 0.5.**0 and you are too lazy to compile it, I packaged it for both Hardy and Intrepid. Further infos and instructions on 
[URL="http://www.soccio.it/michelinux/2008/09/21/new-f-spot-050-build-for-ubuntu/en/"]
http://www.soccio.it/michelinux/2008/09/21/new-f-spot-050-build-for-ubuntu/en/[/URL]

Unfortunately it doesn't want to build on amd64 and I still did not understand why. If you have any idea, let me know.


Hi, 0.5.0.1 has now been released fixing the issue I describe above, would love to see this in your ppa, thanks :)

---

### Post by michelinux on 2008-09-23
Done.
It's in the ppa now.

---

### Post by rbmorse on 2008-09-23
Please ignore.

How does one delete one's post?

---

### Post by rbmorse on 2008-09-23
> **olskar said:**
> Run f-spot with --debug , can you see what images make it crash? for me it was gif-files

In my case, deleting images from F-spot's database caused it to crash. About every third or fourth delete did it.

---

### Post by vikrant82 on 2008-09-24
I wished I had'nt stumbled across this thread. Well I ended up compiling and installing f-spot for myself. And then for some reason I uninstalled it. When I ran the older version again, It gladly, ruthlessly complained that it cannot read the database file and created a new one.

Um, Well, so I lost all my tagging.Yes, all meticulous, dedicated late night taggings. 

The worst part was it pretty much overwrote its db file, ~/.gnome2/f-spot/photos.db

What kind of lame program that knows that my older version doesn't support this new db, would do that.

So be it. Got my reward for being pesky. I know there is no chance of recovery. 

And yes, This thing can never exit gracefully. It wants to be killed all the time.

[B][U]
Please don't go back to older f-spot 0.4.x from 0.5. This would kill all your tagging information.[/U][/B]

Edit: I recovered my tagging from that shiny, well kept backup db file that f-spot kept exactly for situations like these.

---

### Post by zombiepig on 2008-09-24
I had that happen to me once when I was testing a svn build - but from memory, it saved a backup copy of the database somewhere in my home directory. It might be worth doing a search for .db files in all the hidden config files to see if this has happened for you...

---

### Post by michelinux on 2008-09-24
So sorry for your database.
Try to have a look in your home and see if there is a file called something like **photos-20080924-0.db**

This is a backup of your database made by F-Spot.

---

### Post by vikrant82 on 2008-09-24
> Try to have a look in your home and see if there is a file called something like photos-20080924-0.db :)

Now that's a life saver.

I am pretty sure I looked for all .db files, but looks like, my distressed state wanted me to believe that its not there. :)

Thanks, I am back in business.:popcorn:

---

### Post by blom on 2008-09-24
f-spot 0.5 (and 0.5.0.1) is seriously buggy compared to previous versions and I wouldn't recommend anybody try it yet that heavily relies on it.

It basically doesn't start for me any more at all (well, starts then crashes).  And while I can fix it by effectively resetting all of the data for the given user (deleting the image database and gconf stuff) that's clearly not a fix.

It's my own fault for trying it so early, but at a time when I most need it, it's not working at all :-)

I did however keep a copy of the database (somehow I saw this coming) so I can go back to the old version, just some of the new features I was interested in.

---

### Post by Seq on 2008-09-24
In preferences it is a good idea to check "Write metadata to file". It works, and upon Import to a new f-spot you would have to recreate your tag heirarchy and set the proper thumbnails to be used for each, but all the tags will be imported and exist. I've managed to recover via this method in the past.

And including the afore mentioned photos.db in your backup scheme is a good idea as well. I have also learned in the past ;)

---

### Post by bash on 2008-09-29
I installed the new version from the PPA (0.5.0.1). Really like it so far. Only thin that bugs me, is that I can not change the folder to save the pictures in. In the options menu it is just greyed out. And by default it is set to /photos or if that doesn't exist to your home folder. I would love to change it, so that the photos get saved to /pictures/photos. Anyone know how to do this.

---

### Post by ntetreau on 2008-09-29
> **bash said:**
> I installed the new version from the PPA (0.5.0.1). Really like it so far. Only thin that bugs me, is that I can not change the folder to save the pictures in. In the options menu it is just greyed out. And by default it is set to /photos or if that doesn't exist to your home folder. I would love to change it, so that the photos get saved to /pictures/photos. Anyone know how to do this.

In my f-spot 0.5, I can change the path, it is not grayed out.

---

### Post by zombiepig on 2008-10-09
Didn't expect this to happen, but 0.5.0.2 just got in :D

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008315.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008315.html)

---

### Post by olskar on 2008-10-09
> **zombiepig said:**
> Didn't expect this to happen, but 0.5.0.2 just got in :D

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008315.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008315.html)

 :O Wow, where did that come from? Nice move :)

---

### Post by canabal on 2008-10-09
Very nice, this is not an LTS so as long as it is not a whole new version we should be pushing for more stuff for sure.  (with the exception of OOo3, that should be in for SURE)

---

