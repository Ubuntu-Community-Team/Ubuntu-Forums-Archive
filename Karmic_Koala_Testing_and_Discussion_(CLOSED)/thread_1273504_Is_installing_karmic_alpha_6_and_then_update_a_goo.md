---
title: "Is installing karmic alpha 6 and then update a good idea ???"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Axx83 on 2009-09-23
Hi everyone, I have to install ubuntu on a new ssd hard disk, on my sis laptop. I was thinking, instead of installing jaunty, with old grub and ext3, why not install alpha 6 of karmic and then let her update each time until the final karmic is out ? This way she'll have grub 2 and ext4 from the start (otherwise I wouldn't know how to grub2 her).

Is it risky ? Is alpha 6 very unstable ? Will the update be flawless ? Is it a good idea or not considering she'll be very far away from me and she'll have to update all by herself?

Thanks for the help, you're great

---

### Post by snowpine on 2009-09-23
Unless she is an experienced Ubuntu user who is interested in testing an unstable operating system and helping to report bugs, it is a terrible idea.

Jaunty works fine for 99% of users, and you can install using ext4 in Jaunty if you use the Manual partitioning option. Jaunty will be fully supported through Oct. 2010. You can help her upgrade to Karmic if you see her at the holidays. :)

---

### Post by howefield on 2009-09-23
> **Axx83 said:**
> Is it risky ? Is alpha 6 very unstable ? Will the update be flawless ? Is it a good idea or not considering she'll be very far away from me and she'll have to update all by herself?

You have answered your own question, it is a crazy idea ;)

It might go flawlessly, but it may not. With Alpha/Beta software you have to assume that something will go wrong, and if it doesn't then that's a bonus.

The question you need to ask yourself is, can she fix if something goes wrong, how big a disaster would that be and is it worth the risk ?

---

### Post by earthpigg on 2009-09-23
as others have said, you can get ext4 in jaunty.

the other item you listed was grub2.

what advantages are there with grub2 that you think your user will benefit from? tried and true grub gets ubuntu booting just fine...

---

### Post by QIII on 2009-09-23
No.  I wouldn't install an Alpha on a "production" machine.

Last I checked (on the 17th) the iso for Alpha 6 was a bust.  They might have updated it, but I don't know.  There are horror stories all over launchpad about this.

I had to re-install Alpha 5 and and do a dist-upgrade (not upgrade) to get Alpha 6 working on both my 32 bit and 64 bit testing machines.

If you really want GRUB2 to work, there are some commands that need to be run in the terminal (install os-prober, run os-prober, run update-grub2) to get visibility of other OSs if you run a multi-boot system.

Not to mention all the issues that you would normally encounter with an Alpha release.

Again: No.  As advised above.

---

### Post by AlanR8 on 2009-09-23
Have run the Karmic Alphas since V4 and had no problems.

Until last week when I had a fully BORKED system. An update too far!

Could not reinstall and do a full update for two days.

That's the price you pay for being on the cutting bleeding edge.....

---

### Post by Axx83 on 2009-09-23
guys thanks 4 the replies!

I think I'll stick with jaunty for now, with ext4 and no grub2. The doubt is...when karmic comes out, a month passes (for security) and she upgrades will there be a problem with the fact that grub is not version 2 ? and what about the next version and so on ?

Is the performance for a intel gm945 graphic card acceptable now with jaunty ? I have a similar intel card and compiz is unusable, all the rest work very very very well, but I played with intel drivers and config files...what about clean fresh install and latest update of jaunty ?

Thanks again for the help

---

### Post by snowpine on 2009-09-23
I guarantee you will be able to upgrade Ubuntu 9.04 to 9.10. :)

---

