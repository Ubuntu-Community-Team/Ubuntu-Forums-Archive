---
title: "Why is Banshee so slow?"
date: 2009-07-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-07-27
I've just filled Banshee 1.4.3 with 5000 songs, the SQLite-DB has 12MB, and it performs rather slow. Using the search function, sorting, clicking on artists, scrolling through artists - everything feels sluggish compared to Rhythmbox with its XML-"DB".

Also updating to version 1.5.0 from the banshee-unstable-team's PPA didn't change a thing.

Why is it so slow? Is it Mono? Is it SQLite? Is it even normal? :confused:

PS: I'M NOT INTERESTED IN ANY POLEMIC ANTI-MONO BLURBS!

---

### Post by Joe_Bishop on 2009-07-27
i believe it's sqlite, mono itself is not so dramatically slow.
But, of course, they will be talking about "scalability". I'm sure scalability should not be payed a high price of general slowness.

---

### Post by froggyswamp on 2009-07-27
> **MacUntu said:**
> 
 PS: I'M NOT INTERESTED IN ANY POLEMIC ANTI-MONO BLURBS!
That also means that **if** Mono's to blame then you don't wanna know the truth. Interesting. My Java app has a slow startup, but, don't dare to blame Java for that!!

---

### Post by directhex on 2009-07-27
> **MacUntu said:**
> I've just filled Banshee 1.4.3 with 5000 songs, the SQLite-DB has 12MB, and it performs rather slow. Using the search function, sorting, clicking on artists, scrolling through artists - everything feels sluggish compared to Rhythmbox with its XML-"DB".

Also updating to version 1.5.0 from the banshee-unstable-team's PPA didn't change a thing.

Why is it so slow? Is it Mono? Is it SQLite? Is it even normal? :confused:

PS: I'M NOT INTERESTED IN ANY POLEMIC ANTI-MONO BLURBS!

Scrolling in Banshee being slow is a feature.

Okay, done laughing yet?

Now?

...
...


......

Okay. Scrolling in Banshee being slow is a feature. It really is. Here's the specifics:

In Rhythmbox, your entire library is loaded into a GTK ListStore object, which uses a bunch of RAM for every entry. It's pretty quick to filter entries (e.g. when you search), and it's pretty quick to scroll, and so on, because every song's data is in RAM and immediately available. As a result, Rhythmbox can balloon somewhat as your library grows much bigger, and more data needs to be stored in the ListStore.

Now, Banshee has a different approach. It has a special custom ListStore, which only contains the items you see plus 20 (10 above, 10 below). WHen you scroll, search, sort, etc, it's doing a new SQLite query to refresh the data it shows in its ListStore window. As a result, it doesn't use more RAM with bigger libraries, since it isn't storing your library in RAM. It has *OTHER* RAM consumption issues on other places, sure, but it won't grow fatter with library size, even (in theory) on a 100,000 track or more library.

---

### Post by directhex on 2009-07-27
Issues meaning bugs i.e. it'll stop eating RAM needlessly when bugs are fixed

---

### Post by utUtu on 2009-07-27
> **MacUntu said:**
> 

Why is it so slow? Is it Mono? Is it SQLite? Is it even normal? :confused:

PS: I'M NOT INTERESTED IN ANY POLEMIC ANTI-MONO BLURBS!

No need to shout.  ):P

---

### Post by MacUntu on 2009-07-27
> **froggyswamp said:**
> That also means that **if** Mono's to blame then you don't wanna know the truth.
No, that deduction is false.

> **directhex said:**
> Scrolling in Banshee being slow is a feature.

Thanks. I think it's pretty cool to have programs that perform slow hardware-independent. #-o I really hope there are plans to optimize this behavior, because right now Banshee is no option for me.

> **utUtu said:**
> No need to shout.  ):P
I've read enough blabla about Mono, so that was intended. :P

---

### Post by gnomeuser on 2009-07-27
If there is a specific thing that makes it unbearably slow to detect it with metrics:

banshee-1 --debug --debug-sql --redirect-log

