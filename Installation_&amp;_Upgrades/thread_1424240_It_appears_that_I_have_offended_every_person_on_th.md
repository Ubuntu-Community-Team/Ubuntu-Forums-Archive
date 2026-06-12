---
title: "It appears that I have offended every person on this forum."
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by wizarddrummer on 2010-03-07
I don't know what I did to offend everyone; but whatever it was that I did I'm sorry.

I look at other threads where 10's 100's even 1000's of people view them and in most cases at least one or more people respond / reply.

I put this thread up about 10 hours ago. Almost 50 people viewed it.
[http://ubuntuforums.org/showthread.php?t=1423840](http://ubuntuforums.org/showthread.php?t=1423840)

I asked a few questions.

I was way over tired and frustrated and probably rambled too much.

I have this funky computer with a pt800ce-a mother board.

I have a 500GB SATA hard drive with lots of files on it.

I have this wonderful Ubuntu installation that sees the "Unallocated" disk.

All I want to do is learn how to wave the magic wand so Ubuntu will mount the disk.

That's it.

Not one reply. 

So please, if you care to, tell me why so many of you were offended. 

What am I doing wrong?

Thanks.

---

### Post by sgosnell on 2010-03-07
I didn't see it.  There are so many posts on the forum, there isn't enough time in the day to read all of them, even if I read it almost full-time, and I don't have time for that.  I go by the thread subject, and if it just says Help!, I ignore it, because the poster needs to take the time to make it somewhat descriptive.  I've opened too many of those non-descriptive help posts to find something I had no interest in, nor knowledge of, so I don't bother now.  Threads still slip by that I might be interested in, but I just miss.  I also don't bother to post to threads where I can't help the poster.  Everyone here is a volunteer, unpaid, and most of us try to offer whatever help we can, but I can only get here now and then, and the forum only shows the last 250 posts, which may only cover a few hours, so I never see all the posts no matter what.  I'll take a look at your original post, and if I can help, I will, but if I don't have the knowledge, I'll pass, because there is no use in posting just to waste everyone's time.

---

### Post by howefield on 2010-03-07
I doubt you offended anyone :)

I think I read your last post before you reformatted it.

It was a horrible read, all acronyms, extra information and all one paragraph with sentences seeming to run into one another. It was a form of torture trying to read it.

I gave up and didn't finish reading it, maybe others did the the same.

I'm glad you reformatted.

---

### Post by lisati on 2010-03-07
Don't panic! I don't think you've done anything wrong.

As I type it has only been 10 hours or so since you started your other thread. Sometimes it can take days before someone who might be able to help sees a question. There is also a group of us who every now and again go looking for questions which haven't had a reply and help out where they can.

Good luck!

---

### Post by 2hot6ft2 on 2010-03-07
> **howefield said:**
> I doubt you offended anyone :)

I think I read your last post before you reformatted it.

It was a horrible read, all acronyms, extra information and all one paragraph with sentences seeming to run into one another. It was a form of torture trying to read it.

I gave up and didn't finish reading it, maybe others did the the same.

I'm glad you reformatted.
I agree and I did finish reading it but when I did I was left wondering if there was actually one or more questions in there that the OP wanted answers to. Besides the title is less than informative and the devil icon stands for "Thumbs Down" led me to believe it was just ranting.

Plus I don't know about everyone else but I tend to spend more time answering posters that show as being online, I see that this one is offline again so why should I spend my time talking to someone that isn't even there.

So is there an actual question?

---

### Post by Mark Phelps on 2010-03-07
Just for future reference, the timeframe in which to "expect" a response varies enormously by the question and who is here to answer it.

10 hours is NOT a long time to wait, on the contrary, 24 hours is considered the polite MINIMUM before bumping a post.

We're all volunteers here, and many (if not all) of us have full-time jobs relegating this work to our "free" hours.

