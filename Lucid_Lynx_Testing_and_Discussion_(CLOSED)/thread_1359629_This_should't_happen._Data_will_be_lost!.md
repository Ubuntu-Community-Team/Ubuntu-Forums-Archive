---
title: "This should't happen. Data will be lost!"
date: 2009-12-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by orlox on 2009-12-19
I just did a kernel update (2.6.32-9), and on reboot, I got a very peculiar message, just after grub
```

SEGMENTATION FAULT

```
That's it, no boot messages or anything, just that. Sooo, I restarted my computer, and it started the boot process this time, only that, in the end, it popped out a lot of messages regarding ext4 and the file system, none of them very pretty, and it ended in this beauty:
```

This should't happen. Data will be lost!

```
I don't know you, but I don't like error messages with exclamation signs...

So, just when I was thinking that I should start hanging myself, that I should really take more seriously the "use only for testing purposes!!!" messages, or at least take regular backups, I decide to test again wth an older kernel and see what happens.

Just as before, I got many error messages, and I was dropped to a root terminal being asked to run fsck manually. Well then:
```

fsck /dev/sda1

```
After answering "yes" to A LOT of "should I fix this?" questions, things ended with a REBOOT LINUX message.

So, I reboot, everything opens up fine, I put a blank dvd and I backup my data...Hope this serves as a warning for others!

---

### Post by ranch hand on 2009-12-19
Welcome to testing.

Let the breakage begin.

Have FUN.

---

### Post by orlox on 2009-12-19
> **ranch hand said:**
> Welcome to testing.

Let the breakage begin.

Have FUN.

Exactly :popcorn:

I just hate those non development releases that work like a charm. When I use them, I actually feel my computer is more like a tool than a toy. Since I got into alpha releases for intrepid ibex, I've spent very little time in stable releases...

---

### Post by ranch hand on 2009-12-19
I am actually using Lounge Lizard (10.04) as my production OS in the daytime when I can keep an eye on it.

Now, I do have 4 installs of the bugger on here (external enclosure with two 320Gb SATA drives) and I update the other three and try them before doing anything to the one I am on now.

I should be on the Jaunty I use at night but I have a HUGE work unit in boinc (see synaptic for details on boinc) and I am going a few hours long on here today.  The version in the repo is nice and stable.  I am on an Alpha OS running a boinc alpha(testing) version.

The whole purpose of testing is to get the bugs out now.  Everyone uses their box differently and there is a lot of different hardware.

You could look at what we do as being lab rats for the  devs.  Seeing as this is LL, I prefer Lab Lemmings.  There is an update and we all rush over the cliff.

This is what makes the stable releases stable.

Have FUN with the breakage.  There really isn't much good choice other than that any way.

I never did this before the last cycle (Kinky Kitten - 9.10).  I am a lot better at fooling around with my system now than I was when that started.  Educational.

---

### Post by ronacc on 2009-12-19
I just updated to the -9 kernel and rebooted with on problems and no warnings . even the nvidia driver came up right off .

---

### Post by ranch hand on 2009-12-20
> **ronacc said:**
> I just updated to the -9 kernel and rebooted with on problems and no warnings . even the nvidia driver came up right off .
I had a brief warning (too fast to read) about segmentation on one out of four installs.  It was the one without Plymouth.  It booted fine.

I upgraded this OS, boinc on it and all, and rebooted to ...-9 and it seems fine so far.  Been having some flicker in the GDM, it seems to be less, not gone but less, with the new kernel.

---

