---
title: "about tracker"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by manfer on 2009-10-16
If you uncheck enable index in general tab of Preferences->Search and Index, should trackerd run at all?

In my system it was running anyway. And it was making system unusable.

I even tried to configure it to slow and to minimal memory usage and it was even worst.

Finally I had to get rid of tracker that besides I have never used:

<code>
sudo apt-get --purge remove tracker tracker-search-tool tracker-utils
</code>

I'm sorry to mention because I have been for some years a happy ubuntu user but I'm very upset with this karmic release.

From a system working perfect and very smooth even running compiz and this system where I use ubuntu is starting to be an old one (I was very very happy of what ubuntu was able to do with this machine) to an almost unuseful system in 6 months. That's odd.

Let's see if now without tracker and without compiz (I have disabled it too) I have a better experience with karmic. And let's see if the next two weeks upgrades makes it go better. I hope so.

I suppose with a more recent computer these kind of problems probably are not being perceived but with a system like the one I use with ubuntu was a very drastic performance change, from jaunty to karmic.

---

### Post by Sealbhach on 2009-10-16
Really? Did Tracker slow your system down so much that it was unusable? :shock:

.

---

### Post by manfer on 2009-10-16
Really, really, and I dont know why, and I dont know why it was running when I had it disabled in Search and Index preferences.

Which is the only question I have in this thread. If you uncheck on Preferences Search and Index the check box Enable Index, should tracker be running?

Unchecking that isnt tracker disable?

If it is. I don't understand why in my system it was doing its own wish and was running anyway.

If it is not, where a user can disable tracker? I suppose uninstall is not the only way to disable tracker.

---

### Post by manfer on 2009-10-16
And as an example of what I mean of unusable was this:

I was downloading a file from internet (firefox running), trakerd started to run too, and I could not do anything else, the system was almost frozen with those too task. With those two task running I was not able to write here, the typing was not appearing, it was hard to change from one window to another. In my opinion that's an unusable system.

When the download finished, I stopped trackerd process, I remove all tracker, I restarted and then I wrote the thread.

---

### Post by manfer on 2009-10-16
And it is not the first time I notice the degradate performance but I always looked at the system monitor and didn't notice trackerd being wasting so many resources. But system monitor shows memory, CPU, ... usage, and maybe the resource trackerd is eating is the total hard drive read/write bandwidth.

I hope now I get rid of it the system starts to go better.

---

### Post by tekstr1der on 2009-10-16
Well, tracker is not included in karmic, so I guess you should be all set then?

---

### Post by manfer on 2009-10-18
Well, maybe too soon to be sure but it seems tracker was the responsible of my poor system performance.

Now that it is no more on my system all goes better again. I have even enabled again the extra visual effects because I wanted to try docky and it was needed and the performance looks fine.

---

### Post by hanzomon4 on 2009-10-18
Tracker is not installed by default in Karmic, did you upgrade or install fresh? Even if you know what you're doing this can cause bizarre problems.

---

