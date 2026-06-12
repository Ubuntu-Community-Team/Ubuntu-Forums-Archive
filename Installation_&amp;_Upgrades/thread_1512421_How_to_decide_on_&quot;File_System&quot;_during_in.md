---
title: "How to decide on &quot;File System&quot; during installation?"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2010-06-18
HI Guys!

On choosing the desired partition, where I wish to install Ubuntu, screen asks  to choose the "File System" from the drop-down menu.

How to decide on which one to choose from?

What's the implication of choosing EXT4 over EXT3?

Any ideas?

**Point= Iam now fed up with 10.04 release):P since it is crippled with sporadic issues like --"Shaking Screen on Desktop load" & an abrupt "Screen Blackout".....!!

Now I wish to roll-back to 9.04 again, the ONLY release of Ubuntu that worked "Perfectly" for me without posing any nuisance!

Help me choose the "Right" file system.

---

### Post by John Bean on 2010-06-18
> **Saurabhdua said:**
> How to decide on which one to choose from?

Research the capabilities of the various filesystems then choose the one that best meets your intended use. Google is your friend.

If you have no specific needs or preferences then accept the default the installer offers you. It's the default for good reasons.

---

### Post by dino99 on 2010-06-18
install both :p , you will learn

---

### Post by lechien73 on 2010-06-18
Weird duplication of posts!!! See below :)

---

### Post by lechien73 on 2010-06-18
Ext4 has been the standard file system for *buntus since Karmic - it was an option in Jaunty.

This link gives some of the improvements of Ext4 over Ext3:

[http://kernelnewbies.org/Ext4](http://kernelnewbies.org/Ext4)

The release notes for Jaunty give some cautions about using Ext4, but these will probably be fixed as soon as you run update-manager:

[https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes](https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes)

See the sections starting with *"Lock-ups when deleting files from ext4 filesystems"*

---

### Post by Saurabhdua on 2010-06-18
Got the point!

I'll choose the very first one-EXT3 for 9.04.However,Iam surprised that none of you authenticated the issues Iam facing with 10.04?!

Are these prevalent with other users as well? Is there a workaround still?

---

### Post by John Bean on 2010-06-18
> **Saurabhdua said:**
> Got the point!

I'll choose the very first one-EXT3 for 9.04.However,Iam surprised that none of you authenticated the issues Iam facing with 10.04?!

Are these prevalent with other users as well? Is there a workaround still?

I used Jaunty without issue. I tried Karmic and it was a disaster; I stayed with Jaunty until Lucid arrived, tried it, liked it. No issues at all for me, I have no intention of reverting to Jaunty.

Edit: Incidentally I used ext3 with Jaunty and use ext4 with Lucid, both without incident. I played about with ext4 in Jaunty but it wasn't reliable. YMMV, don't rely on what others experience since system behaviour varies enormously with differing hardware.

---

### Post by darkod on 2010-06-18
> **Saurabhdua said:**
> However,Iam surprised that none of you authenticated the issues Iam facing with 10.04?!

Are these prevalent with other users as well? Is there a workaround still?

You created a thread asking about the filesystem, not your issues with 10.04 with more information.

What video card do you have?
Did you try adding a driver?
Does live mode from the cd work OK?
Did you try to boot with the nomodeset parameter?

---

### Post by wojox on 2010-06-18
> **Saurabhdua said:**
> Got the point!

I'll choose the very first one-EXT3 for 9.04.However,Iam surprised that none of you authenticated the issues Iam facing with 10.04?!

Are these prevalent with other users as well? Is there a workaround still?

What are your system specs? 

When exactly does the screen blackout?

---

### Post by Saurabhdua on 2010-06-18
Hi Darkod & Wojox!

I did try my level best to get any HINT of where the issue could be!None of you Guys arrived then....Check out my earlier post::

[http://ubuntuforums.org/showthread.php?t=1502338](http://ubuntuforums.org/showthread.php?t=1502338)

As I have said, issues are very much "Sporadic".However, "Shaky screen or shaky mouse" are a bit frequent."Screen Blackout" is observed(whenever) at around 30-45 minutes of usage!

Live Mode was OK to an extent that I gave my "Final Go" to use 10.04.Didn't try that for say 30-45 minutes.

---

### Post by darkod on 2010-06-18
> **Saurabhdua said:**
> Hi Darkod & Wojox!

I did try my level best to get any HINT of where the issue could be!None of you Guys arrived then....Check out my earlier post::

[http://ubuntuforums.org/showthread.php?t=1502338](http://ubuntuforums.org/showthread.php?t=1502338)

As I have said, issues are very much "Sporadic".However, "Shaky screen or shaky mouse" are a bit frequent."Screen Blackout" is observed(whenever) at around 30-45 minutes of usage!

Live Mode was OK to an extent that I gave my "Final Go" to use 10.04.Didn't try that for say 30-45 minutes.

Start your computer and when the grub boot menu shows, highlight the ubuntu entry but don't hit Enter, hit 'e' instead. That will show you the boot lines.

Using the arrows keys and End go to the end of the line starting with linux. Delete quiet splash and add i915.modeset=1
Press Ctrl+X to boot.

See if it boots fine and whether it's working fine or the same issues appear.

If that didn't work, try the same again but this time add i915.modeset=0 and test how it will work.

Let us know how it went.

PS. The above parameters seem to work for Intel i8xxxx graphics that you have. If anyone has more experience with Intel graphics, jump in. :) I run ATI.

---

### Post by Saurabhdua on 2010-06-19
Hi Darkod!

Thanks for this effort.Initial response::'Screen Resolution' reverted to 1440X900(16:10).Things seem pretty tiny, hence changed that immediately to 1024X768.

Whether issues repeat or else..!?..I'll keep you updated for sure!

Whole-hearted thanks yet again!

---

### Post by Saurabhdua on 2010-06-19
Hello again!

Here goes the UPDATE 1::"Shaky Mouse Cursor" is still very much prevalent but continue to hover around in an irregular fashion.

Affect::diffraction.Iam not able to click any web link accurately with a single attempt.Finding difficulty in placing the cursor at the right place.

UPDATE 2:inadvertently, I have just now pressed ESC & the shaking has stopped!
Pretty stable now...lets see where this 'Hollywood Flick' take us to?

---

### Post by darkod on 2010-06-19
> **Saurabhdua said:**
> Hello again!

Here goes the UPDATE 1::"Shaky Mouse Cursor" is still very much prevalent but continue to hover around in an irregular fashion.

Affect::diffraction.Iam not able to click any web link accurately with a single attempt.Finding difficulty in placing the cursor at the right place.

Did you try with both different parameter values, =1 and =0?

---

### Post by Saurabhdua on 2010-06-19
Good to see you quickly!

Immediately after posting, Screen went black again, gave it a forced manual shutdown & again had a peek to line starting with linux. "Quiet Splash" is still there. I thought that line must have been saved with =1 entry but its not.

Changed it to =0,Ctrl X, Result:Shaky Desktop on load.

Repeated the whole thing with again =1 entry, this time CPU made a short sound before restart & here Iam back again!

Yes Sir, What's next?

---

### Post by darkod on 2010-06-19
When you edit the line like that during boot, what ever you add or delete is not saved, it's only temporary for that boot. When you restart it's lost.

The point is to see what works for you, and only after that you will make the change permanent.

So, =0 gives you the shaky desktop again. Are you happy with how =1 works or not?

---

### Post by darkod on 2010-06-19
I know you said it didn't work good with =0 but I read on google that a combination of two parameters might also help with Intel graphics. Try also adding at the end of the linux line:

i915.modeset=0 nomodeset

Just type it like that together separated by space. See if booting like that is working fine for you.

---

### Post by Saurabhdua on 2010-06-20
Hello Darkod!

Appreciate your time & effort.
i915.modeset=0 nomodeset gives me a SURE SHOT >>"Shaky Desktop".Have tried it twice on back-to-back occasions!

=1 parameter eventually gave a 'Blackout Screen' as reported in my previous post.

Have you come across same issues being reported by other users as well?OR Iam  the first & only one to crib about these?

---

### Post by Saurabhdua on 2010-06-22
Left 'aborted'....again!?

---

### Post by darkod on 2010-06-22
What can I say, don't buy Intel. :)

Stick with AMD and ATI (now also AMD). I don't have any more ideas if nothing worked to your satisfaction. The problem seems to be the graphics chip, you know that, try searching around for solution too.

---

### Post by darkod on 2010-06-22
This is an old thread but the last couple of posts might be interesting:
[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-install-trouble-with-intel-82845g-graphics-card-557840/](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-install-trouble-with-intel-82845g-graphics-card-557840/)

---

### Post by darkod on 2010-06-22
One possible solution for Intel 82845G here:
[http://ubuntuforums.org/showthread.php?t=324379&highlight=installing+intel+extreme+graphics+on+linux](http://ubuntuforums.org/showthread.php?t=324379&highlight=installing+intel+extreme+graphics+on+linux)

---

### Post by Saurabhdua on 2010-06-23
Thanks Darkod for this 'Last Minute' try but I have just checked your posts while making a transition back to 9.04!

Afterall, why to create a FUSS when previous versions work fine for you!

Big Hug & many thanks.

**Point=Do you think that 'Auto Adjustment' feature of Dell Monitors could be causing this issue OR problem is confined to graphics chip only?

---

### Post by darkod on 2010-06-23
Because 9.04 is supported only for another 4 months?

---

### Post by nss0000 on 2010-06-23
> **Saurabhdua said:**
> HI Guys!

On choosing the desired partition, where I wish to install Ubuntu, screen asks  to choose the "File System" from the drop-down menu.

How to decide on which one to choose from?

What's the implication of choosing EXT4 over EXT3?

Any ideas?

**Point= Iam now fed up with 10.04 release):P since it is crippled with sporadic issues like --"Shaking Screen on Desktop load" & an abrupt "Screen Blackout".....!!

Now I wish to roll-back to 9.04 again, the ONLY release of Ubuntu that worked "Perfectly" for me without posing any nuisance!

Help me choose the "Right" file system.

Yes:

LL_10.04 is generally seen to be a "defective" release. All sorts of peripheral functionality is dodgy --- from SOUNDCARDS to PRINTERS and glue-stuff like LOGOUTS !! Stuff that you figure was "solved" 20-years ago. 

Whether the spectrum of issues reflects a "genetic" corruption in the distro, or just a severe case of "over-reaching" with too much new code and too little bug-spray I believe we will not know for months! 

From following one such issue that impacts me --- the CUPs-bug(CUPs randomly fails on-boot)  --- I gather many problems reside non.trivially in deep kernel function.

---

### Post by Saurabhdua on 2010-06-23
Never mind Darkod!

Ubuntu for me is just an another way to relish 'Internet Experience'(only) a bit differently!

Foremost OS continue to remain Windows, though I'll try an another Linux flavor going too popular these days---FreeBSD.

Alas, they do not ship Free CDs!

**Point=Apropos of your comment with 9.04 will be supported for another 4 months, perhaps, that's the reason  why "Update Manager" of 9.04 takes ages to display list of updates(if any).Checking updates have turned into a nightmarish experience, literally!

---