### Post by zika on 2009-12-20
[A thread about that.](http://ubuntuforums.org/showthread.php?t=1359040)

---

### Post by gnomeuser on 2009-12-20
Reading over the changelog there was an awful lot of ext4 changes,  I am not surprised that they throw warnings - it looked like major surgery. Expect a bumpy ride.

---

### Post by plun on 2009-12-20
Yup.... changelog including tons of EXT4 changes.

[https://lists.ubuntu.com/archives/lucid-changes/2009-December/001943.html](https://lists.ubuntu.com/archives/lucid-changes/2009-December/001943.html)


--

---

### Post by zika on 2009-12-20
> **gnomeuser said:**
> Reading over the changelog there was an awful lot of ext4 changes,  I am not surprised that they throw warnings - it looked like major surgery. Expect a bumpy ride.Not a very comforting thought ...

---

### Post by zika on 2009-12-20
> **plun said:**
> Yup.... changelog including tons of EXT4 changes.
[https://lists.ubuntu.com/archives/lucid-changes/2009-December/001943.html](https://lists.ubuntu.com/archives/lucid-changes/2009-December/001943.html)
--Ups, I thought You've been talking about 2.6.33 not about 2.6.32-9.13. I get segfault only in 2.6.33-999 and in 2.6.32-996.

---

### Post by plun on 2009-12-20
> **zika said:**
> Ups, I thought You've been talking about 2.6.33 not about 2.6.32. I get segfault only in 2.6.33.

Well... Lucid is still on 2.6.32 and will probably be so....

2.6.33 can be tested "for fun"....:)

---

### Post by zika on 2009-12-20
> **plun said:**
> Well... Lucid is still on 2.6.32 and will probably be so....

2.6.33 can be tested "for fun"....:)But why the same segfault in 2.6.32-996? I consider it is not dangerous since it is in "wait-for-root" ... Am I wrong?

---

### Post by plun on 2009-12-20
> **zika said:**
> But why the same segfault in 2.6.32-996? I consider it is not dangerous since it is in "wait-for-root" ... Am I wrong?

Ok, I don't know but everyone must be ready for a breakdown more or less....

This is for sure development

---

### Post by zika on 2009-12-20
> **plun said:**
> Ok, I don't know but everyone must be ready for a breakdown more or less....
This is for sure developmentI'm on this side of keyboard ever since DOS was the only thing, Desqview was my favorite at that time, then came W$3.* etc. Breakdown is nothing less that personal friend. Development release testing looks like a walk in the park compared to W$3.* experience ...
(I've even used fglrx drivers on my Ubuntu ...! That is a risk, if I have ever knew what a risk is...)

---

### Post by Gina on 2009-12-20
> **zika said:**
> I'm on this side of keyboard ever since DOS was the only thing, Desqview was my favorite at that time, then came W$3.* etc. Breakdown is nothing less that personal friend. Development release testing looks like a walk in the park compared to W$3.* experience ...
(I've even used fglrx drivers on my Ubuntu ...! That is a risk, if I have ever knew what a risk is...)Ah yes :)  I remember those times well - I loved Desqview too :lolflag:

---

### Post by ranch hand on 2009-12-20
I started wit DOS too.  Don't really mess it.  Or lotus123.

---

### Post by zika on 2009-12-20
> **ranch hand said:**
> I started wit DOS too.  Don't really mess it.  Or lotus123.Well, I **started** with Litton with drum disk and punched track (paper tape) and with IBM and punched cards after that ... No, I'm not in retirement, yet, still a decade and a half and + to go ...

---

### Post by Gina on 2009-12-20
Actually I started before the IBM PC was first produced.  I was employed in electronics and computing, choosing a career rather than marriage and family.

---

### Post by Gina on 2009-12-20
> **zika said:**
> Well, I **started** with Litton with drum disk and punched track (paper tape) and with IBM and punched cards after that ... No, I'm not in retirement, yet, still a decade and a half and + to go ...Did you ever have to edit punched paper tape by hand with a single row hand punch?  I did - a boot-strap loader for a DEC machine (as I recall - it was a long time ago now).  I think the first programming language I used was Mercury Autocode through a teleprinter and phone line to a computer at one of the big UK universities.  Then a bit later assembler and on to Fortran, Cobol, Pascal, oh I forget now.  But I've seen computers and programming advance over nearly half a century :lol:  Gosh, that makes me feel old :lol:  But it has been a great experience which I'm glad of :)

---

### Post by phillw on 2009-12-20
And we were taught "Flow Charting", a tool I use to this day for any layouts of how I'm going to write code (html / php / MySQL) - It just makes SENSE :P

As for playing with ext4 - I'm not sure if Ubuntu are still on their own variant of ext4 or have decided to join the rest of Debian (And, it seems, the world) with the other one.

Having done an ext3 --> ext4 conversion without data-loss I can assure that the output of a ```
sudo e2fsck -y /dev/sda3 
```  Is heart warming :popcorn:

Phill.

---

### Post by zika on 2009-12-20
> **Gina said:**
> Did you ever have to edit punched paper tape by hand with a single row hand punch?  I did - a boot-strap loader for a DEC machine (as I recall - it was a long time ago now).Yes, on Litton. You're not the only one old here ...

---

### Post by zika on 2009-12-20
> **phillw said:**
> And we were taught "Flow Charting", a tool I use to this day for any layouts of how I'm going to write code (html / php / MySQL) - It just makes SENSE :PI just like the faces of my students when I mention that they have to give me flow-chart of a program in their papers ... Old (good) habits die hard ... I do not write any code these days, almost, but it is a valuable mental tool. Even in probability and mathematical statistics the field I'm in these days (information theory, to be precise ...). Sorry for off-topic, I'll stop.

---

### Post by trulan on 2009-12-20
Hmmm... Data loss and a thread going way off-topic...

Reminds me of our first computer (a TRS-80) and the cassette tape recorder we used to save and load our programs (yes, a regular audio cassette recorder.  Hit 'record' on the tape deck, then type "csave" ;) )  Man, when a tape started wearing out, and you'd suddenly lose hours and hours of programming...that was data loss. :icon_frown:

I guess I missed out on this latest breakage because my Lucid is an upgrade from Jaunty and the file system is still ext3.

---

### Post by ronacc on 2009-12-20
> **Gina said:**
> Did you ever have to edit punched paper tape by hand with a single row hand punch?  I did - a boot-strap loader for a DEC machine (as I recall - it was a long time ago now).  I think the first programming language I used was Mercury Autocode through a teleprinter and phone line to a computer at one of the big UK universities.  Then a bit later assembler and on to Fortran, Cobol, Pascal, oh I forget now.  But I've seen computers and programming advance over nearly half a century :lol:  Gosh, that makes me feel old :lol:  But it has been a great experience which I'm glad of :)

gad you were lucky ! I had to use a sharp awl and a steady hand .And didn't it just burn your butt when they handed you back a stack of cards all jumbled and out of order ?

---

### Post by ranch hand on 2009-12-20
Well, all I can say is that I am glad not to be the only grumpy geezer here.

My wife worked with programing on punch cards.  She started a long time before I did but she is still a pup.  Heck she is a ways from 50.

---

### Post by phillw on 2009-12-20
>  I guess I missed out on this latest breakage because my Lucid is an upgrade from Jaunty and the file system is still ext3.

I just cheated - I did my own ext3 --> ext4 upgrade using this --> [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4)  Although I had to 'tweak' the e2fsck command at the end to be e2fsck -y  instead of that long list they give !!

Not had any ext4 issues since :-D

Oh, and my concurrent gripe ? --> [http://ext4.wiki.kernel.org/index.php/Ext4_Howto#For_people_who_are_running_Ubuntu](http://ext4.wiki.kernel.org/index.php/Ext4_Howto#For_people_who_are_running_Ubuntu)

That's why I used their methodology.

Phill.
P.S. - Yeah the Atari 640XL also had a tape drive, I had not long started work & saved up like heck to get a 5 1/4" disk drive for it !!

---

### Post by gacb on 2009-12-21
I have the same issue - reported as part of bug 499100 as I am also getting some mount messages on boot. 

Lucid starts after all the messages and seems to run normally, other than some flickering issues, which I suspect is something to do with Wine.

I had similar, but worse flickering issues on Intrepid due to Wine.

---

### Post by phillw on 2009-12-21
10.04 is at the alpha1 stage. The warnings are quite clear. Do NOT use LL as your production system. LL WILL bork / hose/ mess up your system.
Do NOT use it on a system that requires the 99.99999% uptime.

It is only by people reporting back what & how it went horribly wrong can the devs iron out the bugs.

To paraphrase, - "If it is not registered to Bugs-R-us on Launchpad - A bug will be rectified by chance"

>  Please note: Ubuntu Developers do not usually read the forums, to report a problem found in Lucid please report the bug in [Launchpad]("https://launchpad.net/ubuntu/+filebug").

^^^^ You know, the bit at the top !!!!!  ^^^^^

Report a bug - that's what we're all here for !!

Regards,

Phill.

---

### Post by zika on 2009-12-22
I've found that I get segfault at boot only if I use KMS. No matter what kernel. 2.6.32-9 or 2.6.33-999, whatever ...

---