I didn't see your original post, but if you come here whining about lack of response after only 10 hours, you're creating a bad initial impression of impatience.  If you don't get a response in a day or two, it could be because you worded your post so poorly that no-one understood your question -- or maybe, you hit upon a problem so unique that no-one has an immediate solution.

As to mounting a drive, there is no need for a "magic wand".

So, is this an internal drive that is permanently attached to the PC? Or is this an external drive that you connect via USB?

---

### Post by oldfred on 2010-03-07
this thread also had a poster with a Via chip and issues mounting his SATA. It took 3 days and I did not help him much as I had not seen a similar issue.

[http://ubuntuforums.org/showthread.php?t=1421942](http://ubuntuforums.org/showthread.php?t=1421942)

---

### Post by wizarddrummer on 2010-03-08
> **oldfred said:**
> this thread also had a poster with a Via chip and issues mounting his SATA. It took 3 days and I did not help him much as I had not seen a similar issue.

[http://ubuntuforums.org/showthread.php?t=1421942](http://ubuntuforums.org/showthread.php?t=1421942)

Thanks everyone for the replies.

I apologize if I sounded impatient. I completely understand that everyone is a volunteer and I admit, being tired; frustrated and less than enchanted with the computer that I have I didn't take the time to put up a very good post.

I wasn't expecting a solution as much as I was hoping for a "yeah, I have that problem too".

The reason I wrote my thread is because of what was contained in the thread in the quote did not help me.

There a "solution" near the end of the thread that has this info in it:
> **oldfred said:**
> You edit grub not grub.cfg and run sudo update-grub to fix it permanently.

gksudo gedit /etc/default/grub
from 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[LIST]
[*]***GRUB_CMDLINE_LINUX***
[LIST]
[*]If it exists, this line imports any entries to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. This is similar to the "altoptions" line in menu.lst
[/LIST]
 
[*]***GRUB_CMDLINE_LINUX_DEFAULT=***"quiet splash"
[LIST]
[*]This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". The entry "acpi=off", if required, would also be an option entered on this line.
[/LIST]
 
[/LIST]



I resaerched this problem before I posted anything. I found that some people with older systems that do not use Grub2 have put this command; pci=nomsi into their /boot/grub/menu.lst.

The problem here is I don't know what I am actually supposed to do in Grub2.

If this drive was blank  I would not be concerned I can't afford to lose the data on a mistake.

I included an attachment. 

My question is how to change the status from Unallocated Space to something that can be used. I don't want to press the Create button if there's a chance of destroying the data.

Again, thanks for the help.

Would it be more appropriate to start this whole mess over with a simpler question and better title?

---

### Post by bumanie on 2010-03-08
Sometimes it is best to deal with one issue at a time. It is hard to answer every question in a post that long - one person will not necessarily know every answer and thus long posts, with multiple questions become confusing for everyone, as there tends to be multiple 'part answers' to the many issues raised.

---

### Post by Rasa1111 on 2010-03-08
it appears that you could probably relax a little bit wizarddrummer dude. 
dang. .
g'luck

---

### Post by Paulzy on 2010-03-08
> **sgosnell said:**
> ..I go by the thread subject, and if it just says Help!, I ignore it, ..

I've been around since the days of ARCHIE, JUGHEAD, VERONICA, and BBSs. Well, this is what a community is about. Whenever anyone asks for help, you do not ignore it. Ever. You either offer help, or point them in the right direction.

But, I've seen that this is the way of the new Internet. "Google it", "Use the search function", or others are all too common responses now-a-days. But, ..sigh...this is what the Internet has become. 

You've offended noone, it's just the way the modern Internet is. BUt it seems the latter replies are leading you in the right direction. Good luck, my friend.
Paulzy

---

### Post by overdrank on 2010-03-08
Hi and since this is not a support request, The op does have a support thread [here]("http://ubuntuforums.org/showthread.php?t=1423840"). Thread closed. :)

---