Finish the program right after the problem space has been exercised. That will put a log with timings into .config/banshee-1/ of the run. This can then be attached to a bug report over at bugzilla.gnome.org against the banshee component with an explanation of what you did to cause the slowness.

It is also adviced that you try to repeat with a version from git (or the upcoming 1.5.1 release) the banshee-daily ppa will provide this for you easily. make sure to backup .config/banshee and .cache/banshee (along with any directories in here touched by banshee plugins to be sure, such as album-art and mirage). This should allow smooth rollback if you find git to problematic (Though naturally we would love to have you as a tester and would handle your bugs as best we can).

---

### Post by MacUntu on 2009-07-27
Thanks for the info. Will try the dailies later this day but following directhex' posting I fear it's a design issue (unless someone can assure me that 5000 entries should be sortable within a split second, because that's what I expect on non-ancient hardware - no ifs, ands, or buts).

---

### Post by castrojo on 2009-07-27
It shouldn't be that slow, my sorting and searching is pretty instant.

---

### Post by MacUntu on 2009-07-27
Short comparison clip: [http://www.youtube.com/watch?v=WboqHisYJWo](http://www.youtube.com/watch?v=WboqHisYJWo)

The lack of visual click feedback doesn't help but the difference is obvious where I repeatedly clicked the the titel/name column.

According to 1.5.0's log, sorting takes about a second each time.

---

### Post by deathsshadow77 on 2009-07-27
> **whiprush said:**
> It shouldn't be that slow, my sorting and searching is pretty instant.

Same here for the most part. 

Looking at this my only issue is a lack of visual feedback from banshee. As you show in the video when you click to sort in banshee nothing changes on the bar where you click. I understand that it is slower but I think that the lack of the visual feedback you get with rhythmbox makes it seem slower than it actually is. Scrolling on the other hand seems the same in both applications.

---

### Post by zekopeko on 2009-07-27
might I suggest filing a bug at [http://bugzilla.gnome.org/browse.cgi?product=banshee](http://bugzilla.gnome.org/browse.cgi?product=banshee) ?
provide logs and suggest a solution ie. faster feedback.

---

### Post by MacUntu on 2009-07-27
Before I can file a bug I need to know if what I'm seeing isn't what I should be seeing. ;) A whole second for sorting seems a lot but I need to test the dailies first and will also check the performance on a second system.

---

### Post by zekopeko on 2009-07-27
@MacUntu

well even then a feature bug would be useful. perhaps it only needs tweaking and it's not a "real" bug. If it's a design limitation then providing feedback immediately could lessen the perception of the problem. like the column clickable status could be reflected immediately and a little throbber could be shown in the column title you clicked while the list itself is asynchronously populated with the relevant info.

---

### Post by Joe_Bishop on 2009-07-27
It's not a good reason - their "scalability" is not a thing general user strongly need in. On the contrary, they need instant response which is impossible with banshee. So, you want banshee to be default so far? I only have heard banshee should be default because it's "looks nice". Is it really a reason to choose **musical player**? I'm sure it's not.

---

### Post by zekopeko on 2009-07-27
> **Joe_Bishop said:**
> It's not a good reason - their "scalability" is not a thing general user strongly need in. On the contrary, they need instant response which is impossible with banshee. So, you want banshee to be default so far? I only have heard banshee should be default because it's "looks nice". Is it really a reason to choose [b]musical player[/]? I'm sure it's not.

And then you get users complaining how it uses "too much" RAM.
But anyway this just seems like a bug because two people report differently. 
BTW Banshee is a **media player**.

---

### Post by Joe_Bishop on 2009-07-28
General user doesn't have such a huge library for RB to exceed banshee's memory usage. For me, with my 200Gb lossless collection, RB takes a less memory than banshee but operates much faster. And general user doesn't have so many videos to need in collection software to manage it. So, banshee will have quite useless features like videos management, photo management, etc, which will make it a bloated one. So, in my opinion, it can be default in a thing like "ubuntu media center", but not in regular ubuntu.

---

### Post by Joe_Bishop on 2009-07-28
> And then you get users complaining how it uses "too much" RAM.
They rarely complain about it. If they do, they can install your lovely banshee, without any library watching, etc.

---

### Post by ktulu77 on 2009-08-04
For me too, Banshee seems very slow, not only for sorting songs in the playlist.

For example, when I click on an artist in my musical library, it takes one or two seconds to display artists albums on the right.

When I click on an album, again, it takes approximately one seconds to display them in the bottom of the window.

I don't know if it is a bug, but with rhythmbox, theses actions are almost instantaneous. 

I have approximately 50GB of music.

---

### Post by EmEyKeYwAy on 2009-09-16
It's working slow for me too now. My collection is 200 GB of flac (8900 files), this problem is related to sqlite then?

I willl have to go back to Rhythmbox again.

---

### Post by Podex on 2009-09-16
By the way (a little off topic), just in case someone didn't know yet: Banshee will not replace Rhythmbox as the default player in Karmic. See [https://wiki.ubuntu.com/DesktopTeam/ReleaseStatus](https://wiki.ubuntu.com/DesktopTeam/ReleaseStatus)

> POSTPONED: rhythmbox &#8594; banshee (desktop-karmic-default-media-player-choice); this will probably not make it, since banshee upstream development won't catch up in time for Karmic

---

### Post by knarf on 2009-09-16
Isn't it obvious? This is the result of a complot by the [MAFIAA]("http://mafiaa.org/") to track down obvious copyright infringers. Anyone who has a music collection big enough for Banshee to run slow is obviously stealing their Precious.

Expect a visit from the parasites in suits shortly...

---

### Post by directhex on 2009-09-16
Rhythmbox stores your entire music library in RAM (in a liststore GObject)

Banshee doesn't, and runs a SQLite query for every action.

That's why it can seem slower in Banshee - it doesn't use more RAM linearly with library size

---

### Post by zekopeko on 2009-09-16
> **directhex said:**
> Rhythmbox stores your entire music library in RAM (in a liststore GObject)

Banshee doesn't, and runs a SQLite query for every action.

That's why it can seem slower in Banshee - it doesn't use more RAM linearly with library size

Couldn't it be made to put the entire library in memory if there is enough RAM ,and if the system load increases mark it as a high priority target of RAM cleaning? Or some such thing.

---

### Post by directhex on 2009-09-16
> **zekopeko said:**
> Couldn't it be made to put the entire library in memory if there is enough RAM ,and if the system load increases mark it as a high priority target of RAM cleaning? Or some such thing.

In terms of how the app is architected... I'm not sure. You're not necessarily talking about storing the library in RAM, but about changing the type of store and view objects, and overriding all click/search behaviour, essentially building two code paths, with no way I can think of casually to pick between them.

For curiosity sake, you could try forking the main Banshee GUI (Nereid) and making a more "conventional" use of widgets, to see how it performs in terms of memory consumption. Shouldn't need more than a few hundred lines of code changed - the big issue is how to bring both approaches together

It's not as simple as changing the existing object to store more data than it does (viewable+20), since things like column sorting act on invisible objects, so you need *all* entries in RAM in order to run that kind of operation with a conventional widget

---

### Post by ktulu77 on 2009-09-17
I don't think this speed problem is due to sqllite.

If I remember correctly, Amarok 1.4 was also using a sqllite database by default and the searches where very quick.

---

### Post by gnomeuser on 2009-09-17
> **zekopeko said:**
> Couldn't it be made to put the entire library in memory if there is enough RAM ,and if the system load increases mark it as a high priority target of RAM cleaning? Or some such thing.

I think a more fruitful approach might be to do some data collection to determine what is the optimal number of tracks to cache for the widget. I don't remember seeing anyone providing data to see where the sweet spot is between memory consumption and smoothness in scrolling.

You could also run banshee with the --debug-sql --debug and --profile options to see where we are hitting hit request times and other matters of fun.

---

