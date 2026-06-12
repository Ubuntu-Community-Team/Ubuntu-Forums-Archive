---
title: "Patching apps for the new notification system"
date: 2009-02-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by smbm on 2009-02-26
Hi

I use cGmail to poll my Gmail account every couple of mins for new emails.

Ever since I've updated to Jaunty it's been annoying me that it pops up a proper window instead of a notification (because it uses buttons in it's notification).

I've worked out how to alter the code to not add the buttons anymore.

I've no idea what to do now though.

I've found the project on Launchpad:

[https://launchpad.net/cgmail](https://launchpad.net/cgmail)

It seems pretty stagnant though.

Does anyone have any detailed instructions for uploading a patch?

Should I update the Ubuntu version as well as the upstream?

Cheers

---

### Post by taavikko on 2009-02-26
[https://wiki.ubuntu.com/PackagingGuide/PatchSystems](https://wiki.ubuntu.com/PackagingGuide/PatchSystems)

But maybe better to read the whole thing through...
[https://wiki.ubuntu.com/PackagingGuide/](https://wiki.ubuntu.com/PackagingGuide/)

---

### Post by mpt on 2009-02-26
Whether or not you’re willing to do the packaging, I suggest you first [report a bug for the cgmail package]("https://bugs.launchpad.net/ubuntu/+source/cgmail"), attach your patch, and tag the bug report as “notifications”. That way the Desktop Experience team will see your work and be able to help you out. Thanks!

---

### Post by smbm on 2009-02-26
> **mpt said:**
> Whether or not you’re willing to do the packaging, I suggest you first [report a bug for the cgmail package]("https://bugs.launchpad.net/ubuntu/+source/cgmail"), attach your patch, and tag the bug report as “notifications”. That way the Desktop Experience team will see your work and be able to help you out. Thanks!

Hmm, I filed a bug about excessive CPU wake ups a year or so ago and it's not been touched since.

I will give it a try though, I've never generated a patch before, do you know of any fool proof documentation?

Cheers

---

### Post by smbm on 2009-02-26
I've managed to publish my changes to a branch. Is that any help? I haven't done extensive testing on it though.

It's also quite a dirty hack, I've basically just switched off any buttons appearing on the notifications rather than testing to see if the notification server supports them and then switching them on/off.

Done: [https://bugs.launchpad.net/cgmail/+bug/335197](https://bugs.launchpad.net/cgmail/+bug/335197)

---

### Post by Mr. Picklesworth on 2009-02-26
I see you have the branch thing figured out. Now here's something REALLY cool you can do!

From either your bug report or the branch's [information page]("https://code.launchpad.net/~t.vetterlein/cgmail/no_dialog_buttons"), there is a button that says "Link a related branch." If you feel it's stable, it never hurts to propose that branch for merging and change its status, also from its information page.

---

### Post by smbm on 2009-03-26
I've finally managed to cobble together a package that works on my system.

It turned out the original dev had included a script to turn it into a package.

If anyone would like to test it you can get it from here.

[https://dl.getdropbox.com/u/726576/cgmail_0.5-0ubuntu0ppa41_all.deb](https://dl.getdropbox.com/u/726576/cgmail_0.5-0ubuntu0ppa41_all.deb)

I built it on a 64bit install but it's in Python so I'm hoping it should work on 32bit too. Can anyone clarify this for me?

---

### Post by Lorenz on 2009-03-26
I am using gmail notifier or notification - not sure now, I am at my work computer. I had a thread here, someone told me what to adjust, so now it works with the new notification system too. you might want to look into it, it was just a click away to make it work

---

### Post by smbm on 2009-03-26
I have a working notifier, but thanks for the info.

---

### Post by Kow on 2009-03-26
Yea the reason it is outdated in ubuntu is because it is a universe package which is taken from debian. Debian's latest version of cgmail is 0.4.1. So the best way to go about this would be to file a bug upstream with debian. Since we are long after debian import freeze you would likely have to wait for karmic when ubuntu would merge/resync cgmail with debian. Of course, no one is stopping you from using your created deb. I just don't see 0.5 making it into jaunty, however.

---

### Post by mempf on 2009-03-26
I'm using mail-notification and to get it compliant with the new notification system I went into gconf-editor and removed ""open", "mark-as-read", "mark-as-spam"" from the actions key under popups.

---

### Post by dholbach on 2009-03-27
> **smbm said:**
> I've managed to publish my changes to a branch. Is that any help? I haven't done extensive testing on it though.

It's also quite a dirty hack, I've basically just switched off any buttons appearing on the notifications rather than testing to see if the notification server supports them and then switching them on/off.

Awesome!

Check out [https://wiki.ubuntu.com/SponsorshipProcess](https://wiki.ubuntu.com/SponsorshipProcess) to see how to get it included in Ubuntu.

---

### Post by smbm on 2009-03-27
I've managed to get my PPA working:

[https://launchpad.net/~t.vetterlein/+archive/ppa](https://launchpad.net/~t.vetterlein/+archive/ppa)

It's packaged up in there just fine by the looks of things.

---

