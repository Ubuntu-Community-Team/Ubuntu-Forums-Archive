---
title: "Ubuntu one music store problem(maybe)"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sixthwheel on 2010-04-09
Anyone purchase anything from the Ubuntu One music store yet?
I bought a whole album(CD?) containing 17 songs.
It downloaded 10 songs in about 10 minutes, the rest I've been waiting on for the past 15 minutes. Did it stall?
There is a shaded are next to each song that says, " Transferring to your Ubuntu one storage"

If I can't get all the songs downloaded, what do I need to do?..Did I just lose my money?

---

### Post by Ellipsis on 2010-04-09
Are you still waiting?

My problem is that I get "download unavailable" for every single song after clicking "download".

---

### Post by castrojo on 2010-04-09
This is a known bug and is being worked on: [https://bugs.edge.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755](https://bugs.edge.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755)

For the albums I bought it burst a few songs and then stalled out and started again.

---

### Post by sixthwheel on 2010-04-09
> **Ellipsis said:**
> Are you still waiting?

My problem is that I get "download unavailable" for every single song after clicking "download".

yes I am. Not a big problem since I know we're still in Beta, and I'm sure if something happens I'll get my money back or get credited with songs.

Also is there an option to not have it sync directly with my ubuntu one storage?

---

### Post by sixthwheel on 2010-04-09
> **whiprush said:**
> This is a known bug and is being worked on: [https://bugs.edge.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755](https://bugs.edge.launchpad.net/rhythmbox-ubuntuone-music-store/+bug/551755)

For the albums I bought it burst a few songs and then stalled out and started again.
I guess I'm not alone, thanks.

---

### Post by castrojo on 2010-04-10
> **sixthwheel said:**
> Also is there an option to not have it sync directly with my ubuntu one storage?

The way it was explained to me is that it has to go there first so that it can then be downloaded to all the computers associated with your Ubuntu One account.

---

### Post by sixthwheel on 2010-04-10
That's fine as long as I can delete it later to save room on my 2 Gig limit and not have it disapear from Rhythmbox

---

### Post by ElSlunko on 2010-04-10
Had the same issue and eventually got all my songs.

---

### Post by StudioDave on 2010-04-15
> **sixthwheel said:**
> Anyone purchase anything from the Ubuntu One music store yet?

Not yet, and not for lack of trying. The transaction never completes, I just wait for the 504 Gateway Timed-out message that pops up after a few minutes. Grrr... Maybe I'm missing some step ? I'm signed on to U1, Rhythmbox connects to the service, I can browse the catalog and select songs for purchase. But when I click Checkout that's all she wrote. After a while I get the 504 message and can't even reconnect to the store. :(

I'm running the live disc for AMD64. Is the live session a problem for U1 and the Music Store ?

Occurs on the builds for April 14 and April 15, at least. 

TIA for any help and/or suggestions.

dp

---

### Post by tea for one on 2010-04-15
Good evening

I purchased two songs and they have appeared in my Ryhthmbox list but I am unable to see them in my Ubuntu One account.

I was hoping to download them to add to my Sansa portable player?

Anyway, I realise that the software is still in Beta so I hope that they will arrive in my Ubuntu One Account soon?

Fingers crossed..........

Best wishes

---

### Post by ElSlunko on 2010-04-15
I don't think they appear in the ubuntu one folder. You can find them in ~/.ubuntuone/Purchased from Ubuntu One/

I made a link in my ubuntu one folder so it would be easier to get to. You can also drag them out of that folder & put them anywhere you'd like (Of course they won't sync if you don't have them in synced folders).



Wait...that brings up a question. If I drag the files out and put them in my ~/Music folder will they redownload into ~/.ubuntuone ?

---

### Post by tea for one on 2010-04-15
Good evening again

I should have read the guidelines for Ubuntu One because I did not realise that there is a hidden folder in my Home directory (~/.ubuntuone).

Anyway, my purchases are successfully stored in my hidden folder but I have not been able to find them in my Ubuntu One cloud storage area.

I'll get Inspector Clouseau on the case tomorrow.

---

### Post by tea for one on 2010-04-15
> **ElSlunko said:**
> I don't think they appear in the ubuntu one folder. You can find them in ~/.ubuntuone/Purchased from Ubuntu One/

I made a link in my ubuntu one folder so it would be easier to get to. You can also drag them out of that folder & put them anywhere you'd like (Of course they won't sync if you don't have them in synced folders).



Wait...that brings up a question. If I drag the files out and put them in my ~/Music folder will they redownload into ~/.ubuntuone ?

I'm a bit baffled because, if the purchases are not stored in the cloud, where do you download from? I understood that the purchaser is permitted to download three times. The first download is apparently from 7Digital to the purchaser's cloud storage area?

Or have I completely misunderstood the procedure?

---

### Post by solitaire on 2010-04-15
> **tea for one said:**
> I'm a bit baffled because, if the purchases are not stored in the cloud, where do you download from? I understood that the purchaser is permitted to download three times. The first download is apparently from 7Digital to the purchaser's cloud storage area?

Or have I completely misunderstood the procedure?

Nope you got it!
It's stored in something like a hidden folder within your cloud storage, then it's synced to all your other machines linked to your UbuntuOne account.

Digital7's "3 Download limit" its only from Digital's servers so you don't need to worry about that limit.

---

### Post by farmercyst on 2010-04-15
i thought i was having similar problems with the download from the music store but then i realized that the songs that i purchased were actually transfered to my ubuntu one account pretty quickly. the problem that i see is that even after almost 30 min, rhythmbox is still showing that they are transferring to my ubuntu one storage. i know that they are in my storage because i can download and play the files.

---

### Post by tea for one on 2010-04-16
> **farmercyst said:**
> i thought i was having similar problems with the download from the music store but then i realized that the songs that i purchased were actually transfered to my ubuntu one account pretty quickly. the problem that I see is that even after almost 30 min, rhythmbox is still showing that they are transferring to my ubuntu one storage. i know that they are in my storage because i can download and play the files.

Good morning

Thanks for the screenshot, I checked my Ubuntu One Cloud area this morning and I have 32.9MB used but the folder "Purchased from Ubuntu One" is empty.

The two songs are definitely on my hard dive and I have also received a confirmation of the purchase via e mail. 

It's a mystery.............?

---

### Post by StudioDave on 2010-04-16
> **StudioDave said:**
> Not yet, and not for lack of trying.

I guess I just had to wait long enough for the service to get livelier. Yesterday I successfully purchased a couple of songs from the U1 Music Store. I had the same experience as most of the folks here, i.e. Rhythmbox indicated that the songs were still transferring when they had already been downloaded (locally and to my U1 storage).

A good thing too. I was writing an article about the service, it didn't have a happy ending until yesterday. It's all good now. :)

Best,

dp

---

### Post by sixthwheel on 2010-04-17
Still having the same problem.
7 songs did not download...I checked everywhere and there are nowhere to be found.:(

---

