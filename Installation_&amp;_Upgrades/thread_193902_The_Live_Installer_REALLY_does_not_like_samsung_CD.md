---
title: "The Live Installer REALLY does not like samsung CD drives huh?"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by skelooth on 2006-06-10
I've been trying to get ubuntu on this machine for days :) It's getting to the point that I'd rather go buy another cd drive.

Originally I was getting the freeze at 'mounting root filesystem' problem that a lot of people get for different reasons (most of them seem to have usb issues, but there is no usb on this low end machine).

I could get past it with the irqpoll option, but it'd give me some nasty errors about the driver for the cd drive being incompatible

With the ide=nodma i can get all the way into the live desktop but it will hang or crash almost randomly, and it keeps freezing during install at 22% [Copying files]. ie, it chokes as soon as it touches the cd drive.

Any ideas?

---

### Post by goodmaj on 2006-06-10
Try the Install CD instead of the Live CD.  It is a more robust installer.

---

### Post by skelooth on 2006-06-10
there is a live cd, and an alternative install cd... so?

Regardless I'm downloading the alternative text based installer now.... so hopefully.

---

### Post by skelooth on 2006-06-10
the text installer gets closer, but still no go.... UGH

I can't get it to start / boot unless i disable dma, then during the base install random .debs will be corrupt, and they are different every time.

---

### Post by skelooth on 2006-06-10
*continues crunching on 2lb bag of carrots*

If I sit around and run it over and over and over eventually things complete with a 'clean' install..... but it's taking forever. Literally a half hour to retrieve 200 files off the cd.... :(

---

### Post by tmahmood on 2006-06-11
This might help a little. Create a swap partition (total RAM X 2 would be good) and then boot using the Live CD. You should get a huge performance boost. At least it helped me a lot :)

---

### Post by skelooth on 2006-06-11
FINALLY... i was so frustrated this morning that while i had my morning coffee I yanked out the samsung drive and put in an old dusty generic cd drive i had laying around in my room.

Installer and computer now work fine...... ubuntu and samsung are NOT friends, I've been seeing other topics on the boards that pretty much say anything samsung is probably not going to work....

---

