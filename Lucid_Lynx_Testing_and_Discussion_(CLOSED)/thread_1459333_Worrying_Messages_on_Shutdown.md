---
title: "Worrying Messages on Shutdown"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Olmy on 2010-04-21
Everything seems to be working OK but every time I shutdown I get a load of messages that appear for a second or so before final power down or the exit splash screen.

The number varies and they appear for far too short a time to actually read.

Is this normal?
Should I be worried?
Can I find out what they actually say?

---

### Post by kansasnoob on 2010-04-21
I get the same thing, more so on one machine than my other.

I think it's still due to a slightly buggy plymouth, but I'm not sure.

---

### Post by Eddie Wilson on 2010-04-21
I don't get text messages at shutdown, it just doesn't shut down. It always hangs up. This is on beta 2.

---

### Post by scradock on 2010-04-21
I believe what we're seeing is the "tail" of the console messages that were emitted during boot but hidden by the plymouth splash screen, plus the actual logout messages. 

It would be nice if plymouth stayed up long enough to hide them all, but it's no big deal, is it?

The alternative would be to have the console messages sent to the bit-bucket to begin with (> /dev/null ), but then we wouldn't be able to see them by removing "splash" from the grub2 boot line......

---

### Post by Olmy on 2010-04-22
> **scradock said:**
> ...but it's no big deal, is it?
In a beta, no.

In a final release it would smack of amateurishness.

Either I, as a user, need to (or might need to) see this or not. If I do, it should be made readable and if not, I shouldn't see it.

---

### Post by ndefontenay on 2010-04-22
Yeah. 6 days until the release and I still got the black screen with blinking cursor at startup along with some worrying line as well. I do have a splash screen for a short time.

At shutdown I get a splash screen then about 4-5 worrying lines before it shuts down.

I really hope it will be fixed by next thursday!

---

### Post by philinux on 2010-04-22
I'll take the odd message at shutdown as it's so quick. Shutdown here takes no more than 4 seconds. 

Other operating systems seem to take ages but give no feedback whatsoever. ;)

---

### Post by Olmy on 2010-04-22
> **philinux said:**
> I'll take the odd message at shutdown as it's so quick. Shutdown here takes no more than 4 seconds. 

Other operating systems seem to take ages but give no feedback whatsoever. ;)

I do take the point, lucid is very fast to boot and shutdown (unlike 9.10 which was a disaster for me due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/474495")) but it is also true that this is **worse **than giving no feedback whatsoever.

It's giving a vague hint that something might be wrong.

Sorry, I know this is just a bit of a rant - I work on embedded and sometimes safety critical software and the general lack of professionalism and flakiness of **all** desktop systems frustrates me.....

---

### Post by ndefontenay on 2010-04-22
I agree. This is like a store screen. It has to glitter.
This looks unprofessional and sloppy even if it's deadly efficient.

---

### Post by philinux on 2010-04-22
I'm more bothered about the startup. 15 seconds with a black screen and a blinking cursor top left.

I really hope this gets fixed soon.

---

### Post by d3v1150m471c on 2010-04-22
it's probably your system telling you that it's closing things down

---

### Post by zika on 2010-04-22
I do not worry about messages at shutdown. I do not have a shutdown ... :) Sorry, I do have, power-switch... My mistake... :)

---

