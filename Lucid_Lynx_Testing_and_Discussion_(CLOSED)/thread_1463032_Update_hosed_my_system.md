---
title: "Update hosed my system"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mykrob on 2010-04-26
Ran some updates just a little, I can no longer boot to desktop or recovery mode on ANY kernel.

Anything short of a reinstall that I can do?

Thanks,
-myk

---

### Post by mykrob on 2010-04-26
The last thing showing in recovery mode is

Begin:  Running /scripts/init-bottom ....
Done



Then the cursor just sits there.. flashing, mocking me...

---

### Post by kansasnoob on 2010-04-26
What do you mean by, "Ran some updates just a little"?

Were the updates interrupted?

---

### Post by StuartN on 2010-04-26
I ran updates today and I am left with a dysfunctional system.

After selecting the operating system in Grub2, the boot process lands me in the ash command line of initramfs.

Before a re-install from the release candidate CD, is there anything useful that I can report?

---

### Post by conradin on 2010-04-26
have a look here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1230498](http://ohioloco.ubuntuforums.org/showthread.php?t=1230498)
can you mount your hard drive from the prompt?

---

### Post by kansasnoob on 2010-04-26
OK, I had to research this quickly. To quote Colin Watson, "Argh. Thanks, trying to get a late fix in now."

An earlier update today broke it but a fix has been released:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/569317](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/569317)

IMHO if you can't boot you need to mount & chroot your Lucid and run "apt-get update && apt-get dist-upgrade". My method of performing a chroot here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

**[COLOR="Red"]Note: if you don't understand it don't try until you ask for more help![/COLOR]**

---

### Post by kansasnoob on 2010-04-26
> **conradin said:**
> have a look here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1230498](http://ohioloco.ubuntuforums.org/showthread.php?t=1230498)
can you mount your hard drive from the prompt?

That's not it! A buggy "initramfs-tools" was released earlier today!

A fix has been released:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/569317](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/569317)

---

### Post by kansasnoob on 2010-04-26
Quickie recap of what's up! An update was released earlier today:

> initramfs-tools (0.92bubuntu76) to 0.92bubuntu77
initramfs-tools-bin (0.92bubuntu76) to 0.92bubuntu77

It broke things!

There is a new update available:

> 0.92bubuntu77
0.92bubuntu78

That should fix things. If you can't boot (even into recovery mode) you'll have to mount and chroot the broken Lucid either from another OS on the computer or from a Live CD and then update to the latest packages.

My way of doing so:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

But **you must mount the proper partition** and check to be sure you've mounted the proper partition!

---

### Post by StuartN on 2010-04-26
> **kansasnoob said:**
> IMHO if you can't boot you need to mount & chroot your Lucid and run "apt-get update && apt-get dist-upgrade".

I have no interest in recovery because it is a new install, and re-installing would be just as quick. But before I do so, is there any debugging data anyone would like?

---

### Post by kansasnoob on 2010-04-26
Well, this is really bad! The newest update got me booted but no desktop settings were "saved", nor even my custom fstab settings!

This is a major screw up 3 days prior to release :(

I need to spend some time on this. It's a total mess!!!!!!!!!!!!!!!!!!!!!

---

### Post by mykrob on 2010-04-26
no luck on my end, tried the chroot process ,but no success. Not sure if it mattered, but all i had on me is a Karmic cd.

---

### Post by kansasnoob on 2010-04-26
> **mykrob said:**
> no luck on my end, tried the chroot process ,but no success. Not sure if it mattered, but all i had on me is a Karmic cd.

It shouldn't matter what CD you use. Do you want to try again? If so please use the Live CD (or another adjacent OS) to post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2010-04-26
More follow up! You can read the details here:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/569317](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/569317)

Quite simply, "this should only effect a small percentage of testers that were unfortunate enough to "grab" the bad "initramfs" packages. And it can be corrected through a chroot although it requires more than one reboot."

oops :redface:

---

### Post by mykrob on 2010-04-26
> **kansasnoob said:**
> What do you mean by, "Ran some updates just a little"?

Were the updates interrupted?

didnt realize the typo, sorry. That was supposed to say "just a little while ago", guess I accidentally moved away from the text box.

Still having trouble. I am booting from a Lucid live cd again for the second time. What i did the first time was mount all the locations as specified, then I ran updates and ran dist-upgrade, which updated 150 items. I'm guessing I did something wrong.

Little more hand holding needed, I'm afraid. 

ANy help you can give is appreciated. I have a separate home partition, so its no big deal to re-install, but as you stated, this should be able to be fixed. 

Thanks,
-myk

---

### Post by mykrob on 2010-04-26
I have everything mounted, and when I try to run updates, i get this:

[http://pastebin.com/NJPe6PSu](http://pastebin.com/NJPe6PSu)

---

### Post by mykrob on 2010-04-26
fsck it, I need to use my laptop...
Reinstalled and mounted previous /home partition.

Back to normal.

Didnt learn anything, but at least I can use my laptop now.

---

### Post by moviemaniac on 2010-04-26
Boy am I glad I read this. I picked up the bad update earlier today and hadn't rebooted since then. So I updated again and picked up the fixed initramfs-tools.

---

### Post by kansasnoob on 2010-04-26
They pushed out an iso-test late this afternoon so I'll be unavailable.

Sorry, but priorities .............. :biggrin:

Edit: After a very quick look I'd have tried "apt-get clean", then update and upgrade.

---

### Post by kansasnoob on 2010-04-26
I'm still getting crap for stability! Sometimes I can boot OK, others I can't boot at all, still others I get a horrifically long chkdsk :(

This is a huge ouch!

---

### Post by kansasnoob on 2010-04-26
Even system temps are nutso! And if it's nutso it's just after boot!

I'm tired, time to boot into something stable like Karmic (on this box) and relax.

---

### Post by kansasnoob on 2010-04-26
Well, at this point I can't boot either of the OS's I speak of in that bug report :(

But I'm wiped out! I really don't care other than the fact that this should not have happened this close to final!!!!!!!!!!!

Did the devs party all weekend? Was this hungover Monday? I've never seen this before.

---

### Post by Usksider on 2010-04-27
I have this same problem :(

So okay there's a fix... thing is, how can I apply it given I can't get to Lynx?

---

